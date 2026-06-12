---
title: "how to compress multiple pdf files with ghostscript"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by captain_rob on 2010-10-27
Hi,

Can someone tell me how I can compress multiple pdf files with ghostscript? 

For a single file I use 

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

But using *.pdf for input en output file doesnt work.

Thanks in advance

---

### Post by meske on 2011-05-25
You'll need to write a script to do it.  

You can pass multiple file names as the input for this string.  Each file name needs to be separated by a space, but they all need to be on the same line (i.e no line breaks / CR's).

For example, in one of my scipts, I have this:

/usr/local/bin/gs -dNOPAUSE -dBATCH -sDEVICE=laserjet -sOutputFile=$x `cat $i`

$x is the output file name, and 'cat $i' is a file that was created  by another process that has all the files I want combined into the output file. I built a script for converting PDF's to PCL's for Windows.  I'm sure you could modify this or use the logic to create one for linux.

> 
echo off
:: PDF to PCL Converter.  Needs Ghostscript locally, and installed here: "C:\Program Files\gs\gs9.02\bin\gswin32c.exe"
:: Other versions of GS will work, but the script will have to be updated.  
:: Users can enter the breakpoint for the PCL files.  If none is provided, 100 is used.
cls
echo This program will take all the PDF files in the current directory
echo and group them into PCL files.  If you ran
echo this from the command line, you could enter the breakpoint for 
echo number of PDF files per PCL. If left blank or not entered, the 
echo program defaults to 100.
echo.
echo If you want to continue, hit any key and please wait for the 
echo program to complete processing (could take a while).
echo If you want to stop now, hit CTRL-C and exit out of the batch.
pause

setlocal enabledelayedexpansion
set INC=%1
if "%1%" == "" set INC=100
SET GSS=
SET CTR=0
SET FL=1

for %%i in (*.pdf) DO (
SET GSS=!GSS! "%%i"
SET /a CTR+=1
echo !CTR! COUNTER !FL! OUTPUTFILE NUMBER
  if !CTR! == %INC% (

    "C:\Program Files\gs\gs9.02\bin\gswin32c.exe" -dNOPAUSE -dBATCH -sDEVICE=laserjet -sOutputFile=File_!FL!.pcl !GSS!
    echo "C:\Program Files\gs\gs9.02\bin\gswin32c.exe" -dNOPAUSE -dBATCH -sDEVICE=laserjet -sOutputFile=File_!FL!.pcl !GSS!
    set /a FL+=1
    echo !FL! FL
    set CTR=0
    set GSS=

  )

)
if NOT !CTR! == 0 (
echo LAST PROCESS
    "C:\Program Files\gs\gs9.02\bin\gswin32c.exe" -dNOPAUSE -dBATCH -sDEVICE=laserjet -sOutputFile=File_!FL!.pcl !GSS!
)


endlocal
echo Complete.
echo on


---

