---
title: "Kodak ESP3 - work around?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by dniezby on 2009-02-13
Has anyone found a work around to get Kodak ESP 3 Printers to work in Linux?

I thought for sure there would be someone to have written their own version of a print driver for it by now.

BTW, I'm on a Dual Boot system. Vista / Ubuntu 8.10

Maybe there is a way to install it on Vista and access it's drivers??

---

### Post by Mark Phelps on 2009-02-13
Just checked CUPS and there's no driver listed for the Kodak printer.

As to using Vista or its drivers, basically, no.

Is this a relatively new printer? If so, expect to wait a while, maybe a LONG while, for CUPS to catch up.

---

### Post by dniezby on 2009-02-13
Yeah, it's a new Kodak printer - The ESP3.

I'm actually surprised that someone hasn't taken the windows driver apart and created a linux version. I thought coders loved to do that stuff. I know I would be working on it right now if I knew how to do it. Just because I could.

Well, also because they basically seem to have given Linux the proverbial finger.  I'd like to give it back.

Funny thing is, their developers WANT to work on a unix version (according to an article I read by one of their developers) 

Let's get on this boys (and girls).

Heck, I remember the days when all of the Linux device drivers had to be written by end users. Where are you now ?  Help !! 
LOL.

---

### Post by dniezby on 2009-02-14
What about my work around question? Anyone know a way I can get it print without having to save the document, restart into Vista and print?

I was soooooo set to drop Vista for good, then this printer stuff popped up. Dang it.

---

### Post by wolfen69 on 2009-02-14
this won't solve your problem, but in the future, if you don't mind using HP printers, go that route. nearly every single HP printer will work "out of the box" in linux.

the only possible solution i can think of, is to install xp in virtualbox under ubuntu. i got tired of doing that a long time ago and threw out my lexmark and got an HP. a small price to pay to finally rid myself of windows.

---

### Post by dniezby on 2009-02-14
I would, but I just bought the printer. 

I was tired of the huge costs of printing with HP so I bought this Kodak ESP3. Then I learned of the problems with Kodak print drivers and Linux.

Unfortunately, I was turned on to Ubuntu AFTER I bought the printer.  I'm only about two weeks into Ubuntu.

---

### Post by alanjohnsmith on 2009-07-27
Has anyone solved this?
I've just installed Ubuntu, about a month after buying my new printer Kodak ESP3.
I really don't want to go back to Windows, but I can't justify buying a new printer when the Kodak one is a month old for the pleasure of having Ubuntu.
Please tell me someone has found a workaround!

Alan.

---

### Post by dniezby on 2009-07-27
Yeah, I solved it. I bit the bullet and went back to windows.

That was extremely painful to do. 

But the printer and program support for Ubuntu just isn't there yet.  Even the printers that I could use were still limited in features. 

I long for the day when Ubuntu can run all of the same programs.

---

### Post by SunnyRabbiera on 2009-07-27
> **dniezby said:**
> Yeah, I solved it. I bit the bullet and went back to windows.

That was extremely painful to do. 

But the printer and program support for Ubuntu just isn't there yet.  Even the printers that I could use were still limited in features. 

I long for the day when Ubuntu can run all of the same programs.

This is not the fault of ubuntu or linux, I would blame Kodac for having bad support towards linux

---

### Post by alanjohnsmith on 2009-07-28
Ah well, maybe one day Kodak will consider the market worth its while.

---

### Post by drabzz on 2009-10-18
I have tried leverage on Kodak as follows:

"I have an ESP3 which I am unable to use with my Ubuntu Linux 9.04 system, there are no Linux/Unix drivers for this printer; therefore the printer is currently unfit for the purpose for which I purchased it. Most printer manufacturers provide Linux drivers for their equipment, so it was reasonable for me to purchase this printer with the expectation of Linux driver support. Are Kodak likely to release Linux drivers in the near future, or will I need to exercise my right under UK law to claim a full refund for the printer I cannot use? If this is the case, many of my compatriots may follow suit."

Even if it doesn't do the trick, at least it helped me let off steam!:P

---

### Post by ORVUEDGK360 on 2009-10-29
is it possible to use mac os x drivers for this printer in ubuntu 9.04 if so could someone please walk me threw it?

---

### Post by drabzz on 2009-10-30
Mac drivers don't work.

I gave up looking for a solution, sold my Kodak ESP 3 and bought a HP. Like most Ubuntu guys will tell us, HPs seem to work straight out of the box on Linux systems. 

Kodak Support are in an, "I'm not listening." loop.

I'm loving the HP C4480 though...;)

---

### Post by frank cox on 2009-11-03
> **drabzz said:**
> Mac drivers don't work.

I gave up looking for a solution, sold my Kodak ESP 3 and bought a HP. Like most Ubuntu guys will tell us, HPs seem to work straight out of the box on Linux systems. 

Kodak Support are in an, "I'm not listening." loop.

I'm loving the HP C4480 though...;)

What about Epson? Is it likely older printers will have software available?

---

### Post by mothership111 on 2009-11-03
Well you can  get the ddp from the apple drivers package, if you look for it, it references the special apple driver, i'm going to try and remove those references and see if this is enough and postscript jobs will go through, so save this as the ppd and see if that works. 

Its a start anyway

