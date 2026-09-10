---
tags: [physics, quantum-mechanics, thermodynamics, black-body-radiation]
aliases: [Planck's Law, Black Body Radiation]
---

# Black-Body Radiation

> [!abstract] Big picture
> Black-body radiation is the place where **classical physics broke** — not with a small error, but with a prediction of *infinite energy*. Fixing it required inventing quantum mechanics. This note builds the whole story: phenomenon → classical failure → Planck's fix → full derivation.

---

## 1. What is a Black Body?

Imagine a hollow box with a tiny hole in it:

```
┌─────────────────┐
│                 │
│    ↘   ↓   ↙    │
│      ↘ ↓ ↙      │
│        ●        │  ← tiny hole
│                 │
└─────────────────┘
```

Radiation entering the hole bounces around inside, gets absorbed/re-emitted by the walls over and over. It essentially never finds its way back out.

> [!note] Definition
> A **black body** is an ideal object that absorbs essentially *all* incident electromagnetic radiation, regardless of frequency or direction.

But here's the subtle part: a black body doesn't just absorb — heat it up, and it **emits** radiation too. And that emitted spectrum depends on almost nothing except one variable:

$$T \quad \text{(temperature)}$$

> [!warning] Common misconception
> "Black body" describes its **absorption** property, not its visual appearance. A black body heated to 5000 K emits plenty of visible light — it looks bright, not black.

---

## 2. The Experimental Picture

Heat a piece of iron and watch it change color:

- Low $T$ → infrared (invisible)
- Higher $T$ → dull red → orange → yellow → white

Plotting **intensity vs. frequency** at a fixed temperature gives a curve. As $T$ increases, two things happen:

1. Total emitted energy goes **up**
2. The peak of the curve **shifts toward higher frequency**

```
Intensity
   │               /\       higher T
   │             /    \
   │       /\   /
   │     /    \/
   │____/________________ Frequency
```

---

## 3. Wien's Displacement Law

Since $c = \lambda\nu$, higher frequency means shorter wavelength. So:

$$\boxed{\lambda_{\max} T = b}$$

where $b \approx 2.898 \times 10^{-3}\ \text{m·K}$.

**Examples:**

| $T$ | $\lambda_{\max}$ | Region |
|---|---|---|
| 3000 K | ≈ 966 nm | near-infrared |
| 5800 K (Sun) | ≈ 500 nm | visible |
| 6000 K | ≈ 483 nm | blue-green |

This is why hotter stars look blue-white and cooler stars look red.

> [!important] Careful
> This doesn't mean a hotter body *only* emits short wavelengths — it still emits a broad continuous spectrum. Only the **peak location** shifts.

> [!tip] Frequency-space peak ≠ wavelength-space peak
> $u_\nu\,d\nu = u_\lambda\,d\lambda$, and since $d\nu = -\frac{c}{\lambda^2}d\lambda$, changing variables changes the shape of the curve. So $\lambda_{\max} \neq \dfrac{c}{\nu_{\max}}$ — the two peaks genuinely sit at different physical points on the spectrum.

---

## 4. The Classical Prediction: Rayleigh–Jeans Law

19th-century physicists combined classical electromagnetism with statistical mechanics and got:

$$u(\nu, T) = \frac{8\pi\nu^2}{c^3}kT$$

where $u(\nu,T)$ is energy density per unit frequency.

## 5. The Ultraviolet Catastrophe

Since $u \propto \nu^2$, as $\nu \to \infty$:

$$u \to \infty$$

Integrating over all frequencies to get total energy:

$$U = \int_0^\infty \frac{8\pi\nu^2}{c^3}kT\, d\nu \;\longrightarrow\; \infty$$

> [!danger] The catastrophe
> Classical physics predicted that **any object at any non-zero temperature radiates infinite energy**. Obviously false. Nature was screaming that something fundamental was missing.

**Where exactly is the mistake?** Classical stat-mech says every electromagnetic mode gets average energy $\approx kT$. But the number of modes grows as $\nu^2$ — so at high frequency there are enormously many modes, each still getting $kT$. That product blows up.

---

## 6. Planck's Quantum Hypothesis (1900)

Planck proposed that an oscillator of frequency $\nu$ can't have *any* energy — only:

$$E_n = nh\nu, \qquad n = 0, 1, 2, 3, \dots$$

$$h = 6.626 \times 10^{-34}\ \text{J·s}$$

So allowed energies are $0, h\nu, 2h\nu, 3h\nu, \dots$ — **discrete packets**, with a gap $\Delta E = h\nu$ between them. This is the birth of quantum physics.

### Why this fixes the catastrophe

- **Low frequency** ($h\nu \ll kT$): the energy quantum is tiny compared to thermal energy → easily excited → behaves just like classical physics.
- **High frequency** ($h\nu \gg kT$): the oscillator needs a *huge* quantum just to get excited at all → thermal environment can't supply it often → mode stays essentially empty.

> [!quote] The one picture to keep in your head
> Think of each electromagnetic mode as a **bucket**. Classical physics says "pour $kT$ energy into every bucket" — infinitely many high-frequency buckets means infinite energy. Planck says a bucket can only accept energy in chunks of size $h\nu$. Low frequency → buckets fill easily. High frequency → buckets almost never get filled. That one idea turns infinite UV catastrophe into a finite, correct spectrum.

---

## 7. Wait — what actually *is* an "oscillator" here?

This confused a lot of people, so slow down on it.

An oscillator is anything that swings back and forth around equilibrium — a mass on a spring, a pendulum, a guitar string.

Inside a black-body cavity there are no literal balls-on-springs. Instead, the **electromagnetic field itself** forms standing waves — patterns like:

$$E(x,t) = E_0 \sin(kx)\cos(\omega t)$$

Each such standing-wave pattern is called a **mode**. Energy in a mode sloshes back and forth between electric and magnetic field, exactly like a spring sloshes energy between kinetic and potential — mathematically, that's a harmonic oscillator.

$$\text{one EM mode} \;\longleftrightarrow\; \text{one harmonic oscillator}$$

So "cavity radiation" = a huge collection of independent electromagnetic harmonic oscillators, one per allowed standing wave, and Planck's quantization rule applies to *each one individually*.

---

## 8. Deriving Planck's Law

The full derivation is just two independent questions multiplied together:

$$\text{energy density} = (\text{number of modes at frequency }\nu) \times (\text{average energy per mode})$$

### Part A — Counting modes (why frequency can't be arbitrary)

Take a cavity as a cube of side $L$. A standing wave must vanish at both walls: $E(0) = E(L) = 0$. Using $E(x) = E_0\sin(kx)$, this forces:

$$kL = n\pi, \qquad n = 1, 2, 3, \dots$$

$$\Rightarrow \lambda = \frac{2L}{n} \;\Rightarrow\; \nu_n = \frac{nc}{2L}$$

So only frequencies that are integer multiples of $\frac{c}{2L}$ actually "fit" as standing waves between the walls — e.g. if $L = 1\,\text{m}$, allowed frequencies are $\frac{c}{2}, c, \frac{3c}{2}, 2c,\dots$ A value like $\nu = 0.7c$ would require $n = 1.4$, which isn't an integer, so that wave simply cannot exist in the cavity.

**In 3D**, each direction gets its own integer:

$$k_x = \frac{n_x\pi}{L},\quad k_y = \frac{n_y\pi}{L},\quad k_z = \frac{n_z\pi}{L}, \qquad n_x,n_y,n_z = 1,2,3,\dots$$

Each allowed mode is a point in **$k$-space**, sitting on a 3D lattice. Frequency depends only on distance from the origin:

$$k = \sqrt{k_x^2+k_y^2+k_z^2}, \qquad \nu = \frac{ck}{2\pi}$$

So counting "modes between $\nu$ and $\nu + d\nu$" = counting lattice points in a thin spherical shell of radius $k$, thickness $dk$.

- Shell volume: $4\pi k^2\,dk$
- **Octant factor $\times\frac{1}{8}$**: since $n_x, n_y, n_z$ are all positive, allowed points live in only one of the 8 octants of $k$-space (this avoids counting the same standing wave twice via $\pm k$).
- **Polarization factor $\times 2$**: for any propagation direction $\vec k$, the electric field can point in 2 independent directions perpendicular to $\vec k$.
- Each lattice point occupies $k$-space volume $(\pi/L)^3$.

$$dN = \frac{\frac{1}{8}(4\pi k^2\,dk)\times 2}{(\pi/L)^3} = \frac{V}{\pi^2}k^2\,dk$$

Substituting $k = \frac{2\pi\nu}{c}$, $dk = \frac{2\pi}{c}d\nu$, and simplifying:

$$\boxed{\ g(\nu)\,d\nu = \frac{8\pi\nu^2}{c^3}\,d\nu\ }$$

This is the mode density — **how many electromagnetic "buckets" exist per unit volume near frequency $\nu$.**

### Part B — Average energy per mode (Planck statistics)

Each mode (oscillator) has allowed energies $E_n = nh\nu$. At thermal equilibrium, Boltzmann statistics give:

$$P_n \propto e^{-E_n/kT} = e^{-nh\nu/kT}$$

Let $q = e^{-h\nu/kT}$. The average energy is:

$$\langle E\rangle = \frac{\sum_{n=0}^\infty nh\nu\, q^n}{\sum_{n=0}^\infty q^n}$$

Using the geometric series results $\sum q^n = \frac{1}{1-q}$ and $\sum nq^n = \frac{q}{(1-q)^2}$:

$$\langle E\rangle = h\nu\cdot\frac{q}{1-q} = \frac{h\nu\, e^{-h\nu/kT}}{1-e^{-h\nu/kT}}$$

Multiply top and bottom by $e^{h\nu/kT}$:

$$\boxed{\ \langle E\rangle = \frac{h\nu}{e^{h\nu/kT}-1}\ }$$

### Part C — Combine

$$u(\nu,T)\,d\nu = g(\nu)\,d\nu \times \langle E\rangle$$

$$\boxed{\ u(\nu,T) = \frac{8\pi h\nu^3}{c^3}\cdot\frac{1}{e^{h\nu/kT}-1}\ }$$

**This is Planck's Radiation Law.**

> [!success] The whole derivation in one line
> $$u(\nu,T) = \underbrace{\frac{8\pi\nu^2}{c^3}}_{\text{how many modes exist}} \times \underbrace{\frac{h\nu}{e^{h\nu/kT}-1}}_{\text{energy per mode}}$$

---

## 9. Checking the Limits

### Low frequency ($h\nu \ll kT$) → recovers Rayleigh–Jeans

With $x = h\nu/kT \ll 1$: $e^x - 1 \approx x$, so

$$\langle E\rangle \approx \frac{h\nu}{h\nu/kT} = kT \quad\Rightarrow\quad u(\nu,T) \approx \frac{8\pi\nu^2}{c^3}kT$$

So classical physics wasn't *wrong* — it's the low-frequency approximation of the full quantum result.

### High frequency ($h\nu \gg kT$) → exponential suppression

$$e^{h\nu/kT} \gg 1 \quad\Rightarrow\quad u(\nu,T) \approx \frac{8\pi h\nu^3}{c^3}e^{-h\nu/kT}$$

The $\nu^2$ growth in mode-count is now crushed by the exponential decay — no more catastrophe.

$$\text{energy} = \underbrace{\text{mode-count growth } (\propto \nu^2)}_{\text{wants energy} \uparrow} \times \underbrace{\text{quantum suppression } (\propto e^{-h\nu/kT})}_{\text{wants energy}\downarrow}$$

The competition between these two is what produces the observed *peaked, finite* spectrum.

---

## 10. Wien's Law, Derived from Planck's Law

Wien's law isn't an independent rule — it falls straight out of Planck's law. Write it in wavelength form:

$$u_\lambda(\lambda,T) = \frac{8\pi hc}{\lambda^5}\cdot\frac{1}{e^{hc/\lambda kT}-1}$$

Setting $\frac{du_\lambda}{d\lambda} = 0$ and defining $x = \frac{hc}{\lambda kT}$, the maximum condition reduces to:

$$5(1-e^{-x}) = x \quad\Rightarrow\quad x \approx 4.965$$

$$\Rightarrow\quad \lambda_{\max}T = \frac{hc}{4.965\,k} = 2.898\times10^{-3}\ \text{m·K}$$

---

## 11. Stefan–Boltzmann Law

Integrating the full Planck spectrum over all frequencies gives total emitted power per unit area:

$$\boxed{j^\star = \sigma T^4}, \qquad \sigma = 5.67\times10^{-8}\ \text{W m}^{-2}\text{K}^{-4}$$

Doubling absolute temperature multiplies emitted power by $2^4 = 16$.

For a **real** (non-ideal) object with emissivity $\epsilon$ (where $0 \le \epsilon \le 1$):

$$P = \epsilon\sigma A T^4, \qquad P_{\text{net}} = \epsilon\sigma A\left(T^4 - T_{\text{surroundings}}^4\right)$$

---

## 12. Kirchhoff's Law

At thermal equilibrium, emissivity equals absorptivity at every wavelength:

$$\epsilon_\lambda = \alpha_\lambda$$

A good absorber at a given wavelength is an equally good emitter at that wavelength. Since a black body has $\alpha = 1$, it also has $\epsilon = 1$ — the maximum possible thermal emitter.

---

## 13. Summary — the whole story as one chain

1. Hot matter → EM standing-wave modes → radiation is emitted.
2. Experiment: $T\uparrow \Rightarrow$ total radiation $\uparrow$, and $\lambda_{\max}\downarrow$.
3. Classical physics assumes $\langle E\rangle = kT$ per mode, and $g(\nu)\propto \nu^2$ modes exist.
4. Result: $u(\nu)\propto \nu^2 \Rightarrow U \to \infty$ — the **ultraviolet catastrophe**.
5. Planck's fix: $E_n = nh\nu$ — energy is **quantized**.
6. High-frequency modes need large quanta ($h\nu \gg kT$) → rarely excited.
7. Result: $u(\nu,T) = \dfrac{8\pi h\nu^3}{c^3}\cdot\dfrac{1}{e^{h\nu/kT}-1}$
8. From this single formula: Wien's law ($\lambda_{\max}T = b$) and Stefan–Boltzmann ($P/A = \sigma T^4$) both emerge.

> [!quote] The core idea, one more time
> Classical physics: every mode gets roughly $kT$, and there are infinitely many high-frequency modes → infinite energy.
> Planck's fix: a mode's energy comes in chunks of $h\nu$. When $h\nu \gg kT$, thermal energy can't afford the chunk, so that mode stays essentially unexcited.
> That single idea — **discreteness of energy** — is the conceptual heart of quantum mechanics, and it was born from trying to explain something as mundane as a glowing piece of iron.

---

## Related notes
- [[Wien's Displacement Law]]
- [[Rayleigh-Jeans Law]]
- [[Quantum Harmonic Oscillator]]
- [[Stefan-Boltzmann Law]]
