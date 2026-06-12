---
title: "Where can I find the ndiswrapper .debs?"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by Jedidawn on 2005-08-28
I am trying to follow this guide: [https://wiki.ubuntu.com/NdiswrapperWithoutInternetAccessSlowFirefox](https://wiki.ubuntu.com/NdiswrapperWithoutInternetAccessSlowFirefox) 
But I can't find where to download the .debs.

---

### Post by SGC on 2005-08-28
Enable the universe repository and run this command:
apt-get install ndiswrapper-source ndiswrapper-utils

Or download them from here:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fn%2Fndiswrapper%2Fndiswrapper-source_0.12%2B1.0rc2-1_i386.deb&md5sum=041ef35b1aeb5f33e8dd375385463fcb&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fn%2Fndiswrapper%2Fndiswrapper-source_0.12%2B1.0rc2-1_i386.deb&md5sum=041ef35b1aeb5f33e8dd375385463fcb&arch=i386&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils_0.12%2B1.0rc2-1_i386.deb&md5sum=6472b995467d74c38de49b8536f452f6&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils_0.12%2B1.0rc2-1_i386.deb&md5sum=6472b995467d74c38de49b8536f452f6&arch=i386&type=main)

---

### Post by Jedidawn on 2005-08-28
I cannot use apt because I recieve my internet acces through a router. The links you gave seem to be for an Intel x86 computer. I have an amd64 and am using the amd64 version of Ubuntu does this matter?

---

### Post by az on 2005-08-28
ndiswrapper-utils is on you install cd.  The modules are already in the running (stock) kernel.

---

### Post by Jedidawn on 2005-08-28
[QUOTE=azz]ndiswrapper-utils is on you install cd.  The modules are already in the running (stock) kernel.[/QUOTE]
 But not normal ndiswrapper?

---

### Post by blu.gecko on 2005-08-28
dude,

I installed ndiswrapper on my laptop before I ever learned about changing the source.list, if you go to the gui on the synatics to install applications, look up ndiswrapper or type in 

sudo apt-get install ndiswrapper
sudo ndiswrapper -l (to list the ndiswrapper)


its pretty simple, but yeah the ndiswrapper is on the ISO image of 5.0.4

check out my threads, I think I wrote a howto on that one, mabye not,
mabye it was at justlinux.com...... I did it somewhere.....Im sure I did

---

### Post by blu.gecko on 2005-08-28
eh, I found my post

sudo apt-get install ndiswrapper
sudo ndiswrapper -i /media/cdrom0/swsetup/bcmlw5.inf
sudo ndiswrapper -l
driver found, hardware present
sudo modprobe ndiswrapper
goto "administrator" goto "Network" goto "Wireless Adapter" then "Activate"

"reboot"

sudo ndiswrapper -m

"reboot"

if you dont activate the hardware it will disapear. 

[http://security.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/](http://security.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/)

pulled from my post at [http://ubuntuforums.org/showthread.php?t=24000&page=2&pp=10](http://ubuntuforums.org/showthread.php?t=24000&page=2&pp=10)
hope that helps somewhat...... 
__________________
blu.gecko <---linux newb

---

### Post by az on 2005-08-28
"But not normal ndiswrapper?"

Ah.  I see!

If you take the ndiswrapper source and compile it and then install it, you get a kernel module and a userland tool.

Ndiswrapper is packaged in binary form as two packages.  Ther kernel module and the userspace tool called "ndiswrapper-utils". The module is already there.

So, that is *normal ndiswrapper*.

---

### Post by blu.gecko on 2005-08-28
yeah its utils, that threw me offguard at 1st too

as long as you dont have any driver issues, it should be a pretty quick install

I think gtk wifi is the best manager, I havent tried an others yet.

---

### Post by Jedidawn on 2005-08-29
Is that tutorial outated then? If so how do I get my network card working?

---

### Post by az on 2005-08-29
[QUOTE=Jedidawn]Is that tutorial outated then? If so how do I get my network card working?[/QUOTE]


If your network card needs ndiswrapper, install ndiswrapper-utils from the cd.  If your network card has native linux drivers, you may need to prevent those drivers from working to use ndiswrapper.  For example, some cards work wine out-of-the-box, in Ubuntu, but cannot handle WEP, or be configured by the GUI properly.  You may chose to use ndiswrapper, in this case.

Find your windows drivers for your card and open a terminal.

Go to the directory where you put the driver

cd /Desktop
sudo ndiswrapper -i (windowsdrivername.INF)
sudo ndiswrapper -l
sudo modprobe ndiswrapper

Then, open the network GUI (In adminstration) and configure your network card (WEP, ETC...)


If your thing does not work, prevent the native driver from being loaded byputting it's name in /etc/hotplug/blacklist and rebooting.

---

### Post by Jedidawn on 2005-08-29
My card has no linux drivers. I did a search of the install cd but I couldn't find ndiswrapper.

---

### Post by az on 2005-08-29
[QUOTE=Jedidawn]My card has no linux drivers. I did a search of the install cd but I couldn't find ndiswrapper.[/QUOTE]


sudo apt-get install ndiswrapper-utils

or just use synaptic.

---

### Post by Jedidawn on 2005-08-30
When I try to install it i get the error E:package not found and when I do a search on synaptic for "ndis" then "ndiswrapper" and then "ndiswrapper-utils" and I got no results for every search

---

### Post by az on 2005-08-30
Do you have a Warty cd, or a Hoary cd?

---

### Post by Jedidawn on 2005-08-31
I have a Hoary Hedgehog 5.04 amd64 cd

---

### Post by az on 2005-08-31
[QUOTE=Jedidawn]I have a Hoary Hedgehog 5.04 amd64 cd[/QUOTE]


Oh.  Sorry.

You only mentioned that four days ago and nobody seems to have noticed.

ndiswrapper will not work on anything but 32-bit ix86 since it can only run 32-bit windows drivers.  Sorry.

---

### Post by az on 2005-08-31
What card do you have?

---

### Post by Jedidawn on 2005-08-31
I have a d-link dwl-g520+

---

### Post by Jedidawn on 2005-08-31
oh and it is 32 bit windows... my processor just can't opperate at it's full potential

---

### Post by az on 2005-08-31
[QUOTE=Jedidawn]I have a d-link dwl-g520+[/QUOTE]

Your card has linux drivers.  WEP did not work when Hoary was released, but I heard that the current version supports WEP.

[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)
[http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless](http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless)

Please ask if you have any  problems compilng this driver...

Good luck!  It should not be too bad.  This is a comon card.

Can someone confirm if this chipset supports WEP in Breezy out-of-the-box?

---

### Post by Jedidawn on 2005-09-01
I have looked at the acx100 page but I can't find out how to install it and the wiki doesn't help

---

### Post by Jedidawn on 2005-09-04
Hello?

---

