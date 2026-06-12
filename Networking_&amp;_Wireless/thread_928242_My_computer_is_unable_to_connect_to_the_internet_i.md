---
title: "My computer is unable to connect to the internet in Ubuntu but can in Windows XP"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Elliander on 2008-09-23
I installed Ubuntu 7.10 for an AMD 64-bit a few months ago, as a dual boot with Windows XP Home Edition 32-bit. At the time I was using an Ethernet card, and everything worked fine. I didn't even have to configure anything, the internet worked on it's own.

Since then I had to move the computer, right now another computer is plugged in to the Ethernet and this computer is using a wireless connection.

Right now, I have internet access and strong connections to the wireless router using Windows XP but no connection at all in Ubuntu. 

Ubuntu is my first non-Windows operating system. (well, I used apple before that, but that was years and years ago.) And I really don't know the first thing about getting this to work.

I don't even know if Ubuntu sees the drivers or not, and I don't see any means of repairing the connection. I found places to change IP, but I have to manually type the network name and even then it won't seem to see it.

I was really getting to like Ubuntu, but I need Internet Access. Is there any way I can get it to work?


I am using 2 SATA-150 465 GB, the first has a split partition, with 20 GB currently set to Ubuntu. Which can be adjusted if needed. I am using 1 DVD-RW, and while I do have a floppy drive, I think it has cobwebs in it from lack of use. I have plenty of USB drives if I need to copy files over to install anything manually. (though I have no idea how to install something manually in Ubuntu either) I am using an Nvidia GeForce 5500 FX 128 MB VIdeo card which has no problems. My Ethernet card is built into the motherboard. 

Broadcom 802.11 b/g WLAN
Driver: 3.100.65.1
BCMWL5.SYS
PCI Slot 2

I am using a Linksys Router with wireless and ethernet.


My CPU is rated at 2.3 Ghz but seems to read as 1.6 Ghz in my DxDiag information:

Below is the DXDiag information gathered in Windows XP. (the OS I have to use to go online to write this.) I cut a heap out since it was really long.


------------------
System Information
------------------
Time of this report: 9/23/2008, 18:30:42
       Machine name: DREAM_MACHINE
   Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_qfe.071023-1323)
           Language: English (Regional Setting: English)
System Manufacturer: MICRO-STAR INTERNATIONAL CO., LTD
       System Model: MS-7142
               BIOS: Phoenix - AwardBIOS v6.00PG
          Processor: AMD Sempron(tm) Processor 2800+,  MMX,  3DNow, ~1.6GHz
             Memory: 1984MB RAM
          Page File: 352MB used, 2917MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

------------
DxDiag Notes
------------
  DirectX Files Tab: No problems found.
      Display Tab 1: No problems found.
        Sound Tab 1: No problems found.
          Music Tab: No problems found.
          Input Tab: No problems found.
        Network Tab: No problems found.

