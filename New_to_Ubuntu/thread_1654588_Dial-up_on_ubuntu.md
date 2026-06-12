---
title: "Dial-up on ubuntu?"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by trpted on 2010-12-28
#1 While I have broadband now, I was looking around and found something interesting.

[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

#2 I ran that tool and this is the output.

  ```
 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.32-26-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu ,  ALSA_version=1.0.21
Linux version 2.6.32-26-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010
 scanModem update of:  2010_12_12

Distrib_ID=Ubuntu
DistribCodeName=lucid
AptRepositoryStem=http://us.archive.ubuntu.com/ubuntu/

Presently install your Linux Distributions dkms package. It provides for automated driver updates,
following upgrade of your kernel.  For details see [http://linux.dell.com/projects.shtml#dkms](http://linux.dell.com/projects.shtml#dkms)

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
                  

Attached USB devices are:
 ID 04cc:1122 Philips Semiconductors Hub
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)
A sample report is:  [http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html](http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

Candidate PCI devices with modem chips are:
01:0e.0 Communication controller: Agere Systems LT WinModem
High Definition Audio cards can host modem chips.

For candidate card in slot 01:0e.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:0e.0	11c1:044e	1235:044e	Communication controller: Agere Systems LT WinModem

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 01:0e.0 ----
[    0.066236] pci 0000:01:0e.0: reg 10 32bit mmio: [0xf4101400-0xf41014ff]
[    0.066253] pci 0000:01:0e.0: reg 14 io port: [0x3800-0x3807]
[    0.066269] pci 0000:01:0e.0: reg 18 io port: [0x3400-0x34ff]
[    0.066331] pci 0000:01:0e.0: supports D2
[    0.066340] pci 0000:01:0e.0: PME# supported from D2 D3hot
[    0.066351] pci 0000:01:0e.0: PME# disabled
[   46.130112] pci 0000:00:01.0: sharing IRQ 10 with 0000:01:0e.0

 The PCI slot 01:0e.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 01:0e.0:
	Modem chipset  detected on
NAME="Communication controller: Agere Systems LT WinModem"
CLASS=0780
PCIDEV=11c1:044e
SUBSYS=1235:044e
IRQ=10
IDENT=Agere.DSP

 For candidate modem in:  01:0e.0
   0780 Communication controller: Agere Systems LT WinModem
      Primary device ID:  11c1:044e
 Support type needed or chipset:	Agere.DSP
 

 The modem has a Lucent/Agere/LSI Mars or Apollo DSP (digital signal processing) chipset. 
Support packages for 2.6.n kernels are at:
 [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/) 
 [http://packages.debian.org/sid/martian-modem-source/](http://packages.debian.org/sid/martian-modem-source/)
Always use the most update for kernels after 2.6.20, currently martian-full-20080625.tar.gz
For kernels 2.6.20 and less, usr martian-full-20080407.tar.gz.

 See DOCs/AgereDSP.txt for Details.

 At [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/) get the martian-full-20080625.tar.gz and follow Readme-NOW.html
 0x044e -- Mars 3 Mercury data fax only
-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.4.3
             and the compiler used in kernel assembly: 4.4.3

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.4
   linuc_headers base folder /lib/modules/2.6.32-26-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.

If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

For guidance on FAX usage, get from [http://linmodems.technion.ac.il/packages/](http://linmodems.technion.ac.il/packages/)  get faxing.tar.gz
It has samples for a modem using port /dev/ttySL0, which must be changed to match your modem's port.

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```


So..

Please tell: What do you recommend if I wanted to use Dial-up on ubuntu?

Thanks

---

### Post by davidmohammed on 2010-12-28
suggest have a read of [this]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html") and [this]("https://help.ubuntu.com/community/DialupModemHowto").

---

### Post by lkraemer on 2010-12-28
By you running the Script from [www.linmodems.org](www.linmodems.org), I must
assume you are talking Modem Hardware for Dialup support with Ubuntu.

Marvin and the fine folks at linmodems.org will assist you in trying to
get your WinModem working with Ubuntu.  If you join the group, and send
your email request in "PLAIN TEXT", your emails will be answered.
Just don't forget to switch your email to PLAIN TEXT.

But, I'd recommend you get an External Serial Hardware USR Modem from
[www.ebay.com](www.ebay.com) and use it for your dialup.  There are postings
on this forum that suggest the USB US Robotics Modem works fine too.

As far as software goes I'd recommend starting with wvdial, as it will try
to locate the modem, and set it up for you.  You still need to insert the
Phone Number, LoginName, & Password in the configuration file.
wvdial has dependencies that have to also be downloaded if you are trying
to install without an Ethernet or Wifi connection.  Once wvdial is working,
you can download and install Gnome-PPP. 

Your Dialup ISP should be one that readily works with Linux, and a quick
search of the forum should locate those.  I use Copper.net because they
have access numbers nation wide, and several for my area.

If you are looking for a guide here is a starting point:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)
Posting #4.

Also:
[http://ubuntuforums.org/showthread.php?p=10197883#post10197883](http://ubuntuforums.org/showthread.php?p=10197883#post10197883)
Posting #3.

[http://ubuntuforums.org/showthread.php?t=1589966](http://ubuntuforums.org/showthread.php?t=1589966)
Posting #4.

Along with the previous URL's.

lk

---

### Post by peyre on 2011-03-11
trpted, you saw the reference in the output saying yours is an Agere winmodem, and referring you to martian?  Martian is a part of the linmodem program, but it's specifically geared to getting Agere winmodems working.  I just finished getting mine going yesterday.  I'm not sure exactly what I did, but I wrote down what I could remember:

(This was in Lubuntu 10.04.)

I installed **KPPP**, **martian-modem**, and **martian-modem-source**. 
I also installed **gnome-ppp**, but it was useless: it kept hanging when I tried to detect the modem.  I eventually removed it altogether.

I ran **sudo martian_modem**, which I think started martian running.
At one point I ran **sudo m-a a-i martian-modem** (which built martian) and **sudo m-a -f get martian-modem**.  At some point in here, something told me what device the modem was assigned to: **/dev/ttySM0**.  (Apparently, ttyS**_M_**x is how martian assigns ports.)

At another point I ran **sudo apt-get update** and **sudo apt-get -s install linux-kernel-devel**.  At yet another point I ran **sudo apt-get install module-assistant**.

At the end, I installed hwinfo, which I think installs the Hardware Drivers utility (installed on Ubuntu and Xubuntu by default) that controls third-party and proprietary drivers.  When I ran that utility, I saw my modem in there and active, as the Agere 164x dsp driver.

KPPP doesn't have an option for /dev/ttySM0, so I linked it to /dev/modem:
  sudo ln -s /dev/ttySM0 /dev/modem

I was now able to select /dev/modem and get KPPP to recognize it.  Woohoo!

---------------------------

After that initial success, I was never able to get the modem working, so I brought did some more messing with it.  In the end, I found that in order to use the modem, I needed a script on the Desktop which reads as follows:
```

gksudo martian_modem
gksudo ln -s /dev/ttySM0 /dev/modem
/usr/bin/kppp
```

The last line, of course, brings up KPPP--both to save me a step and to keep me from opening KPPP prematurely.  If I want to dial out, I just double-click on the icon, and it gets the modem ready and opens the dial utility for me to use--slick.

---

