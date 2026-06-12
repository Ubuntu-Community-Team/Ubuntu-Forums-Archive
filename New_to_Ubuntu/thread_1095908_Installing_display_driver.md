---
title: "Installing display driver?"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by abybaddi on 2009-03-14
I've no display driver enabled on my ubuntu and I can't enable it from "Hardware drivers" as none is available. But I've a CD that came with my mother-board and there's a folder called Linux drivers.

So can anybody help me to compile and install the display driver?

ThanX in advance!!!

---

### Post by blueridgedog on 2009-03-14
Some more information might help.  What type of card?  What is the contents of the "linux drivers" folder?

---

### Post by abybaddi on 2009-03-14
Two folders "Audio" and "VGA" and one file named "FILELIST.TXT". And Motherboard is of asus.

---

### Post by abybaddi on 2009-03-14
VGA folder has "DRI.tgz", "KM400_Linux_Install.txt" and "KM-K8MXF40047.tgz".
When I open "KM400_Linux_Install.txt" and see the instructions I can't get anything of what is written.

---

### Post by abybaddi on 2009-03-14
Here are the contents of "KM400_Linux_Install.txt": Please **Guide ME!!!**
```

           ====================================================================
           Copyright (C) VIA Technologies, Inc. and S3G Technologies, Inc. 2002

                    VIA/S3G KM400/K8M800 Installation Notes for Linux XFree86
           ====================================================================


Installation:
=============

1.How to Install Linux Driver and utility

  1.1 Configure your hardware device when intalling Linux

      1.1.1 Video Configureation

            Please choose another video card, for example "S3 Savgae4 (generic)"
            because KM400/K8M800 graphic chip is not on the support list. 
            We will modify this configuration in step 3 for KM400/K8M800 
            graphic chip after the installation. If you choose to 
            "Skip X Configuration", you could configure X after 
            the installation following step 1.2.

      1.1.2 Monitor Configuration

            The installation program will attempt to detect your monitor to
            determine your machine's best display setting. You may also enter
            the horizontal and vertical synchonization ranges for your monitor.
            These value can be found in the documentation for your display.

      1.1.3 Custom X Configuration

            Please choose your login type as "text" because we need post
            configuration after the installation.

  1.2 Configure your hardware device after intalling Linux

      If you choose to "Skip X Configuration" when install Linux. Please do
      following step..

      1.2.1 Login as root

      1.2.2 Check is there a link point to /usr/X11R6/bin/XFree86

          # cd /etc/X11
          # ls -l X

          If there is no link named "X", then do following..
          # ln -s /usr/X11R6/bin/XFree86 X

          Note:
          If you skip the step of X setup when install Linux, there
          will be no link named "X" in /etc/X11.

      1.2.3 Run "xf86config" to configure your keyboard, mouse and monitor
          # xf86config

          The configuration program will create the file "XF86Conifg" in the
          /etc/X11 directory. If there is the file named "XF86Config-4",
          please remove or rename it.


  1.3 Install driver and utility

      a. Uncompress this file
         # tar zxvf KM-K8MXF400xx.tgz(x is version number)
      b. Installation XServer driver. 
         # ./vinstall 
  
  1.4 Install DRI library
     
      a. Uncompress DRI.tgz
    	 # tar zxvf DRI.tgz
      b. change directory into  DRI
	 # cd DRI
      c. Installation
	 #./minstall


Uninstallation:
===============

2.How to Uninstall Linux Driver and utility
  a. Uncompress this file
     # tar zxvf KM-K8MXF400xx.tgz(x is version number)

  b. Uninstallation
     # ./vuninstall
    
  c. Uncompress DRI.tgz
     # tar zxvf DRI.tgz

  d. Unstalllation DRI library
     # ./muninstall 


Configuration:
==============

3.How to Configure XFree86

  # login as root

  # Edit /etc/X11/XF86Confit-4 or XF86Config

  3.1 Set driver

      In the Section "Device", make sure the driver is "via".

            Driver "via"

      for example, if you choose "S3 Savge4 (generic)", please rename

            Driver "savage" to Driver "via"

  3.2 Add user define resolution

      If necessary, you can add extra resolution which non-define by XFree86 default.
      In the Section "Monitor", add following setting before "EndSection"

	  #Refresh Rate 60Hz
          ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
          ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
          ModeLine "800x480" 29.6 800 816 896 992 480 481 484 497
          ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
          ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
          ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
          ModeLine "1280x768" 87.04 1280 1376 1488 1800 768 771 777 806
          ModeLine "1280x800" 68.9 1280 1344 1368 1408 800 803 806 816
          Modeline "1400x1050" 122.61 1400 1488 1640 1880 1050 1051 1054 1087
	  #Refresh Rate 75Hz
          ModeLine "1280x768" 108.81 1280 1376 1488 1800 768 771 777 806
          Modeline "1400x1050" 155.85 1400 1496 1648 1896 1050 1051 1054 1096
	  #Refresh Rate 85Hz
          ModeLine "1280x768" 123.32 1280 1376 1488 1800 768 771 777 806
          Modeline "1400x1050" 179.26 1400 1504 1656 1912 1050 1051 1054 1103

  3.3 Change the Resolution & BPP

      3.3.1 Change BPP

         In the Section "Screen",

         DefaultDepth xx

         Note: xx can be 8, 16, 24, 32

      3.3.2. Change Resolution

         In the Subsection "Display" Section "Screen",

         For example, change to the resolution 800x600 of 32bpp

         Subsection "Display"
             Depth 24
             Modes "800x600"
         EndSubSection

         The supported resolution:
             "640x480" "720x480" "720x576" "800x600" "848x480" "856x480"
             "1024x512" "1024x768" "1152x864" "1280x768" "1280x960" "1280x1024"
             "1400x1050" "1600x1200"

  3.4 Device Selection

      3.4.1 Support Device

         UniChrome Family support 4 kinds of device: CRT, TV, LCD, DFP

      3.4.2 Active Device

         a. Active by default

            If there is no manually setting the CLE266 driver will accord with
            console mode active status (nomorlly, it will be CMOS setting) to
            active device in XWindow.

         b. Active manually

            The driver will auto detect the device connected or not. If the devices
            are connected. you can active device through Option in Section "Device"

            Option "ActiveDevice" "device1[,device2]"

            For example, the CRT and TV are connected and you would like to turn on
            them simultaneous.the option will be

            Option "ActiveDevice" "CRT,TV"

      3.4.3 Limitation

         For the timing issue. there is no simultaneous in TV + LCD/DVI case, but
         SAMM is ok.

  3.5 LCD Simultaneous

      3.5.1 LCD simultaneous "Center" mode

         Please add following setting in the Section "Device"

         Option "Center"

      3.5.2 LCD simultaneous "Expand" mode

         Please add following setting in the Section "Device"

         #Option "Center"

      3.5.3 Supported Panel Size & Mode

         a. Panel Size - 640x480
            mode:
                 640x480 -
                           support LCD simultaneous "Expand" and "Center" mode
                 800x600 -
                           support LCD simultaneous

                 720x480, 720x576, 800x600, 848x480, 856x480, 1024x768,
                 1152x864, 1280x768, 1280x960, 1280x1024, 1400x1050,
                 1600x1200 -
                           support LCD simultaneous virtual desktop mode

         a. Panel Size - 800x600
            mode:
                 640x480 -
                           support LCD simultaneous "Expand" and "Center" mode
                 800x600 -
                           support LCD simultaneous

                 1024x768, 1152x864, 1280x768, 1280x960, 1280x1024, 1400x1050,
                 1600x1200 -
                           support LCD simultaneous virtual desktop mode

         b. Panel Size - 1024x768
            mode:
                 640x480, 800x600 -
                           support LCD simultaneous "Expand" and "Center" mode

                 1024x768 -
                           support LCD simultaneous

                 1152x864, 1280x768, 1280x960, 1280x1024, 1400x1050, 1600x1200 -
                           support LCD simultaneous virtual desktop mode

         c. Panel Size - 1280x1024
            mode:
                 1280x768, 1280x960 -
                           not support LCD simultaneous

                 640x480, 800x600, 1024x768, 1152x864, 1280x768, 1280x960 -
                           support LCD simultaneous "Expand" and "Center" mode

                 1280x1024 -
                           support LCD simultaneous

                 1400x1050, 1600x1200 -
                           support LCD simultaneous virtual desktop mode

  3.6 TV Simultaneous

      3.6.1 Select TV Type

         You can use following setting in the Section "Device" to select "NTSC"
         or "PAL"

         Option "TVType" "NTSC" (or "PAL")

         If you don't set this option in the Section "Device", the driver will
         use the BIOS setting of TV_type of "Advanced Chipset Features"

      3.6.2 Select TV Output Signal

         The driver will auto detect the TV output signal is "Composit" or
         "S-Video". You can also use following setting in the Section "Device"
         to select "Composite", or "S-Video"

         Option "TVOutput" "Composite" (or "S-Video")

         If you would like to use "RGB" or "YCbCr" as your TV output signal,
         Please use following setting in the Section "Device" to select
         "RGB", or "YCbCr". These output signals are only VT1622.

         Option "TVOutput" "RGB" (or "YCbCr")

      3.6.3 Vertical Scan

         a. For TV Encoder - VT1621

            The driver support two kinds of TV vertical scan - under & over.
            You can use following setting in the Section "Device" to select.

            Option "TVVScan" "over" (or "under")

            If you don't set this option, the default value is "under".

         b. For TV Encoder - VT1622

            The driver support three kinds of TV vertical scan - under, over.
            You can use following setting in the Section "Device" to select.

            Option "TVVScan" "under" (or "over")

            If you don't set this option, the default value is "under".

      3.6.4 Enable DotCrawl

            You can use following setting in the Section "Device" to enable
            "DotCrawl".

            Option "TVDotCrawl"

      3.6.5 Supported TV Encoder & Mode

         a. TV Encoder - VT1621

            mode:
                 640x480, 800x600 -
                           support TV simultaneous

                 others -
                           support TV simultaneous virtual desktop mode

         b. TV Encoder - VT1622(A)/VT1623

            mode:
                 640x480, 800x600, 848x480, 1024x768 ,720x480(NTSC Only),
                 720x576(PAL Only)-
                           support TV simultaneous

                 others -
                           support TV simultaneous virtual desktop mode

  3.7 Others device related options

      3.7.1 Using non-DDC CRT

         Normally CRT has support DDC protocal provides CRT's infomation to driver.
         If your CRT hasn't support DDC or driver don't care CRT limitation. You
         can add following option.

         Option "NoDDCValue"

      3.7.2 Using 24-Bit Bus Width Digital Interface

         If using 24-Bit LVDS or 24-Bit TMDS.
         
         Option "BusWidth" "24Bit"

         If you don't set the option, driver will set 12-Bit Digital Interface 
         by default.

      3.7.3 Using Dual Edge Panel.

         If using Dual Edge Panel.

         Option "LCDDualEdge"

         If you don't set the option, driver will set single edge panel by default.

  3.8 HQV related options

      3.8.1 Select HQV assignment method

         You can use the following setting to change HQV feature manual switch 
         by application.
  	     
	 Option "HQVManualSwitch"
	 
	 If you don't set the option, the HQV feature will be assigned dynamically.

      3.8.2 Disable HQV vertical filter

         You can use the following setting to disable HQV vertical filter feature
         for video H/W overlay.
  	     
	 Option "NoHQVVFilter"
		 
	 If you don't set the option, the HQV vertical filter is enabled default
         in driver.
  
  3.9 Capture related options

      3.9.1 Turn off capture overscan function

         You can use following setting to turn off capture overscan function,
         then driver doesn't reduce the height of source image to prevent the 
         garbage line on top & bottom.

         Option "CaptureOverScanOff"

         If you don't set this option, driver will do overscan to the source 
         capture image.

      3.9.2 Select de-interlace mode

         You can use following setting in the Section "Device" to select "Bob"
         or "Weave" deinterlace mode for capture input 0 or capture input 1.

         Option "Cap0Deinterlace" "Bob" (or "Weave")
         Option "Cap1Deinterlace" "Bob" (or "Weave")

         If you don't set this option in the Section "Device", the default setting
         is "Weave" mode.

      3.9.3 Field swap

         You can use following setting in the Section "Device" to swap the input
         field from capture input 0. This option is for some device,ex: 
         Sigma Design EM8475 MPEG decoder device, which the input field sequence
         is mismatch with CLE266 capture function. Only capture input 0 has field
         swap function.

         Option "Cap0FieldSwap"

      3.9.4 No capture horizontal filter

         You can use following setting in the Section "Device" to disable horizontal
         filter for capture input 0 or capture input 1.

         Option "NoCap0HFilter"
         Option "NoCap1HFilter"

         If you don't set this option in the Section "Device", driver will 
         enable horizontal filter for capture input 0 or capture input 1 by
         default.

      3.9.5 i2c device auto detection

         You can use following setting in the Section "Device" to disable i2c 
         devide auto detection for capture input 0 or capture input 1. If you
         set the option, you MUST set the related options below.

         Option "Cap0NoAutoDetect"
         Option "Cap1NoAutoDetect"

         If you don't set this option in the Section "Device", driver will 
         auot-detect i2c device & initialize them if driver found any i2c 
         device by default.
         
      3.9.6 Data Width

         You can use following setting in the Section "Device" to set the output
         data width of video decoder attached to capture input 0 or capture input 1.

         Option "Cap0DataWidth" "8" (or "16")
         Option "Cap1DataWidth" "8" (or "16")

      3.9.7 Video decoder device

         You can use following setting in the Section "Device" to set the video 
         decoder device attached to capture input 0 or capture input 1.

         Option "Cap0VDODecoderDev" "SAA7113" (or "SAA7108", "SAA7114")
         Option "Cap1VDODecoderDev" "SAA7113" (or "SAA7108", "SAA7114")

      3.9.8 Video decoder device i2c slave address

         You can use following setting in the Section "Device" to set the slave
         address of video decoder device attached to capture input 0 or capture
         input 1. The value is just for example, the actual slave address is
         dependent on the H/W layout setting.

         Option "Cap0VDODecoderI2C" "72"
         Option "Cap1VDODecoderI2C" "74"

      3.9.9 Composite mode

         You can use following setting in the Section "Device" to set the Composite
         mode of video decoder device for capture input 0 or capture input 1. The 
         value is just for example, the actual value is dependent on the H/W layout 
         setting.

         Option "Cap0CompositeMode" "2"
         Option "Cap1CompositeMode" "2"

      3.9.10 SVideo mode

         You can use following setting in the Section "Device" to set the SVideo
         mode of video decoder device for capture input 0 or capture input 1. The 
         value is just for example, the actual value is dependent on the H/W layout 
         setting.

         Option "Cap0SVideoMode" "9"
         Option "Cap1SVideoMode" "7"

      3.9.11 Tuner mode

         You can use following setting in the Section "Device" to set the Tuner
         mode of video decoder device for capture input 0 or capture input 1. The 
         value is just for example, the actual value is dependent on the H/W layout 
         setting.

         Option "Cap0TunerMode" "0"
         Option "Cap1TunerMode" "0"

      3.9.12 Scaler function

         You can use following setting in the Section "Device" to set the scaler
         function of video decoder device for capture input 0 or capture input 1.
         "0" disable scaler function, "1" enable scaler function. Not all of the 
         video decoders have scaler function. About the detail, please refer to
         the video decoder specification.

         Option "Cap0Scaler" "0"
         Option "Cap1Scaler" "1"

      3.9.13 Brightness of video decoder

         You can use following setting in the Section "Device" to set the brightness
         value of video decoder device for capture input 0 or capture input 1.
         The valid range is 0-255.

         Option "Cap0Brightness" "119"
         Option "Cap1Brightness" "119"

      3.9.14 Contrast of video decoder

         You can use following setting in the Section "Device" to set the contrast
         value of video decoder device for capture input 0 or capture input 1.
         The valid range is 0-255.

         Option "Cap0Contrast" "95"
         Option "Cap1Contrast" "95"

      3.9.15 Hue of video decoder

         You can use following setting in the Section "Device" to set the hue
         value of video decoder device for capture input 0 or capture input 1.
         The valid range is 0-255.

         Option "Cap0Hue" "124"
         Option "Cap1Hue" "124"

      3.9.16 Saturation of video decoder

         You can use following setting in the Section "Device" to set the saturation
         value of video decoder device for capture input 0 or capture input 1.
         The valid range is 0-255.

         Option "Cap0Saturation" "95"
         Option "Cap1Saturation" "95"

      3.9.17 Standard of video decoder

         You can use following setting in the Section "Device" to set the standard
         mode of video decoder device for capture input 0 or capture input 1.

         Option "Cap0Standard" "NTSC" (or "PAL", "SECAM")
         Option "Cap1Standard" "NTSC" (or "PAL", "SECAM")

      3.9.18 Tuner device

         You can use following setting in the Section "Device" to set the tuner
         device attached to capture input 0 or capture input 1.

         Option "Cap0TunerDev" "FI1236MK2"
         Option "Cap1TunerDev" "FI1236MK2"

      3.9.19 Tuner device i2c slave address

         You can use following setting in the Section "Device" to set the slave
         address of tuner device attached to capture input 0 or capture
         input 1. The value is just for example, the actual slave address is
         dependent on the H/W layout setting.

         Option "Cap0TunerI2C" "198"
         Option "Cap1TunerI2C" "192"
```

---

### Post by overdrank on 2009-03-14
Hi and you may look at [UniChrome]("https://help.ubuntu.com/community/UniChrome")

---

### Post by Troll_the_Great on 2009-03-14
What type of card do you have? ATI? nVidia?

---

### Post by abybaddi on 2009-03-14
Ati...

---

### Post by abybaddi on 2009-03-14
> **overdrank said:**
> Hi and you may look at [UniChrome]("https://help.ubuntu.com/community/UniChrome")

Mine is KM400a which is not on the list.

---

### Post by Troll_the_Great on 2009-03-14
If you have ATI, you can install it automatically with an application called Envy.Open a terminal and type
```
sudo apt-get install envyng-gtk
```
You will find it under Applications-System Tools-EnvyNG. Start it and after that is pretty simple.
Cheers!

---

### Post by abybaddi on 2009-03-14
There's nothing like that in that menu.

---

