# Eclipsing Binary Characterization Project

## TIC 158794976 Stellar Characterization

### Shubham Apte

## 1. Introduction
Eclipsing Binary (EB) systems are tremendously important for determining stellar parameters. These systems consist of two or more stars revolving around their Center Of Mass, which gives rise to periodic eclipses. These eclipses provide insights about the stellar parameters, such as mass, temperature, orbital period, luminosity, and distance from the Solar System. Among the Detached (DBS), Semi-Detached (SDBS), and Contact Binary Systems (CBS), DBS offers distinct primary and secondary eclipse patterns, enabling accurate stellar parameter predictions.

One such system is **KIC 7023917** (GSC 03129-01771, TYC 3129-1771-1, TIC 158794976, Gaia DR3 2102332172948222976). This object was studied by [Gajdoš et al., 2024] and its parameters were determined with minimal error using standard methods. This project aims to recreate those results using various approximations.

## 2. Data Acquisition
- **Light Curve Data**: TESS data was used to identify eclipse patterns. The **Lightkurve** package [2] was used to extract light curves (LCs) from TESS data.
- **Radial Velocity Data**: Radial velocity data was taken from Gajdoš et al. (2024), recorded using a 2-meter Perek telescope.
- **Distance and Magnitude Data**: The distance and magnitude data were taken from **Gaia DR3** for comparison.

## 3. Stellar Parameter Prediction

### 3.1 Orbital Period
Using the light curve from TESS Sector 14, primary and secondary eclipses were observed. Their depths and durations were used to predict the orbital period, which was found to be:
- **Complete Overlap Duration**: 1264 seconds
- **Partial Overlap Duration**: 7783 seconds

The inbuilt **Box Least Square (BLS)** function in Lightkurve was used to phase-fold the time series data and predict the most likely eclipse positions.

### 3.2 Semi-Major Axis of the System
The semi-major axis was calculated using:
\[
a = \frac{K_1 P (q + 1)}{2 \pi q \sin i}
\]
Where \(i\) is the inclination, \(q\) is the mass ratio. The calculated semi-major axis is **4.51 R⊙**, compared to **4.189 R⊙** in [1].

### 3.3 Semi-Amplitude of RV
The semi-amplitude of the RV curve was approximated as the mean of the maximum and minimum amplitude points, resulting in:
- **Semi-amplitude**: 24.015 km/s, compared to 22.28 km/s in [1].

### 3.4 Combined Mass
Using Kepler’s third law, the combined mass of the system was calculated as:
\[
m_1 + m_2 = \frac{4 \pi^2 a^3}{G P^2}
\]
Result: **2.077 M⊙**, compared to **2 M⊙** from [1].

### 3.5 Temperature Ratio
Using the Stefan-Boltzmann Law, the temperature ratio of the two stars was approximated from the depth of the eclipses. The ratio of temperatures was found to be:
\[
\left( \frac{T_A}{T_B} \right)^4 = \frac{\text{Primary Eclipse Depth}}{\text{Secondary Eclipse Depth}}
\]
Result: **1.036**, compared to **1.164** in [1].

### 3.6 Luminosity
Using the blackbody approximation, the total luminosity of the system was found to be:
\[
L = 4 \pi R_A^2 \sigma T_A^4 + 4 \pi R_B^2 \sigma T_B^4
\]
Result: **14.85 L⊙**, compared to **14.4 L⊙** from [1].

### 3.7 Absolute Magnitude
Using the calculated luminosities, the absolute magnitudes of the stars were determined by:
\[
m_2 - m_1 = -2.5 \log_{10} \left( \frac{L_1}{L_2} \right)
\]

### 3.8 Distance
The distance to the system was calculated using the distance modulus:
\[
m - M = 5 \log_{10} d - 5
\]
Result: **442.11 parsecs**, compared to **432.46 parsecs** from Gaia DR3.

## 4. Discussion and Conclusion
The values of stellar parameters derived using simplified approximations differ slightly from those found by Gajdoš et al. (2024). The maximum error observed was **11%** in temperature estimation due to the assumption of blackbody radiation. However, most of the derived parameters were within a reasonable margin of error, showing that simple approximations can still yield valuable insights into stellar systems.

| Stellar Parameter          | Value (This Project) | Value (Gajdoš et al.) | Error (%) |
|----------------------------|----------------------|-----------------------|-----------|
| Semi-Major Axis (R⊙)        | 4.511                | 4.189                 | 7.68      |
| Semi-Amplitude Velocity (km/s)| 24.015              | 22.28                 | 7.79      |
| Combined Mass (M⊙)          | 2.077                | 2                     | 3.85      |
| Temperature Ratio           | 1.036                | 1.164                 | 11.07     |
| Luminosity (L⊙)             | 14.85                | 14.4                  | 3.15      |
| Distance (parsec)           | 442.11               | 432.46                | 2.23      |

## References
1. Gajdoš et al., 2024 - *Analysis of KIC 7023917: Spotted Low-mass Ratio Eclipsing Binary with δ Scuti Pulsations*.
2. Lightkurve Collaboration - *Lightkurve: Kepler and TESS time series analysis in Python*.
3. Vallenari et al., 2023 - *Gaia data release 3-summary of the content and survey properties*.