---------------
Display Devices
---------------
        Card name: NVIDIA GeForce FX 5200
     Manufacturer: NVIDIA
        Chip type: GeForce FX 5200
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0322&SUBSYS_01AD196E&REV_A1
   Display Memory: 256.0 MB
     Current Mode: 1024 x 768 (32 bit) (75Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: nv4_disp.dll
   Driver Version: 6.14.0011.6375 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 10/4/2007 18:14:00, 5783424 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: nv4_mini.sys
    Mini VDD Date: 10/4/2007 18:14:00, 6854464 bytes
Device Identifier: {D7B71E3E-4062-11CF-3962-A62100C2CB35}
        Vendor ID: 0x10DE
        Device ID: 0x0322
        SubSys ID: 0x01AD196E
      Revision ID: 0x00A1
      Revision ID: 0x00A1
      Video Accel: ModeMPEG2_A ModeMPEG2_B ModeMPEG2_C ModeMPEG2_D 
 Deinterlace Caps: {212DC722-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,2) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {212DC723-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_MedianFiltering 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC722-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,2) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {212DC723-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_MedianFiltering 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC722-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,2) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {212DC723-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_MedianFiltering 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC722-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,2) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {212DC723-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_MedianFiltering 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

-------------
Sound Devices
-------------
            Description: Vinyl AC'97 Audio (WAVE)
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: PCI\VEN_1106&DEV_3059&SUBSYS_04301462&REV_60
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: vinyl97.sys
         Driver Version: 6.14.0001.4170 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 8/10/2006 05:32:14, 204672 bytes
            Other Files: 
        Driver Provider: VIA Technologies, Inc.
         HW Accel Level: Full
              Cap Flags: 0xF5F
    Min/Max Sample Rate: 8000, 96000
Static/Strm HW Mix Bufs: 1, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No
               Registry: OK
      Sound Test Result: Not run

---------------------
Sound Capture Devices
---------------------
            Description: Vinyl AC'97 Audio (WAVE)
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: vinyl97.sys
         Driver Version: 6.14.0001.4170 (English)
      Driver Attributes: Final Retail
          Date and Size: 8/10/2006 05:32:14, 204672 bytes
              Cap Flags: 0x41
           Format Flags: 0xFFF

-----------
DirectMusic
-----------
        DLS Path: C:\WINDOWS\SYSTEM32\drivers\GM.DLS
     DLS Version: 1.00.0016.0002
    Acceleration: n/a
           Ports: Microsoft Synthesizer, Software (Not Kernel Mode), Output, DLS, Internal, Default Port
                  Vinyl AC'97 Audio (WAVE), Software (Kernel Mode), Output, DLS, Internal
                  Microsoft MIDI Mapper [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  Microsoft GS Wavetable SW Synth [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
        Registry: OK
     Test Result: Not run

-------------------
DirectInput Devices
-------------------
      Device Name: Mouse
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a

      Device Name: Keyboard
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a

Poll w/ Interrupt: No
         Registry: OK

-----------
USB Devices
-----------
+ USB Root Hub
| Vendor/Product ID: 0x1106, 0x3038
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 3/27/2008 21:43:01, 59392 bytes
| Driver: usbd.sys, 8/4/2004 07:00:00, 4736 bytes
| 
+-+ USB Human Interface Device
| | Vendor/Product ID: 0x093A, 0x2510
| | Location: USB OPTICAL MOUSE
| | Matching Device ID: usb\class_03&subclass_01
| | Service: HidUsb
| | Driver: hidclass.sys, 3/27/2008 21:40:58, 36864 bytes
| | Driver: hidparse.sys, 8/4/2004 07:00:00, 24960 bytes
| | Driver: hid.dll, 3/27/2008 21:54:28, 20992 bytes
| | Driver: hidusb.sys, 8/4/2004 07:00:00, 9600 bytes
| | 
| +-+ HID-compliant mouse
| | | Vendor/Product ID: 0x093A, 0x2510
| | | Matching Device ID: hid_device_system_mouse
| | | Service: mouhid
| | | Driver: mouclass.sys, 3/27/2008 21:54:28, 23040 bytes
| | | Driver: mouhid.sys, 3/27/2008 21:53:13, 12160 bytes

------------
PS/2 Devices
------------
+ Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
| Matching Device ID: *pnp0303
| Service: i8042prt
| Driver: i8042prt.sys, 8/4/2004 07:00:00, 52736 bytes
| Driver: kbdclass.sys, 8/4/2004 07:00:00, 24576 bytes
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 06:01:08, 40840 bytes
| Driver: kbdclass.sys, 8/4/2004 07:00:00, 24576 bytes
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 06:01:08, 40840 bytes
| Driver: mouclass.sys, 3/27/2008 21:54:28, 23040 bytes

----------------------------
DirectPlay Service Providers
----------------------------
DirectPlay8 Modem Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 Serial Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 IPX Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 TCP/IP Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
Internet TCP/IP Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.2180)
IPX Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.2180)
Modem Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.2180)
Serial Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.2180)

DirectPlay Voice Wizard Tests: Full Duplex: Not run, Half Duplex: Not run, Mic: Not run
DirectPlay Test Result: Not run
Registry: OK

-------------------
DirectPlay Adapters
-------------------
DirectPlay8 Serial Service Provider: COM1
DirectPlay8 Serial Service Provider: COM2
DirectPlay8 TCP/IP Service Provider: Wireless Network Connection - IPv6 - fe80::218:f3ff:fe3c:c641
DirectPlay8 TCP/IP Service Provider: Teredo Tunneling Pseudo-Interface - IPv6 - fe80::ffff:ffff:fffd
DirectPlay8 TCP/IP Service Provider: Automatic Tunneling Pseudo-Interface - IPv6 - fe80::5efe:
DirectPlay8 TCP/IP Service Provider: Wireless Network Connection - IPv4 - 

------------------------
Disk & DVD/CD-ROM Drives
------------------------

      Drive: C:
 Free Space: 115.4 GB
Total Space: 446.9 GB
File System: NTFS
      Model: SAMSUNG HD501LJ

      Drive: E:
 Free Space: 69.6 GB
Total Space: 476.9 GB
File System: NTFS
      Model: SAMSUNG HD501LJ

      Drive: D:
      Model: SONY DVD RW DRU-510A
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.3126 (English), 3/27/2008 21:40:37, 62592 bytes

---

### Post by willca on 2008-09-24
Lets figure out first if you wireless nic is even running.

sudo iwconfig
sudo iwlist wlan0 scan

If both gave outputs then its setup. Otherwise try this while on the wired internet connection.

sudo apt-get update
sudo apt-get install b43-fwcutter
and follow the instructions.

---

### Post by superprash2003 on 2008-09-24
if you are unable to see wifi networks then try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Elliander on 2008-11-15
I was able to solve this problem by buying an Atheros Chipset Network card. I found out that most companies selling network cards will sell two different cards as the same thing. Which explained why one card I had wouldn't work when in the past the same card name would work. After some research I found out that because the Atheros provides Unix drivers, then any card made with an Atheros Chipset will work, and it did right away without having to configure anything.

---

