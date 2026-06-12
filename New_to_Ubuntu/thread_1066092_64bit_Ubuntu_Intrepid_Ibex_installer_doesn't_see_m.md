---
title: "64bit Ubuntu Intrepid Ibex installer doesn't see my second HDD"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Pendarth on 2009-02-10
Trying to install the 64bit Intrepid Ibex (first time - new user) from the Live CD, on my second SATA HDD (500 GB ATA Seagate ST3500320AS).  When I run the installer, only the primary HDD (1 TB ATA Samsung HD103UJ) shows up.

Opening GParted shows both HDDs.  My Partition Table data according to GParted look like below:

[quote="GParted"]

/dev/sda  931.51 GiB:

**Device Information**
** Model:**   ATA SAMSUNG HD103UJ
** Size:**    931.51 GiB
** Path:**    /dev/sda

** DiskLabelType:**  msdos
** Heads:**          255
** Sector/Track:**   63
** Cylinder:**       121601
** Total Sectors:**  1953520065

/dev/sda1    ntfs    XP_PRO SP3    409.64 GiB
/dev/sda2    extended              521.87 GiB
  /dev/sda5  ntfs    PROGRAMS      137.38 GiB
  /dev/sda6  ntfs    DATA          111.79 GiB
  /dev/sda7  ntfs    ORIGINAL_CDS  272.70 GiB

/dev/sdb  465.76 GiB

**Device Information**
** Model:**   ATA ST3500320AS
** Size:**    465.76 GiB
** Path:**    /dev/sdb

** DiskLabelType:**  msdos
** Heads:**          255
** Sector/Track:**   63
** Cylinder:**       60801
** Total Sectors:**  976768065

/dev/sdb1    ntfs    /media/GAMES    270.44 GiB
/dev/sdb2    extended                195.32 GiB
  /dev/sdb5  ext3    /media/UBUNTU_8.1 195.32 GiB
[/quote]

2.  The second problem that I'm having, while using the LiveCD, is that I'm using 2 LCD monitors with ASUS EAH4850 (ATI clone) - one Digital and the other Analog - with different resloutions.  When I try to uncheck "Mirror Screens" - it asks to log out and back in. Doing so, although I get the desktop background, I lose both the top and bottom "bars" -- thus cannot do anything.  Not quite familiar with using the commmand line interface, yet.

Thanks in advance for your time and effort to help me with these problems.

BTW. Would it be better to go with the 32 bit version ?

---

### Post by Drate on 2009-02-10
For the first problem, it is the SATA that is not recognized right?  I'll tell you what I did to correct for this and you can see which bits apply to you.

First I adjusted my bios settings for the SATA hard drive to use AHCI mode.  Then I started Ubuntu LiveCD, and at the first screen (the boot screen), I hit (F4) for more options (it might have been (F6), but I am thinking 4), and typed in "pci=nomsi" and hit enter.  My Not seeing Sata was cured at that point.

I will say though, on MY machine I had trouble having both the SATA and the IDE drives in at the same time (only a problem after install during bootup).  Probably won't be a problem for you, just thought I'd mention it just in case.

---

### Post by Pendarth on 2009-02-10
> **Drate said:**
> For the first problem, it is the SATA that is not recognized right?  I'll tell you what I did to correct for this and you can see which bits apply to you.

First I adjusted my bios settings for the SATA hard drive to use AHCI mode.  Then I started Ubuntu LiveCD, and at the first screen (the boot screen), I hit (F4) for more options (it might have been (F6), but I am thinking 4), and typed in "pci=nomsi" and hit enter.  My Not seeing Sata was cured at that point.

I will say though, on MY machine I had trouble having both the SATA and the IDE drives in at the same time (only a problem after install during bootup).  Probably won't be a problem for you, just thought I'd mention it just in case.

I am afraid of enabling AHCI -- that will mess up my windows install.  I will have to reinstall (so I've been told) Windows and ALL programs.  I can save my data, but, it's going to be one hell of a headache :(

I'm am not a complete computer idiot, but, close to it -- so, just repeating what I've read.

---

### Post by Pendarth on 2009-02-10
Also, since GParted can see the second HDD, how come the installer can't ??

---

### Post by Pendarth on 2009-02-11
It **seems** that the reason the Installer couldn't see the other SATA drive - was to do with the way Windows works, I'm no expert here.

But, when I chose to "SHUTDOWN" windows and boot with the Installer disk - it could see both disks and gave me the option of installing in either.  Instead of "Rebooting" (as mentioned in the Installer Disk, when it's inserted while windows is running) it should say "Shutdown & Reboot" to make it a bit more "idiot-proof."

Anyway - just thought I'd mention it.

AND I think I'm not quite ready for the "real" Ubuntu experience, yet.  Going to hang around here and learn a bit more before installing it as an OS in it's own right -- going for the Wubi Install ;)

---

### Post by sturdy on 2009-02-11
Hi Pendarth,

I'm a newby here and still trying to wean myself from Windows but maybe I can offer a little insight. I have the P5Q-E mobo and had similar problems with earlier Linux distros for several weeks. With some bios tweaking I could get the chipset to recognize either IDE or SATA drives but not both at the same time. Of course Win XP ran okay in dual boot when bios was set for IDE. When I changed to AHCI, Windows failed to boot.

When I installed 64 bit Intrepid Ibex and the latest bios update (14-something), both XP and ubuntu were happy with the bios set for IDE. I have two IDE and two SATA HD installed with no more issues. It doesn't seem worth reinstalling Windows to get AHCI compatibility so I have left the bios in IDE mode. Ubuntu now seems happy with IDE, too.

So what little help I can offer is to install the latest bios update from ASUS and maybe your problem will clear itself. I am now using 17-something and still okay.  HTH

Sturdy

---

### Post by Pendarth on 2009-02-11
Thanks for the reply :)

Since my post, I have come to realize that I will for the near future be heavily dependent on support - either from here or the internet ... to solve many of the up and coming problems.

Thus I have (as I said) installed Intrepid Ibex within WindowsXP (Wubi Install) - and so far, except for a few glitches things seem to working out.  Once, I am more comfortable with -ls / grep and all the "greek" names, I might consider ditching windows.

The only remaining problem (or one that has developed :D) is that I've lost my second monitor.  I installed the Manufacturer's ATI 4850 Upgrade (not supported by the community) which gave me my native 1650x1050 resolution on my main screen ... but, lost my 15" (1024x768) monitor.  Will make a separate post about that.

---

