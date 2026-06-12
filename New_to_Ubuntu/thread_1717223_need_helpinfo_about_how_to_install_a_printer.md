---
title: "need help/info about how to install a printer"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by s1baker on 2011-03-29
Hi,
I need some help in how to install a printer.
First, my system is Ubuntu 10.10, 32 bit version.

I have purchased a Brother printer MFC-J265W and I am about to install it on Ubuntu. It is a multi-function printer, that has printer/scanner/fax capabilities.

I sent an email to Brother, and they assured me that their drivers on their website for both the LPR driver and Cuspwrapper and the scanner driver will work with Ubuntu 10.10 ( I don't care about any fax drivers, as the printer will allow me to fax stand alone )
 
I downloaded these drivers from the Brother website with their instructions:

 LPR driver  ->    mfcj265wipr~1.1.1-1.i386.deb
 Cuspwrapper ->    mfcj265wcuspwrapper~1.1.1-i386.deb
 Scanner     ->    brscan3-0.2.11-4.i386.deb
 Scan-Key-Tool ->  brscan-skey-0.2.1-3.i386.deb


1) Can anyone give me the order I should install these?
I think I read that the LPR driver should be installed first,
then the Cuspwrapper.

2) I guess the Scanner is the driver to make the scanner work,    but what is the "Scan-Key-Tool"?\

3) can anyone offer any other tips or caveats I should be aware of before I start?

---

### Post by wilee-nilee on 2011-03-29
Try the OS systems drivers first menu-system-admin.

---

### Post by walt.smith1960 on 2011-03-29
Also don't forget to look at the "do this before you install" on the driver download page. I don't recall the exact phraseology.  There are two or three (or four) commands that need to be run in terminal. Directions for .deb & .rpm are mixed together, I printed them all out then cross out what didn't apply.  The install directions seem to be stuck at around 8.10 so I don't know if all the commands are necessary but they don't seem to cause a problem.  Don't forget to install csh or tcsh for scanning, recent versions of Ubuntu don't include that by default and the scanner won't work without it.  Also, if you're running 64 bit, you'll need to do a command line install-gdebi etc. won't work on 64 bit systems.

I haven't tried the OS system drivers-that would be the simplest if it works. I always downloaded the software from Brother's web site. I did find that enabling Brother CUPS drivers in synaptic and using that driver on a Brother MFC-7820N was much faster than the drivers on the Brother web site.

---

### Post by s1baker on 2011-03-29
I also downloaded the "do this before you install" from the Brother web site, so I will check those out before I install.

What do I type in the terminal to determine if I have csh or tcsh on my system? Also, I have 32 bit Ubuntu 10.10 so I don't guess I will need the command line install 'install-gdebi'.

 If I try the OS system drivers first from synaptic, do I look for specifically a driver for MFC-J265W, or is there like a package of a bunch of Brother drivers that I need to download? Is there like a package for the LPR driver, a package of them for the cuspwrapper, and another package for the scanner and the scan-key-tool?

---

### Post by walt.smith1960 on 2011-03-30
> **s1baker said:**
> I also downloaded the "do this before you install" from the Brother web site, so I will check those out before I install.

What do I type in the terminal to determine if I have csh or tcsh on my system? Also, I have 32 bit Ubuntu 10.10 so I don't guess I will need the command line install 'install-gdebi'.

 If I try the OS system drivers first from synaptic, do I look for specifically a driver for MFC-J265W, or is there like a package of a bunch of Brother drivers that I need to download? Is there like a package for the LPR driver, a package of them for the cuspwrapper, and another package for the scanner and the scan-key-tool?

CSH or TCSH can be checked/installed from synaptic.  I haven't used the Brother software from the repositories except the CUPS for Brother so I'm not much help there. The only terminal commands I recall running for a 32 bit install are:
**sudo aa-complain cupsd**[B]
sudo mkdir /usr/share/cups/model[/B]
**         mkdir /var/spool/lpd **if it doesn't already exist
then after installing run:
**brsaneconfig(2-3-4 as appropriate)  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx**
remember when entering the model name to use capital letters & hyphens just like Brother or the model name will not be recognized.  I hope this is painless for you and you're as happy with your machine as I am.

---

