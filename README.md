# Performance Analysis of an InGaAs/HfO2 Gate-All-Around Nanowire FET Under Channel-Length Scaling (14, 10 and 7 nm)

Simulation study of a cylindrical In0.53Ga0.47As gate-all-around (GAA) nanowire FET with a HfO2 gate dielectric, built in **Silvaco ATLAS**. The channel length is scaled from 14 nm to 10 nm and 7 nm to see how short-channel effects develop and where leakage starts to dominate.

**Department of Electrical and Electronic Engineering, United International University, Dhaka, Bangladesh (2026)**

## Authors

- Md Atick Ahamed Rafid
- Md Samiul Islam
- Md Shahriyar Amin Shibbir
- Md Tanvir Alam
- Iqbal Bahar Chowdhury (Mentor)

## Overview

High-mobility III-V channels in a GAA geometry are a promising route to continued scaling, but short-channel behaviour needs careful study. This work extracts the threshold voltage, sub-threshold swing, DIBL, ON current and OFF current using one consistent set of definitions, so the scaling trends can be compared directly.

### Device structure

| Parameter | Value |
|---|---|
| Channel material | In0.53Ga0.47As (lattice matched to InP) |
| Channel (gate) length Lch | 14 / 10 / 7 nm |
| Nanowire diameter | 6 nm (radius 3 nm) |
| Gate dielectric | HfO2, εr = 22, 2 nm |
| Source/drain | n-type, 1×10²⁰ cm⁻³, 5 nm each |
| Channel doping | p-type, 1×10¹⁷ cm⁻³ |
| Gate work function | 5.0 eV |
| Interface fixed charge | 2×10¹² cm⁻² |
| Drain bias | 0.03 V and 1.0 V |

Only Lch changes between the three devices.

### Simulation setup

- **Tool:** Silvaco ATLAS 5.22.1.R, cylindrical coordinates
- **Framework:** drift-diffusion
- **Models:** Fermi-Dirac statistics, field-dependent mobility (Caughey-Thomas form), SRH recombination
- **Sweep:** VG from 0 to 1.0 V in 20 mV steps at VD = 0.03 V and 1.0 V
- **Not included:** quantum confinement, source-to-drain tunnelling, band non-parabolicity

### Parameter extraction

- **Vth:** constant current (ID = 10 nA); linear extrapolation used as a cross-check
- **SS:** maximum slope of log10(ID) at VD = 0.03 V
- **DIBL:** from the Vth shift between VD = 0.03 V and 1.0 V
- **ION / IOFF:** read at VG = 1 V and 0 V, VD = 1.0 V

## Key Results

| Lch (nm) | Vth (V) | SS (mV/dec) | DIBL (mV/V) | ION (A) | IOFF (A) | ION/IOFF |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 14 | 0.427 | 60.5 | 26.6 | 2.5×10⁻⁶ | 3.1×10⁻¹⁵ | 8.0×10⁸ |
| 10 | 0.362 | 62.9 | 47.4 | 2.9×10⁻⁶ | 1.4×10⁻¹³ | 2.1×10⁷ |
| 7 | 0.214 | 68.9 | 93.0 | 3.8×10⁻⁶ | 2.6×10⁻¹⁰ | 1.5×10⁴ |

- Scaling from 14 to 7 nm raises ION by about 52%.
- Gate control weakens: SS rises from 60.5 to 68.9 mV/dec, DIBL from 26.6 to 93.0 mV/V, and Vth rolls off from 0.427 to 0.214 V.
- IOFF increases by almost five orders of magnitude, so ION/IOFF drops from 8.0×10⁸ to 1.5×10⁴.
- The **10 nm** device is the best compromise (ION/IOFF of 2.1×10⁷, DIBL of 47.4 mV/V, SS of 62.9 mV/dec).
- The **7 nm** device still switches but is leaky and less suited to low-power use.

## Limitations

Quantum confinement and tunnelling are not modelled, so absolute values should be treated with care and the trends are the main takeaway. Leakage at 7 nm is likely underestimated.

## Repository Structure

```
├── report_paper/          # Research article (PDF)           
└── README.md
```
> Adjust the folder names to match your actual repository.

## Usage

1. Open the ATLAS deck for the desired channel length in Silvaco DeckBuild.
2. Run the VD = 0.03 V and VD = 1.0 V transfer-characteristic sweeps.
3. Extract Vth, SS, DIBL, ION and IOFF from the saved ID-VG data using the definitions above.

Requires a licensed copy of Silvaco ATLAS.

## Citation

```
M. A. A. Rafid, M. S. Islam, M. S. A. Shibbir, M. T. Alam, and I. B. Chowdhury,
"Performance Analysis of an InGaAs/HfO2 Gate-All-Around Nanowire FET Under
Channel-Length Scaling (14, 10 and 7 nm)," United International University, 2026.
```
