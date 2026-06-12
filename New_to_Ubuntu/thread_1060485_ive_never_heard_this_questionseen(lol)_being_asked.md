---
title: "ive never heard this question/seen(lol) being asked!!!!"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by nubix on 2009-02-04
best distro for a high end computer?
i finally decided to dual boot linux/vista because i have a multitude of of useless/unused applications unbelievable fragmentation, possible spyware/virus infestation (huge outgoing traffic!!!) so i figured it would be best for a fresh start. i think ill be more conservative with program installation. linux distro with optimal useless eyecandy right after install? also refresh my mind with the whole dual booting thing please.(ive done it before). also ive heard that there are many problems with logitec usb headsets im using one for my main sound output device so id like to know about problems befor i go dual booting

again your guys are the best!! i give all my days worth of thanks.

------------------
System Information
------------------
Time of this report: 
       Machine name: you would like to know
   Operating System: Windows Vista™ Home Premium (6.0, Build 6001) Service Pack 1 (6001.vistasp1_gdr.080917-1612)
           Language: English (Regional Setting: English)
System Manufacturer: XFX68L
       System Model: XFX Nforce 680i LT
               BIOS: Phoenix - AwardBIOS v6.00PG
          Processor: Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz (2 CPUs), ~2.4GHz
             Memory: 2046MB RAM
          Page File: 754MB used, 3576MB available
        Windows Dir: E:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6001.18000 32bit Unicode



---------------
Display Devices
---------------
        Card name: NVIDIA GeForce 8800 GT 
     Manufacturer: NVIDIA
        Chip type: GeForce 8800 GT
         DAC type: Integrated RAMDAC
       
   Display Memory: 1269 MB
 Dedicated Memory: 501 MB
    Shared Memory: 767 MB
     Current Mode: 1440 x 900 (32 bit) (60Hz)
          Monitor: Generic PnP Monitor
      Driver Name: nvd3dum.dll,nvwgf2um.dll
   Driver Version: 7.15.0011.7519 (English)
      DDI Version: 10
Driver Attributes: Final Retail
 Driver Date/Size: 5/16/2008 13:01:00, 5689344 bytes
      WHQL Logo'd: n/a
  WHQL Date Stamp: n/a
Device Identifier: {D7B71E3E-4551-11CF-AD46-0AE802C2CA35}
        Vendor ID: 0x10DE
        Device ID: 0x0611
        SubSys ID: 0xC8013842
      Revision ID: 0x00A2
      Revision ID: 0x00A2
    

-------------
Sound Devices
-------------
            Description: Speakers (2- Logitech USB Headset)
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: USB\VID_046D&PID_0A0C&REV_1013&MI_00
        Manufacturer ID: 65535
             Product ID: 65535
                   Type: WDM
            Driver Name: USBAUDIO.sys
         Driver Version: 6.00.6001.18000 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: n/a
          Date and Size: 1/19/2008 00:53:23, 73088 bytes
            Other Files: 
        Driver Provider: Microsoft
         HW Accel Level: Basic
              Cap Flags: 0x0
    Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No

            Description: Digital Output Device (SPDIF) (High Definition Audio Device)
 Default Sound Playback: No
 Default Voice Playback: No
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0885&SUBSYS_10ECE601&REV_1001
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: HdAudio.sys
         Driver Version: 6.00.5840.16387 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: n/a
          Date and Size: 11/2/2006 02:36:49, 235520 bytes
            Other Files: 
        Driver Provider: Microsoft
         HW Accel Level: Basic
              Cap Flags: 0x0
    Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No



------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 54.8 GB
Total Space: 238.5 GB
File System: NTFS
      Model: ST325041 0AS SCSI Disk Device

      Drive: D:
      Model: LITE-ON DVDRW LH-20A1S SCSI CdRom Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 6.00.6001.18000 (English), 1/19/2008 00:49:51, 67072 bytes


judging by the system specs that ive given you, if you can see any other issues i might run into please let me know.

---

### Post by petervk on 2009-02-04
Burn the livecd to an iso and try booting it first. Try out your usb headset there and see if it works. The nvidia card should work great.

---

### Post by nubix on 2009-02-04
yea looking forward to using that beast with compiz fusion!!!!:p

---

### Post by Walter Melon on 2009-02-04
I have an nvidia graphics card and since it isnt open source, the live cd will boot up with standard resolution - probably 800x640.  But after you install just go to System->Administration->Software Sources and check proprietary drivers and restricted software. 

Also make sure you install Windows first then linux as the windows partitioner won't recognize the linux partitions.    As petervk said burn a liveCD and see if any major problems pop up.

---

### Post by DariusS on 2009-02-04
> **Walter Melon said:**
> I have an nvidia graphics card and since it isnt open source, the live cd will boot up with standard resolution - probably 800x640.  But after you install just go to System->Administration->Software Sources and check proprietary drivers and restricted software. 

Also make sure you install Windows first then linux as the windows partitioner won't recognize the linux partitions.    As petervk said burn a liveCD and see if any major problems pop up.

About the video drivers, you can actually (in 8.10) enable/install restricted drivers while still on the liveCD.

---

### Post by nubix on 2009-02-04
the last time i booted a live cd i could have sworn you could...

---

### Post by SuperSonic4 on 2009-02-04
It's not asked because you can have any Linux you like on a high end pc.

I think Mandriva looks good as my own opinion

---

### Post by Walter Melon on 2009-02-04
I thought you couldn't because I've only installed 8.04.

---

### Post by Gotaro on 2009-02-04
Not to knock you or anything, but I wouldn't exactly consider that system "high end"! ;P  As far as the most native eyecandy, anything with the KDE 4.2 desktop environment is probably your best bet.  It can be installed on any Linux distribution, but Kubuntu is the name of the Ubuntu version that comes preloaded with KDE.  It isn't 4.2 by default, so you'd have to upgrade.  You also will probably want to get Compiz-fusion for the most visually pleasing and customizable experience.  This can also be loaded onto any distribution.

---

### Post by nubix on 2009-02-04
i have my headset enabled under volume preferences and no sound.

---

### Post by nubix on 2009-02-04
the only thing i can get going is a beep when i test the pipelines

---

