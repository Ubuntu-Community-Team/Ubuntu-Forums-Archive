---
title: "Cmake"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by nathanv221 on 2011-07-20
hey, i've just finished making changes to the program Slicer  on my computer. (i am a summer intern at Kitware) Slicer is a program that relies on Cmake for testing, the problem is that i cant remember how to make the test (Ctest) relize that i've made changes to Slicer. i know it's a simple command and i'm in the correct folder to do the change.

more info:
i am testing in the folder ~/Projects/Slicer4-Superbuild-Debug/Slicer-build$
the change i have made is renaming a file (i changed all code to match the new file name)
after running Ctest in -V (also know as verbose)  i get this:
313: Exception detected while reading /home/taylor/Projects/Slicer4/Applications/CLI/N4ITKBiasFieldCorrection/Testing/../Data/Baseline/he3corrected.nii :  Could not create IO object for file /home/taylor/Projects/Slicer4/Applications/CLI/N4ITKBiasFieldCorrection/Testing/../Data/Baseline/he3corrected.nii
313: The file doesn't exist. 
313: Filename = /home/taylor/Projects/Slicer4/Applications/CLI/N4ITKBiasFieldCorrection/Testing/../Data/Baseline/he3corrected.nii
313: <DartMeasurement name="BaselineImageName" type="text/string">he3corrected.nii</DartMeasurement>
313: Exception detected while reading /home/taylor/Projects/Slicer4/Applications/CLI/N4ITKBiasFieldCorrection/Testing/../Data/Baseline/he3corrected.nii :  Could not create IO object for file /home/taylor/Projects/Slicer4/Applications/CLI/N4ITKBiasFieldCorrection/Testing/../Data/Baseline/he3corrected.nii

the file he3corrected.nii has been renamed N4ITKBiasFildCorrection_he3corrected.nii

PLEASE NOTE: I am not trying to update to the latest git version of Cmake i am trying to update to my own changes.

---

### Post by nathanv221 on 2011-07-20
happened again.

---

