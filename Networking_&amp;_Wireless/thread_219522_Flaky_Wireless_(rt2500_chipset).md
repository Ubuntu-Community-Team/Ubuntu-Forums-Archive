---
title: "Flaky Wireless (rt2500 chipset)"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by deadfolk on 2006-07-20
Hi all,

I'm having a weird wireless problem - if anyone has any advice, it would be greatly appreciated.

After failing miserably to get my old Broadcom-based PCI card working (tried everything), I bit the bullet and got a Linksys WMP54G (rt2500 chipset), as these 'work out of the box'.

True enough, plugged it in, configured the wireless properties and voila!  Cool, I think, wireless sorted.  Except...well...it's kind of flaky.

First off let me say that the previous card (when used in the 'other' operating system) worked a treat.  As does the wireless bridge I borrowed from my XBox.  So I don't think range/obstructions are the problem - unless this card is just rubbish.

Anyway, symptoms are:

1) Pinging the Ubuntu machine from elsewhere results in a LOT of dropped packets - sometimes up to 70-80% or so.
2) Accessing the machine from another (e.g. ssh, samba) is very, very slow.  Samba is pretty much unusable - and often the connections drop out altogether.

So, like I said, any suggestions very much appreciated.

Cheers,

DF

---

### Post by phork on 2006-07-20
The Ralink chipsets aren't known for their sensitivity, so if you're looking for a nice long range adapater, I'm afraid your out of luck.  However, I have a ralink usb stick and experienced a similar problem with the version of the drivers that Ubuntu ships with.  Excessively bad sensitivity, lots of dropped packets (especially on large transfers) etc...  

The fix -- grab the latest BETA (or CVS as I use) version of these drivers from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads), compile, install, reboot, and notice your now much imporved signal strength.  Since upgrading to the newer drivers I have had 0 problems with dropped packets without any change in placement on the router or adapter.  Hope that helps.

---

### Post by deadfolk on 2006-07-21
Cool - I'll give that a shot over the weekend.  Thanks.

---

### Post by bionnaki on 2006-07-25
> The fix -- grab the latest BETA (or CVS as I use) version of these drivers from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads), compile, install, reboot, and notice your now much imporved signal strength. Since upgrading to the newer drivers I have had 0 problems with dropped packets without any change in placement on the router or adapter. Hope that helps.

I have had the exact same problem with my wmp54g card. I have wpa setup and it works, but it drops so much.

I am interested in these latest drivers, but can you show us how to set them up? I am not very good at compiling stuff, yet. what exactly should I do?

thanks!

---

### Post by bionnaki on 2006-07-26
bump

---

### Post by bionnaki on 2006-07-26
also, would I get better performance using ndiswrapper?

---

### Post by bionnaki on 2006-07-31
bump

---

### Post by drag on 2006-08-03
Try this...
Make sure that you have universe repositories enabled and your system is completely up to date.

To make sure that you don't mess up your drivers make sure that in /lib/modules/your-kernel-version
that you move the rt2500.ko driver to a safe place.

Go like this:
cd /usr/lib/`uname -r` 
sudo mv `find |grep rt2500.ko` ~/rt2500.ko.backup


Then from a command line try this:

sudo su -
apt-get install module-assistant
m-a update
m-a prepare
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
tar xfz rt2500-cvs-daily.tar.gz
cd rt2500-(subsitute correct date/name)
cd Modules
make && make install


If all of that works out then reboot and see if your card helps out.

The key to the step is to make sure that you have the development tools and kernel headers installed. Module-assistant helps with this.

Then after you cd into the downloaded tarball the 'make' command will do the actual compiling and 'make install' should copy the new module to the correct location. You may want to double check that.

---

### Post by hans030390 on 2006-08-03
I followed instructions like that, and it installed the rt2500.ko file in /lib/modules/my kernel/extras. Is it supposed to go there? After the make and make install commands, it puts it there and does not seem to affect my system at all.

Are there any other things I'm supposed to do to the original rt2500.ko file (other than what you mentioned) before installing a new one?

In one guide, I read you just copy over the original file with the new one (if it gets put in the extras folder). Then there is some insmod command on that file, then depmod -a.

After rebooting and doing the modprobe command, it seems to connect, but now I can do nothing online. The connection also drops a lot more often now (it switches every second or two), but the signal is stronger...but I still can't do anything.

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1076&highlight=ubuntu](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1076&highlight=ubuntu)

That's the other guide I'm talking about.

Also, when using the above guide, I get some "-1 files exist" with the insmod command. Why? I believe this does not help...

So, I have multiple questions in this reply, and I hope you can help me. Thanks!

---

### Post by bionnaki on 2006-08-04
I was able to install the cvs driver by playing around with compiling a few days ago. I also installed the beta driver before the cvs, and the beta did nothing for me. And I am happy to report that my wireless is working perfectly now. I also did the following (not sure if it affected my machine, but you might want to try):

> sudo iwconfig ra0 freq 2.422

2.422 being channel 2 - what I use.

see: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

> sudo gedit /boot/grub/menu.lst

added acpi=off to the first entry making it look like:

> title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


again, not sure if these modifications did anything positive, but in doing so, my wireless is running great. be sure to reboot.

you can check to see if the drivers are loaded with the following command:

> modinfo rt2500

I get:

> filename:       /lib/modules/2.6.15-26-386/extra/rt2500.ko
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 CVS CVS
license:        GPL
vermagic:       2.6.15-26-386 preempt 486 gcc-4.0
depends:
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
srcversion:     8085ACEE4D1ED71FFA5CAA4
parm:           ifname:Network device name (default ra%d) (charp)
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)


---

### Post by bionnaki on 2006-08-05
thanks drag

I decided to update my driver to the latest cvs for the hell of it and your method worked perfectly. my connection is actually a bit stronger than it was  before. I'd like to write up a how-to on setting up wireless with your method + how to setup wpa (another method I discovered), if you dont mind. I'll give you credit. let me know if this is cool.

thanks again

---

