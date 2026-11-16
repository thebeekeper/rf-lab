# RF Lab

Small RF boards I designed in Altium Designer, each built around one RF building block: attenuators, phase shifters, a power detector, a directional coupler and a SAW device.
Every board is a 50 Ω design with edge-mount SMA connectors.

> **Why there are no design files here:** these boards were made for lab work, so the schematics, layouts and gerbers stay private. This repo describes what each board does and how it was designed.

## The boards

| Board | Key part | Band | What it does |
|---|---|---|---|
| [Wideband attenuator, 0–8 V](#wideband-attenuators) | Mini-Circuits EVA-3000+ | 50 MHz – 3 GHz | Voltage-controlled attenuator |
| [Wideband attenuator, 0–12 V](#wideband-attenuators) | Mini-Circuits SVA-2000+ | 50 MHz – 2 GHz | Voltage-controlled attenuator |
| [Variable attenuator](#variable-attenuator) | Qorvo RFSA2033 | 50 MHz – 6 GHz | Voltage-controlled attenuator, 3.3 V supply |
| [Power detector](#power-detector) | MAX4003 | 100 MHz – 2.5 GHz | Turns RF power into a DC voltage |
| [Phase shifter, 100 MHz](#phase-shifters) | Mini-Circuits JSPHS-150+ | 100 – 150 MHz | Voltage-controlled phase shift |
| [Phase shifter, 433 MHz](#phase-shifters) | Mini-Circuits JSPHS-661+ | 400 – 660 MHz | Voltage-controlled phase shift |
| [Directional coupler](#directional-coupler) | Mini-Circuits TCD-20-4+ | 5 MHz – 1 GHz | Samples the signal at 20 dB down |
| [SAW device board](#saw-device-board) | Custom SAW device | ~500 MHz | Test fixture for a custom SAW device |

## Wideband attenuators

Two versions of the same idea, one for each control range: an RF in and an RF out on SMA, and a control voltage that sets the attenuation.
The control input is filtered with a small LC network (330 nH, 100 pF and 1 nF) so supply noise doesn't modulate the RF path.

## Variable attenuator

A Qorvo RFSA2033 analog attenuator covering 50 MHz to 6 GHz.
It runs from 3.3 V with a filtered supply rail, and the control voltage comes in on a 3-pin header.
The RF input and output are AC-coupled with 1 nF capacitors.

## Power detector

A MAX4003 RF detector with a 50 Ω input termination.
It outputs a DC voltage that tracks the input power from 100 MHz to 2.5 GHz, on a 3-pin header next to the 3.3 V supply.

## Phase shifters

Two boards with the same layout idea: RF in, RF out and a bias voltage on SMA, so the phase can be swept from a bench supply or a signal generator.
One covers 100–150 MHz, the other 400–660 MHz for the 433 MHz ISM band.
The 100 MHz board uses JLCPCB's stack-up, so its 50 Ω lines are sized for the fab's real dielectric.

## Directional coupler

A Mini-Circuits TCD-20-4+ 20 dB coupler from 5 MHz to 1 GHz.
The main line runs straight through, the coupled port has its own SMA, and the unused port is terminated in 50 Ω.

## SAW device board

A test board for a custom two-port SAW device with a designed centre frequency of about 500 MHz.
Each side has an LC matching network (20 nH and 16 nH inductors with 6.2 pF capacitors) to bring the SAW's input and output close to 50 Ω.

## Tools

Altium Designer · JLCPCB
