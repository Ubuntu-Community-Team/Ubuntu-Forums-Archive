---
title: "Installing Linksys WUSB11"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by sonicbs on 2006-08-30
Hi,
I am having trouble trying to install a Linksys USB wireless adapter model WUSB11. There is a wiki page about this product with a detailed installation process:
[https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11]("https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11")
Here are the main steps:
5) Log in to your Ubuntu and copy the downloaded file (most probably named "at76c503a-cvsroot.tar.gz") to your desktop.
6-12)NOT IMPRORTANT
13) Type: "sudo apt-get install build-essential linux-headers-`uname -r`"
14) Type: "sudo apt-get install cvs"
15,16,17) NOT IMPORTANT
17) Type: "cd /home/USERNAME/Desktop"
18 ) Type: "tar xzvf at76c503a-cvsroot.tar.gz"
19) Type: "mv at76c503a CVS"
20) Type: "cvs -d /home/sargonx/Desktop/CVS co at76c503a"
21) Type: "cd at76c503a"
22) Type: "make".

I have a problem following step 22. Here's the message I get:

Makefile:24: *** Kernel in /lib/modules/2.6.15-25-386/build is not configured.
Stop.

Can anyone help me with this one?

Thanks.
Sonny

---

### Post by Dcastle on 2006-08-30
What version of WUSB11 is it?

---

### Post by sonicbs on 2006-08-30
it's WUSB11 v4 (version 4)

---

### Post by sonicbs on 2006-08-31
Fixed it!
OK, to whoever's having the same problem - 
To install the Linksys WUSB11v4 I used the ndiswrapper module.
I used this excelent step-by-step wiki which can be found here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

If anybody knows if there's a way to install a native driver for this product please reply to this thread. Although, ndiswrapper seems to do the trick.

---

### Post by JawsThemeSwimming428 on 2006-09-08
I am sort of new to Ubuntu, I used Fedora for a few years. I am trying to install the WUSB11 Wireless adapter on my Ubuntu 6.06 desktop and in the first few steps it won't let me accomplish the commands. The packages are not available. what am I doing wrong?

---

### Post by AllenJM on 2006-09-16
Yeah I'm new too I got to the point of checking if the driver and hardware was present and the machine went belly up:rolleyes:  and for the sake  of being sure I'm re-installing from scratch.

The main things that I did wrong was typing in exactly the command lines and then realising that the file names were wrong#-o . Once corrected that got the packages installed and the Graphic ndisgtk is really easy to use.

The other problem I got was the driver was wrong, I couldn't get anything from *lspci* and then I realised that it was on USB and tried *lsusb* and now I know which driver to use just waiting on the install to finish :KS , really got this drive partioning of to pat now......:lol:

---

