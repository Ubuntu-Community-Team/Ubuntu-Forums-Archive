---
title: "Ndiswrapper on Xubuntu 7.04?"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by deinonychus75 on 2007-06-17
Trying Linux for the first time.  I have Xubuntu 7.04 as the primary OS on an IBM T23.  For some reason, Ubuntu did not want to install even though the CD checked out fine as having no defects.  Xubuntu installed easily.  So I guess that's my first question - anyone have a stab at why that would be?  The T23 is slightly older, slower technology.  This particular one only has 256MB of RAM, which I think could have been a good part of the problem.  Second question is - should I be able to install ndiswrapper on Xubuntu 7.04?  I'm short on time so haven't been able to read as many web sites as I'd like to on the subject, but I've tried.  DL'd ndiswrapper, and I'm trying to learn the command line and Synaptic Package Manager, but so far I've just been met with failure and frustration.  Lots of errors, warnings, and permission denied when trying to install so far.  As I said, I'm not being lazy not trying to find the info. on my own, just short on time.  Anyone who might be able to help, your assistance is sincerely appreciated.  I'm trying to get life into a Motorola WN825G, which is the reason I'm trying.  Haven't even been able to load the drivers yet, nevermind ndiswrapper.

---

### Post by ugm6hr on 2007-06-17
I don't think Xubuntu has the facility to compile (missing build-essential), and you can't install that without internet via Xubuntu.  

So the first question is - do you have ethernet access?  

If so you should be able to use Synaptic to install ndisgtk (which should install everything necessary), which gives a GUI for ndiswrapper.

If not - assuming you have i386 Xubuntu - then you have to go to (and download from):
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main)

Then just double-click the files in the above order.
This should install a "Windows Wireless Drivers" in System Menu, where you can select the correct .inf (Windows driver).

As for which .inf file:
The following might help (try *lspci* in Terminal to find exactly which card you have)
#
Card: Minitar MN54GCB

    *
      Chipset: Broadcom Corporation BCM4306 802.11g (rev 3)
    *
      pciid: 14e4:4320 (rev 3)
    *
      Driver: Minitar [http://www.minitar.com/downloads/4.1.17.26.zip](http://www.minitar.com/downloads/4.1.17.26.zip)
    *
      Other: Mandrake 10.1 (kernel 2.6.8.1-12mdk) and ndiswrapper 0.9-1mdk (on the 10.1 DVD). All appears to work.

#
Card: Motorola WN825G (V2) FCC ID: ACQWN825GV2

    *
      pciid: 14E4:4320, lspci -vb string is “Broadcom Corporation BCM 94306 802.11g (rev. 03)” Windows
    *
      *Driver: [http://www.motorola.com/broadband/networking](http://www.motorola.com/broadband/networking)
    *
      Other: This card works with ndiswrapper 0.9+ using the drivers obtainable at Motorola.

#
Card: Motorola WN825G (V3) FCC ID: ACQWN825GV3

    *
      pciid: 14E4:4320, lspci -vb string is “Broadcom Corporation: Unknown Device 4320 (rev 3)” Windoze
    *
      Driver: ./Motorola Utility Installer/Win/bcmwl5.{inf,sys}
    *
      Other: This card works with ndiswrapper 1.1 and 1.5 using supplied drivers on CDROM, though I’m sure drivers can be downloaded from Motorola® at [http://www.motorola.com/broadband/networking](http://www.motorola.com/broadband/networking).

---

### Post by deinonychus75 on 2007-06-17
ugm6hr - Thank you.  Yes, I do have ethernet access.  I will try your suggestions.

---