kd_esp3_custom.ppd FILE STARTS NEXT LINE
```
*PPD-Adobe: "4.3"
*% PPD file for KODAK ESP All-in-One Printer with CUPS.
*% Created by the CUPS PPD Compiler v1.2.3.
*% Copyright (c) 2006-2009 by Eastman Kodak Company, All Rights Reserved.
*% This PPD file may be freely used and distributed under the terms of the GNU GPL.
*FormatVersion: "4.3"
*FileVersion: "4.2"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*PCFileName: "KD_ESP3.PPD"
*Product: "(Eastman Kodak Company KODAK ESP-3 AiO)"
*Product: "(Eastman Kodak Company KODAK ESP 5 AiO)"
*Manufacturer: "Kodak"
*ModelName: "KODAK ESP All-in-One Printer"
*ShortNickName: "KODAK ESP 3/5 AiO Printer"
*NickName: "KODAK ESP 3/5 All-in-One Printer"
*PSVersion: "(3010.000) 705"
*PSVersion: "(3010.000) 707"
*PSVersion: "(3010.000) 815"
*PSVersion: "(3010.000) 853"
*LanguageLevel: "3"
*ColorDevice: True
*DefaultColorSpace: RGB
*FileSystem: False
*Throughput: "30"
*LandscapeOrientation: Plus90
*TTRasterizer: Type42
*% Driver-defined attributes...
*1284DeviceID: "MFG:Eastman Kodak Company;MDL:KODAK ESP-3 AiO;"
*1284DeviceID: "MFG:Eastman Kodak Company;MDL:KODAK ESP 5 AiO;"
*DefaultOutputOrder: Reverse
*APSupportsCustomColorMatching: True
*APDefaultCustomColorMatchingProfile: "AdobeRGB"
*APCustomColorMatchingProfile: "AdobeRGB"
*APSupportsCustomColorMatching: "sRGB"
*cupsVersion: 1.4
*cupsModelNumber: 3
*cupsManualCopies: True
*OpenUI *PageSize/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: Letter
*PageSize Letter/US Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize Legal/US Legal: "<</PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageSize Executive/US Executive: "<</PageSize[522 756]/ImagingBBox null>>setpagedevice"
*PageSize A4/A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize A5/A5: "<</PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageSize A6/A6: "<</PageSize[297 420]/ImagingBBox null>>setpagedevice"
*PageSize ISOB5/ISO B5: "<</PageSize[499 709]/ImagingBBox null>>setpagedevice"
*PageSize EnvMonarch/Monarch Envelope: "<</PageSize[279 540]/ImagingBBox null>>setpagedevice"
*PageSize Env9/#9 Envelope: "<</PageSize[279 639]/ImagingBBox null>>setpagedevice"
*PageSize Env10/#10 Envelope: "<</PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageSize EnvA2/A2 Envelope: "<</PageSize[315 414]/ImagingBBox null>>setpagedevice"
*PageSize EnvC5/C5 Envelope: "<</PageSize[459 649]/ImagingBBox null>>setpagedevice"
*PageSize EnvC6/C6 Envelope: "<</PageSize[323 459]/ImagingBBox null>>setpagedevice"
*PageSize EnvDL/DL Envelope: "<</PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageSize Photo_4x6/4x6 in: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x7/4x7 in: "<</PageSize[288 504]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x12/4x12 in: "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"
*PageSize Photo5x7/5x7 in: "<</PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageSize Photo8x10/8x10 in: "<</PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageSize LetterBorderless/Borderless US Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize A4Borderless/Borderless A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x6Borderless/Borderless 4x6 in: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x7Borderless/Borderless 4x7 in: "<</PageSize[288 504]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x12Borderless/Borderless 4x12 in: "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"
*PageSize Photo5x7Borderless/Borderless 5x7 in: "<</PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageSize 8x10Borderless/Borderless 8x10 in: "<</PageSize[576 720]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize
*OpenUI *PageRegion/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: Letter
*PageRegion Letter/US Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion Legal/US Legal: "<</PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageRegion Executive/US Executive: "<</PageSize[522 756]/ImagingBBox null>>setpagedevice"
*PageRegion A4/A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion A5/A5: "<</PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageRegion A6/A6: "<</PageSize[297 420]/ImagingBBox null>>setpagedevice"
*PageRegion ISOB5/ISO B5: "<</PageSize[499 709]/ImagingBBox null>>setpagedevice"
*PageRegion EnvMonarch/Monarch Envelope: "<</PageSize[279 540]/ImagingBBox null>>setpagedevice"
*PageRegion Env9/#9 Envelope: "<</PageSize[279 639]/ImagingBBox null>>setpagedevice"
*PageRegion Env10/#10 Envelope: "<</PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageRegion EnvA2/A2 Envelope: "<</PageSize[315 414]/ImagingBBox null>>setpagedevice"
*PageRegion EnvC5/C5 Envelope: "<</PageSize[459 649]/ImagingBBox null>>setpagedevice"
*PageRegion EnvC6/C6 Envelope: "<</PageSize[323 459]/ImagingBBox null>>setpagedevice"
*PageRegion EnvDL/DL Envelope: "<</PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageRegion Photo_4x6/4x6 in: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x7/4x7 in: "<</PageSize[288 504]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x12/4x12 in: "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"
*PageRegion Photo5x7/5x7 in: "<</PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageRegion Photo8x10/8x10 in: "<</PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageRegion LetterBorderless/Borderless US Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion A4Borderless/Borderless A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x6Borderless/Borderless 4x6 in: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x7Borderless/Borderless 4x7 in: "<</PageSize[288 504]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x12Borderless/Borderless 4x12 in: "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"
*PageRegion Photo5x7Borderless/Borderless 5x7 in: "<</PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageRegion 8x10Borderless/Borderless 8x10 in: "<</PageSize[576 720]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion
*DefaultImageableArea: Letter
*ImageableArea Letter/US Letter: "14.17 14.17 597.82 777.82"
*ImageableArea Legal/US Legal: "14.17 14.17 597.82 993.82"
*ImageableArea Executive/US Executive: "14.17 14.17 507.82 741.82"
*ImageableArea A4/A4: "14.17 14.17 580.82 827.82"
*ImageableArea A5/A5: "14.17 14.17 405.82 580.82"
*ImageableArea A6/A6: "14.17 14.17 282.82 405.82"
*ImageableArea ISOB5/ISO B5: "14.17 14.17 484.82 694.82"
*ImageableArea EnvMonarch/Monarch Envelope: "14.17 42.52 264.83 497.48"
*ImageableArea Env9/#9 Envelope: "14.17 42.52 264.83 596.48"
*ImageableArea Env10/#10 Envelope: "14.17 42.52 282.83 641.48"
*ImageableArea EnvA2/A2 Envelope: "14.17 42.52 300.83 371.48"
*ImageableArea EnvC5/C5 Envelope: "14.17 42.52 444.83 606.48"
*ImageableArea EnvC6/C6 Envelope: "14.17 42.52 308.83 416.48"
*ImageableArea EnvDL/DL Envelope: "14.17 42.52 297.83 581.48"
*ImageableArea Photo_4x6/4x6 in: "14.17 14.17 273.82 417.82"
*ImageableArea Photo4x7/4x7 in: "14.17 14.17 273.82 489.82"
*ImageableArea Photo4x12/4x12 in: "14.17 14.17 273.82 849.82"
*ImageableArea Photo5x7/5x7 in: "14.17 14.17 345.82 489.82"
*ImageableArea Photo8x10/8x10 in: "14.17 14.17 561.82 705.82"
*ImageableArea LetterBorderless/Borderless US Letter: "0.00 0.00 612.00 792.00"
*ImageableArea A4Borderless/Borderless A4: "0.00 0.00 595.00 842.00"
*ImageableArea Photo4x6Borderless/Borderless 4x6 in: "0.00 0.00 288.00 432.00"
*ImageableArea Photo4x7Borderless/Borderless 4x7 in: "0.00 0.00 288.00 504.00"
*ImageableArea Photo4x12Borderless/Borderless 4x12 in: "0.00 0.00 288.00 864.00"
*ImageableArea Photo5x7Borderless/Borderless 5x7 in: "0.00 0.00 360.00 504.00"
*ImageableArea 8x10Borderless/Borderless 8x10 in: "0.00 0.00 576.00 720.00"
*DefaultPaperDimension: Letter
*PaperDimension Letter/US Letter: "612.00 792.00"
*PaperDimension Legal/US Legal: "612.00 1008.00"
*PaperDimension Executive/US Executive: "522.00 756.00"
*PaperDimension A4/A4: "595.00 842.00"
*PaperDimension A5/A5: "420.00 595.00"
*PaperDimension A6/A6: "297.00 420.00"
*PaperDimension ISOB5/ISO B5: "499.00 709.00"
*PaperDimension EnvMonarch/Monarch Envelope: "279.00 540.00"
*PaperDimension Env9/#9 Envelope: "279.00 639.00"
*PaperDimension Env10/#10 Envelope: "297.00 684.00"
*PaperDimension EnvA2/A2 Envelope: "315.00 414.00"
*PaperDimension EnvC5/C5 Envelope: "459.00 649.00"
*PaperDimension EnvC6/C6 Envelope: "323.00 459.00"
*PaperDimension EnvDL/DL Envelope: "312.00 624.00"
*PaperDimension Photo_4x6/4x6 in: "288.00 432.00"
*PaperDimension Photo4x7/4x7 in: "288.00 504.00"
*PaperDimension Photo4x12/4x12 in: "288.00 864.00"
*PaperDimension Photo5x7/5x7 in: "360.00 504.00"
*PaperDimension Photo8x10/8x10 in: "576.00 720.00"
*PaperDimension LetterBorderless/Borderless US Letter: "612.00 792.00"
*PaperDimension A4Borderless/Borderless A4: "595.00 842.00"
*PaperDimension Photo4x6Borderless/Borderless 4x6 in: "288.00 432.00"
*PaperDimension Photo4x7Borderless/Borderless 4x7 in: "288.00 504.00"
*PaperDimension Photo4x12Borderless/Borderless 4x12 in: "288.00 864.00"
*PaperDimension Photo5x7Borderless/Borderless 5x7 in: "360.00 504.00"
*PaperDimension 8x10Borderless/Borderless 8x10 in: "576.00 720.00"
*MaxMediaWidth: "612.00"
*MaxMediaHeight: "1008.00"
*HWMargins: 0.00 0.00 0.00 0.00
*CustomPageSize True: "pop pop pop <</PageSize[5 -2 roll]/ImagingBBox null>>setpagedevice"
*ParamCustomPageSize Width: 1 points 279.00 612.00
*ParamCustomPageSize Height: 2 points 360.00 1008.00
*ParamCustomPageSize WidthOffset: 3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation: 5 int 0 0
*RequiresPageRegion All: True
*OpenUI *ColorModel/Color Mode: PickOne
*OrderDependency: 10.0 AnySetup *ColorModel
*DefaultColorModel: RGB
*ColorModel RGB/Color: "<</cupsColorSpace 1/cupsColorOrder 0/cupsCompression 0>>setpagedevice"
*CloseUI: *ColorModel
*OpenUI *Resolution: PickOne
*OrderDependency: 10.0 AnySetup *Resolution
*DefaultResolution: 600dpi
*Resolution 300dpi/Draft: "<</HWResolution[300 300]/cupsBitsPerColor 8/cupsRowCount 0/cupsRowFeed 0/cupsRowStep 0>>setpagedevice"
*Resolution 600dpi/Normal: "<</HWResolution[600 600]/cupsBitsPerColor 8/cupsRowCount 0/cupsRowFeed 0/cupsRowStep 0>>setpagedevice"
*Resolution 600dpi/Best: "<</HWResolution[600 600]/cupsBitsPerColor 8/cupsRowCount 0/cupsRowFeed 0/cupsRowStep 0>>setpagedevice"
*CloseUI: *Resolution
*DefaultFont: Courier
*Font AvantGarde-Book: Standard "(1.05)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(1.05)" Standard ROM
*Font AvantGarde-Demi: Standard "(1.05)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(1.05)" Standard ROM
*Font Bookman-Demi: Standard "(1.05)" Standard ROM
*Font Bookman-DemiItalic: Standard "(1.05)" Standard ROM
*Font Bookman-Light: Standard "(1.05)" Standard ROM
*Font Bookman-LightItalic: Standard "(1.05)" Standard ROM
*Font Courier: Standard "(1.05)" Standard ROM
*Font Courier-Bold: Standard "(1.05)" Standard ROM
*Font Courier-BoldOblique: Standard "(1.05)" Standard ROM
*Font Courier-Oblique: Standard "(1.05)" Standard ROM
*Font Helvetica: Standard "(1.05)" Standard ROM
*Font Helvetica-Bold: Standard "(1.05)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Oblique: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(1.05)" Standard ROM
*Font Palatino-Bold: Standard "(1.05)" Standard ROM
*Font Palatino-BoldItalic: Standard "(1.05)" Standard ROM
*Font Palatino-Italic: Standard "(1.05)" Standard ROM
*Font Palatino-Roman: Standard "(1.05)" Standard ROM
*Font Symbol: Special "(001.005)" Special ROM
*Font Times-Bold: Standard "(1.05)" Standard ROM
*Font Times-BoldItalic: Standard "(1.05)" Standard ROM
*Font Times-Italic: Standard "(1.05)" Standard ROM
*Font Times-Roman: Standard "(1.05)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(1.05)" Standard ROM
*Font ZapfDingbats: Special "(001.005)" Special ROM
*% End of KD_ESP3.PPD, 13148 bytes.
```

---

### Post by drabzz on 2009-11-03
> **frank cox said:**
> What about Epson? Is it likely older printers will have software available?

On the check I made with Epson Support, it seems they are Windoze and Mac only. But there are Linux speciality websites which may have the drivers you require:

[http://www.linux-drivers.org/]("http://www.linux-drivers.org/")

[http://avasys.jp/eng/linux_driver/]("http://avasys.jp/eng/linux_driver/")

---

### Post by stinkinrich88 on 2009-11-22
> **mothership111 said:**
> Well you can  get the ddp from the apple drivers package, if you look for it, it references the special apple driver, i'm going to try and remove those references and see if this is enough and postscript jobs will go through, so save this as the ppd and see if that works. 

Its a start anyway

kd_esp3_custom.ppd FILE STARTS NEXT LINE
```
*PPD-Adobe: "4.3"
*% PPD file for KODAK ESP All-in-One Printer with CUPS.
*% Created by the CUPS PPD Compiler v1.2.3.
*% Copyright (c) 2006-2009 by Eastman Kodak Company, All Rights Reserved.
*% This PPD file may be freely used and distributed under the terms of the GNU GPL.
*FormatVersion: "4.3"
*FileVersion: "4.2"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*PCFileName: "KD_ESP3.PPD"
*Product: "(Eastman Kodak Company KODAK ESP-3 AiO)"
*Product: "(Eastman Kodak Company KODAK ESP 5 AiO)"
*Manufacturer: "Kodak"
*ModelName: "KODAK ESP All-in-One Printer"
*ShortNickName: "KODAK ESP 3/5 AiO Printer"
*NickName: "KODAK ESP 3/5 All-in-One Printer"
*PSVersion: "(3010.000) 705"
*PSVersion: "(3010.000) 707"
*PSVersion: "(3010.000) 815"
*PSVersion: "(3010.000) 853"
*LanguageLevel: "3"
*ColorDevice: True
*DefaultColorSpace: RGB
*FileSystem: False
*Throughput: "30"
*LandscapeOrientation: Plus90
*TTRasterizer: Type42
*% Driver-defined attributes...
*1284DeviceID: "MFG:Eastman Kodak Company;MDL:KODAK ESP-3 AiO;"
*1284DeviceID: "MFG:Eastman Kodak Company;MDL:KODAK ESP 5 AiO;"
*DefaultOutputOrder: Reverse
*APSupportsCustomColorMatching: True
*APDefaultCustomColorMatchingProfile: "AdobeRGB"
*APCustomColorMatchingProfile: "AdobeRGB"
*APSupportsCustomColorMatching: "sRGB"
*cupsVersion: 1.4
*cupsModelNumber: 3
*cupsManualCopies: True
*OpenUI *PageSize/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: Letter
*PageSize Letter/US Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize Legal/US Legal: "<</PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageSize Executive/US Executive: "<</PageSize[522 756]/ImagingBBox null>>setpagedevice"
*PageSize A4/A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize A5/A5: "<</PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageSize A6/A6: "<</PageSize[297 420]/ImagingBBox null>>setpagedevice"
*PageSize ISOB5/ISO B5: "<</PageSize[499 709]/ImagingBBox null>>setpagedevice"
*PageSize EnvMonarch/Monarch Envelope: "<</PageSize[279 540]/ImagingBBox null>>setpagedevice"
*PageSize Env9/#9 Envelope: "<</PageSize[279 639]/ImagingBBox null>>setpagedevice"
*PageSize Env10/#10 Envelope: "<</PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageSize EnvA2/A2 Envelope: "<</PageSize[315 414]/ImagingBBox null>>setpagedevice"
*PageSize EnvC5/C5 Envelope: "<</PageSize[459 649]/ImagingBBox null>>setpagedevice"
*PageSize EnvC6/C6 Envelope: "<</PageSize[323 459]/ImagingBBox null>>setpagedevice"
*PageSize EnvDL/DL Envelope: "<</PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageSize Photo_4x6/4x6 in: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x7/4x7 in: "<</PageSize[288 504]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x12/4x12 in: "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"
*PageSize Photo5x7/5x7 in: "<</PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageSize Photo8x10/8x10 in: "<</PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageSize LetterBorderless/Borderless US Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize A4Borderless/Borderless A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x6Borderless/Borderless 4x6 in: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x7Borderless/Borderless 4x7 in: "<</PageSize[288 504]/ImagingBBox null>>setpagedevice"
*PageSize Photo4x12Borderless/Borderless 4x12 in: "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"
*PageSize Photo5x7Borderless/Borderless 5x7 in: "<</PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageSize 8x10Borderless/Borderless 8x10 in: "<</PageSize[576 720]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize
*OpenUI *PageRegion/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: Letter
*PageRegion Letter/US Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion Legal/US Legal: "<</PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageRegion Executive/US Executive: "<</PageSize[522 756]/ImagingBBox null>>setpagedevice"
*PageRegion A4/A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion A5/A5: "<</PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageRegion A6/A6: "<</PageSize[297 420]/ImagingBBox null>>setpagedevice"
*PageRegion ISOB5/ISO B5: "<</PageSize[499 709]/ImagingBBox null>>setpagedevice"
*PageRegion EnvMonarch/Monarch Envelope: "<</PageSize[279 540]/ImagingBBox null>>setpagedevice"
*PageRegion Env9/#9 Envelope: "<</PageSize[279 639]/ImagingBBox null>>setpagedevice"
*PageRegion Env10/#10 Envelope: "<</PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageRegion EnvA2/A2 Envelope: "<</PageSize[315 414]/ImagingBBox null>>setpagedevice"
*PageRegion EnvC5/C5 Envelope: "<</PageSize[459 649]/ImagingBBox null>>setpagedevice"
*PageRegion EnvC6/C6 Envelope: "<</PageSize[323 459]/ImagingBBox null>>setpagedevice"
*PageRegion EnvDL/DL Envelope: "<</PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageRegion Photo_4x6/4x6 in: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x7/4x7 in: "<</PageSize[288 504]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x12/4x12 in: "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"
*PageRegion Photo5x7/5x7 in: "<</PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageRegion Photo8x10/8x10 in: "<</PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageRegion LetterBorderless/Borderless US Letter: "<</PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion A4Borderless/Borderless A4: "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x6Borderless/Borderless 4x6 in: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x7Borderless/Borderless 4x7 in: "<</PageSize[288 504]/ImagingBBox null>>setpagedevice"
*PageRegion Photo4x12Borderless/Borderless 4x12 in: "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"
*PageRegion Photo5x7Borderless/Borderless 5x7 in: "<</PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageRegion 8x10Borderless/Borderless 8x10 in: "<</PageSize[576 720]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion
*DefaultImageableArea: Letter
*ImageableArea Letter/US Letter: "14.17 14.17 597.82 777.82"
*ImageableArea Legal/US Legal: "14.17 14.17 597.82 993.82"
*ImageableArea Executive/US Executive: "14.17 14.17 507.82 741.82"
*ImageableArea A4/A4: "14.17 14.17 580.82 827.82"
*ImageableArea A5/A5: "14.17 14.17 405.82 580.82"
*ImageableArea A6/A6: "14.17 14.17 282.82 405.82"
*ImageableArea ISOB5/ISO B5: "14.17 14.17 484.82 694.82"
*ImageableArea EnvMonarch/Monarch Envelope: "14.17 42.52 264.83 497.48"
*ImageableArea Env9/#9 Envelope: "14.17 42.52 264.83 596.48"
*ImageableArea Env10/#10 Envelope: "14.17 42.52 282.83 641.48"
*ImageableArea EnvA2/A2 Envelope: "14.17 42.52 300.83 371.48"
*ImageableArea EnvC5/C5 Envelope: "14.17 42.52 444.83 606.48"
*ImageableArea EnvC6/C6 Envelope: "14.17 42.52 308.83 416.48"
*ImageableArea EnvDL/DL Envelope: "14.17 42.52 297.83 581.48"
*ImageableArea Photo_4x6/4x6 in: "14.17 14.17 273.82 417.82"
*ImageableArea Photo4x7/4x7 in: "14.17 14.17 273.82 489.82"
*ImageableArea Photo4x12/4x12 in: "14.17 14.17 273.82 849.82"
*ImageableArea Photo5x7/5x7 in: "14.17 14.17 345.82 489.82"
*ImageableArea Photo8x10/8x10 in: "14.17 14.17 561.82 705.82"
*ImageableArea LetterBorderless/Borderless US Letter: "0.00 0.00 612.00 792.00"
*ImageableArea A4Borderless/Borderless A4: "0.00 0.00 595.00 842.00"
*ImageableArea Photo4x6Borderless/Borderless 4x6 in: "0.00 0.00 288.00 432.00"
*ImageableArea Photo4x7Borderless/Borderless 4x7 in: "0.00 0.00 288.00 504.00"
*ImageableArea Photo4x12Borderless/Borderless 4x12 in: "0.00 0.00 288.00 864.00"
*ImageableArea Photo5x7Borderless/Borderless 5x7 in: "0.00 0.00 360.00 504.00"
*ImageableArea 8x10Borderless/Borderless 8x10 in: "0.00 0.00 576.00 720.00"
*DefaultPaperDimension: Letter
*PaperDimension Letter/US Letter: "612.00 792.00"
*PaperDimension Legal/US Legal: "612.00 1008.00"
*PaperDimension Executive/US Executive: "522.00 756.00"
*PaperDimension A4/A4: "595.00 842.00"
*PaperDimension A5/A5: "420.00 595.00"
*PaperDimension A6/A6: "297.00 420.00"
*PaperDimension ISOB5/ISO B5: "499.00 709.00"
*PaperDimension EnvMonarch/Monarch Envelope: "279.00 540.00"
*PaperDimension Env9/#9 Envelope: "279.00 639.00"
*PaperDimension Env10/#10 Envelope: "297.00 684.00"
*PaperDimension EnvA2/A2 Envelope: "315.00 414.00"
*PaperDimension EnvC5/C5 Envelope: "459.00 649.00"
*PaperDimension EnvC6/C6 Envelope: "323.00 459.00"
*PaperDimension EnvDL/DL Envelope: "312.00 624.00"
*PaperDimension Photo_4x6/4x6 in: "288.00 432.00"
*PaperDimension Photo4x7/4x7 in: "288.00 504.00"
*PaperDimension Photo4x12/4x12 in: "288.00 864.00"
*PaperDimension Photo5x7/5x7 in: "360.00 504.00"
*PaperDimension Photo8x10/8x10 in: "576.00 720.00"
*PaperDimension LetterBorderless/Borderless US Letter: "612.00 792.00"
*PaperDimension A4Borderless/Borderless A4: "595.00 842.00"
*PaperDimension Photo4x6Borderless/Borderless 4x6 in: "288.00 432.00"
*PaperDimension Photo4x7Borderless/Borderless 4x7 in: "288.00 504.00"
*PaperDimension Photo4x12Borderless/Borderless 4x12 in: "288.00 864.00"
*PaperDimension Photo5x7Borderless/Borderless 5x7 in: "360.00 504.00"
*PaperDimension 8x10Borderless/Borderless 8x10 in: "576.00 720.00"
*MaxMediaWidth: "612.00"
*MaxMediaHeight: "1008.00"
*HWMargins: 0.00 0.00 0.00 0.00
*CustomPageSize True: "pop pop pop <</PageSize[5 -2 roll]/ImagingBBox null>>setpagedevice"
*ParamCustomPageSize Width: 1 points 279.00 612.00
*ParamCustomPageSize Height: 2 points 360.00 1008.00
*ParamCustomPageSize WidthOffset: 3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation: 5 int 0 0
*RequiresPageRegion All: True
*OpenUI *ColorModel/Color Mode: PickOne
*OrderDependency: 10.0 AnySetup *ColorModel
*DefaultColorModel: RGB
*ColorModel RGB/Color: "<</cupsColorSpace 1/cupsColorOrder 0/cupsCompression 0>>setpagedevice"
*CloseUI: *ColorModel
*OpenUI *Resolution: PickOne
*OrderDependency: 10.0 AnySetup *Resolution
*DefaultResolution: 600dpi
*Resolution 300dpi/Draft: "<</HWResolution[300 300]/cupsBitsPerColor 8/cupsRowCount 0/cupsRowFeed 0/cupsRowStep 0>>setpagedevice"
*Resolution 600dpi/Normal: "<</HWResolution[600 600]/cupsBitsPerColor 8/cupsRowCount 0/cupsRowFeed 0/cupsRowStep 0>>setpagedevice"
*Resolution 600dpi/Best: "<</HWResolution[600 600]/cupsBitsPerColor 8/cupsRowCount 0/cupsRowFeed 0/cupsRowStep 0>>setpagedevice"
*CloseUI: *Resolution
*DefaultFont: Courier
*Font AvantGarde-Book: Standard "(1.05)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(1.05)" Standard ROM
*Font AvantGarde-Demi: Standard "(1.05)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(1.05)" Standard ROM
*Font Bookman-Demi: Standard "(1.05)" Standard ROM
*Font Bookman-DemiItalic: Standard "(1.05)" Standard ROM
*Font Bookman-Light: Standard "(1.05)" Standard ROM
*Font Bookman-LightItalic: Standard "(1.05)" Standard ROM
*Font Courier: Standard "(1.05)" Standard ROM
*Font Courier-Bold: Standard "(1.05)" Standard ROM
*Font Courier-BoldOblique: Standard "(1.05)" Standard ROM
*Font Courier-Oblique: Standard "(1.05)" Standard ROM
*Font Helvetica: Standard "(1.05)" Standard ROM
*Font Helvetica-Bold: Standard "(1.05)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Oblique: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(1.05)" Standard ROM
*Font Palatino-Bold: Standard "(1.05)" Standard ROM
*Font Palatino-BoldItalic: Standard "(1.05)" Standard ROM
*Font Palatino-Italic: Standard "(1.05)" Standard ROM
*Font Palatino-Roman: Standard "(1.05)" Standard ROM
*Font Symbol: Special "(001.005)" Special ROM
*Font Times-Bold: Standard "(1.05)" Standard ROM
*Font Times-BoldItalic: Standard "(1.05)" Standard ROM
*Font Times-Italic: Standard "(1.05)" Standard ROM
*Font Times-Roman: Standard "(1.05)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(1.05)" Standard ROM
*Font ZapfDingbats: Special "(001.005)" Special ROM
*% End of KD_ESP3.PPD, 13148 bytes.
```

Nah, doesn't work... Printer doesn't do anything when I print something using this pdp

---

### Post by frank cox on 2009-11-23
My solution right now is to run XP on an old P$ I got for free and link them together on the network 
Then hooked the machines through a switch so I can switch the keyboard , monitor and keyboard from one machine to the other in one second.

May not be exotic , pretty, or energy efficient but it is a whole lot faster than rebooting, VM's or whatever.
Works for me . Now I can print with my Kodak and save money on ink and play windows games , run Quicken etc with no worries about viruses.

---

### Post by wesblake on 2010-01-06
Hi. I made the mistake of buying the ESP-7, trying to save ink costs like the rest of you, even though Ive been on Linux for almost 10 years.
HUGE mistake. I should have never strayed from HP, it's true, HP has the BEST support for Linux/Unix operating systems.
It's Kodak's fault, not Linux, for not supporting Linux. However, that's not the only problem, this thing has basic design flaws. For one, if a cartridge runs out, you can no longer scan either! I've had many printers, and never had one where the scanner did not work independently of the printer. There is NO reason why I should not be able to scan even if I'm out of ink.
The other thing to note is that despite all their marketing on low cost ink, I've found by owning this printer and further researching that all ink-jet printers cost about the same to print. Next time you get a new cartridge, do a count on the prints you get out of it. A full set of ink for this thing is $25 bucks because the cartridges last half as long! I am changing this thing out like once a month, THAT IS WHY THE INK "COSTS LESS"!
My HP, Epsons, and Cannons before it all cost roughly $50-60 for ink, but I only had to change them out ~ every few, even up to 6 months, so some of the others are actually cheaper to run.
This thing is junk, and others have bought there digital camera's which are absolute junk. I would recommend not buying ANY Kodak product, I will not ever again. It's back to HP printers only for me. (Their cameras are junk too, but you don't go to a computer manufacturer for a camera, guess I should not have gone to a camera manufacturer for a printer!)
P.S., I am getting by with my ESP until I can buy an HP buy running Winblows XP in VirtualBox, works fine, just a slower way of using it.

---

### Post by paulnewall on 2010-03-23
I wrote a driver for Kodak ESP5250, it might also work with the ESP 3?
[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)

---

### Post by thecure on 2010-04-01
> **paulnewall said:**
> I wrote a driver for Kodak ESP5250, it might also work with the ESP 3?
[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)

You Rock! Your driver works well (some colors off but not a big issue for me) Kodak ESP 9. (Lucid Lynx beta)

---

### Post by kcgrad on 2010-04-10
> **paulnewall said:**
> I wrote a driver for Kodak ESP5250, it might also work with the ESP 3?
[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)

I am new to cups and its administration.  When I try to install the driver, I'm getting the error that follows.  Am I missing an obvious dependency?

After running the "make" command....

#
# Dependencies...
#
      ***
      *** Error: /usr/include/cups/raster.h is not installed!
      ***
      *** Install cups raster library package
      *** for Ubuntu: sudo apt-get install libcupsimage2
      ***
make: *** [all-test] Error 1


When I try sudo apt-get install libcupsimage2, the system states that libcupsimage2 is already the newest version.

I appreciate any advice you have to offer (including the suggestion to go out and buy HP... it's already tempting).

kcgrad
(obvious newb)

(Editing to include Ubuntu version 9.10 and Kodak printer ESP 7)

---

### Post by thecure on 2010-04-11
> **kcgrad said:**
> I am new to cups and its administration.  When I try to install the driver, I'm getting the error that follows.  Am I missing an obvious dependency?

After running the "make" command....

#
# Dependencies...
#
      ***
      *** Error: /usr/include/cups/raster.h is not installed!
      ***
      *** Install cups raster library package
      *** for Ubuntu: sudo apt-get install libcupsimage2
      ***
make: *** [all-test] Error 1


When I try sudo apt-get install libcupsimage2, the system states that libcupsimage2 is already the newest version.

I appreciate any advice you have to offer (including the suggestion to go out and buy HP... it's already tempting).

kcgrad
(obvious newb)

(Editing to include Ubuntu version 9.10 and Kodak printer ESP 7)

You need to install libcupsimage2-dev then it'll work

---

### Post by kcgrad on 2010-04-11
> **thecure said:**
> You need to install libcupsimage2-dev then it'll work

Excellent!  After removing CUPS, then reinstalling it as well as libcupsimage2-dev, the ESP 7 printer is working (Ubuntu 9.10).

Great job!

kcgrad

---

### Post by markrayne on 2010-05-03
I have installed c2esp05 on three computers running Ubuntu. On the first, using Ubuntu 9.10 (Karmic), it works fine. I can now use my wireless-networked Kodak ESP 7 for the first time from Ubuntu (no need to switch to Windows - brilliant!). On the second computer, (an aged laptop with limited RAM running Xubuntu 9.10) printing on the ESP7 also now works fine. 

However, on the third computer, a desktop running Ubuntu 8.10 (Jaunty), only black and white printing is possible. Attemping to print a test page from the "printer properties window" with colour enabled results in the printer state: "Processing - specified color format is not supported", followed by printer state: "Idle - no pages found", and a blank sheet of paper is ejected from the printer. It works with Black&white selected instead of colour, however.

I don't want to update this computer to Karmic at present as it is not my computer and I don't want to risk data loss.

---

### Post by bkuhns on 2010-05-05
I've been bummed for the last ~15 months since my wife bought the Kodak ESP7 that I can't print to it from my Ubuntu boxes. I just stumbled on this ESP 5250 driver and was amazed when an Ubuntu test page started spitting out of the printer. Unfortunately, it stopped about 30% the way through and just ejected the paper without finishing. I've printed several times again and every time it gets about 30-40% through, stops, then feeds the paper out without finishing. :(

So close yet so far, any ideas?

---

### Post by paulnewall on 2010-05-14
I don't have any clear idea what the problem will be but I'd suggest:
1. Make sure you have the most recent version of c2esp - I've made a lot of versions.
2. Try monitoring the memory use while it generates the print data, maybe you are using a lot of swap, slowing your PC and the printer gets fed up waiting for data?
3. Try printing black and white, or draft, or both and try printing some things other than the test page to see if they work.

---

### Post by bwallum on 2010-06-12
> **paulnewall said:**
> I wrote a driver for Kodak ESP5250, it might also work with the ESP 3?
[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)

Ant idea how to get it running in64 bit 10.4? I'm trying to get an ESP3 to work.

---

### Post by Morimando on 2010-06-25
This is the most awesome news! I own a Kodak ESP3 and it's about the last thing i needed to keep a Windows around for (occasional printing). I hope this works w/ amd64 lynx :D

---

### Post by Thelasko on 2010-06-25
> **bwallum said:**
> Ant idea how to get it running in64 bit 10.4? I'm trying to get an ESP3 to work.

Try compiling from source. (tar.gz)

I don't know what the dependencies are, but you will at least need to install the package "build-essential"

P.S. Good work! Ubuntu users can potentially save a lot of money on ink.

---

### Post by sgtslwilson on 2010-09-01
> **paulnewall said:**
> I wrote a driver for Kodak ESP5250, it might also work with the ESP 3?
[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)



Thank you, Paul. Your driver worked for my mom's printer. Perfect. Good job.

Lance

---

### Post by walt.smith1960 on 2010-09-01
is Brother.  I have 2,both networked.  My only complaint with the MFC-7820N is it can be pretty slow with second and subsequent pages.  The MFC-6490CW works beautifully.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html). The installation instructions look more complicated than they are,  many entries do not apply to Ubuntu-Debian releases.

---

### Post by topias.l on 2010-09-13
I just installed the drivers today for my Kodak ESP-3 printer and the test page turned out perfect! Thanks

---

### Post by diverbelow on 2010-09-23
> **bwallum said:**
> Ant idea how to get it running in64 bit 10.4? I'm trying to get an ESP3 to work.

Here is what I did:
you can use the archive manager to open up the deb package, then open up the data.tar.gz to extract /./usr/share/ppd/ once extracted, I did a network search for the Dell P703w in printing and browsed for the ppd file in the c2esp folder, and installed the Kodak_ESP_5xxx_Series.ppd file and was able to print a test page.

Next, need to work on the network scanner part.

---

### Post by Morimando on 2010-09-30
The driver works very fine with 10.04 amd64.
The only issue I got (last tested with driver version 08, just installed 12 today) is that photo-printing was really screwed-up (lines in the picture, colors not too great).
But 90% of the time I use the ESP to print documents, which now works perfectly using this driver. Many thanks, again!

---

### Post by mister_playboy on 2010-10-17
> **paulnewall said:**
> I wrote a driver for Kodak ESP5250, it might also work with the ESP 3?
[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)

Excellent... I will give this a try. :KS

I have an ESP3 and I selected "ESP5200" as the driver... test page print worked perfectly!  Thank you so much!

---

### Post by Scooter_X on 2011-01-16
I got it printing color, but not black... Why would that be?

edit: both black and color cartridges are brand-spankin' new

Double edit: Why in the heck is there a 'black' or 'color' selector button?! It was on 'color' and now it's on 'black'. It printed black just fine. I then tested part of a document in blue and it printed out the blue lines just fine, but the black stuff that should be above the blue lines didn't appear and the black lines that were below the blue ones got chopped in half, horizontally.  Still working and waiting to see if anyone knows what's up.

---

### Post by paulnewall on 2011-01-29
reasons for black/colour options are:
1. writing a driver is hard, and you start with black only because that is much simpler. Then you add the colour option later. And you keep the black option so people can still print something if the colour does not work properly.
2. slow PCs take ages to print in colour. and you need more memory.

---

### Post by Lena1224 on 2011-05-05
I'm new to Ubuntu, my brother in law installed it for me. He said it was better then the windows I was running. I too am having the printer problem, mine mostly is the need for the scanner attached to it with the ESP3. I'm not even sure what a cups is or anything like that. I have learned how to do a bit in the terminal by some trial and error but if anyone could give a step by step way to make this work I would greatly appreciate it.

---

