---
title: "[SOLVED] Wireless not working on Compaq cq50"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by scorziello on 2008-11-18
I have tried everything I have seen on the forums to get the wireless working. I have just installed 8.10 but nothing can seem to get the wireless working. I have a Compaq cq 50-215nr. It automatically selects to use the atheros driver. Any help would be appreciated.

Edit:
  So to update the status here. I can get the wireless working, but I have to disable the restricted driver, reboot and then enable the driver again, and then the wireless works. I just can't get the wireless to work without doing those steps. I have tried adding "ath_pci" and "ath_hal" to "/etc/modules" and that doesn't work either. Any help would be great. Thanks in advance.

---

### Post by scorziello on 2008-11-19
So I finally figured this out on my own after poking around the forums for a few days and trying different things. I am running this wifi card btw; Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01). 
What I finally figured out is that ath5k was not getting loaded at startup. So the first thing I did was add ath5k to list in my modules file.
```
sudo gedit /etc/modules
```
After doing that I added both hal_pci and ath_pci to my blacklist file.
```
sudo gedit /etc/modprobe.d/blacklist
```
I just added them to the bottom as seen below:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

#causing ath5k not to load because of conflicts
blacklist ath_hal
blacklist ath_pci


I haven't had the time to figure out which of the two modules is causing conflict with ath5k but now when I boot up the wireless card automatically detects networks. Hope this helps some one.

---

### Post by jlburky on 2008-12-21
Thank you so much! I already spent about 4 hours on this. Everything seems to be working fine now since adding the deviced to the blacklist.

---

### Post by scorziello on 2008-12-21
No problem that is why we are called a community. Let me know if you need anything else. I will try to help you if I can.

---

### Post by wisstnb on 2008-12-24
Does not work for me. Followed the same steps, but nothing seems to work. I have the same laptop (Compaq c50)

---

### Post by luks911 on 2008-12-24
> **wisstnb said:**
> Does not work for me. Followed the same steps, but nothing seems to work. I have the same laptop (Compaq c50)

Do you have the ath5k module? What do you get if you do 
```
sudo modprobe ath5k
```
If you don't have the module, install linux-backports:
```
sudo aptitude install linux-backports-modules-intrepid
```

---

### Post by wisstnb on 2008-12-24
When I do "sudo modprobe ath5k" I get "FATAL: Module ath5k not found". I'm new to Linux, so please, bear with me!

I've been trying to find a solution for this for days now. Nothing seems to work.

---

### Post by luks911 on 2008-12-24
That's because you have to instal linux-backports:
```
sudo aptitude install linux-backports-modules-intrepid
```
Then, yes
```
sudo modprobe ath5k
```
and then, to load the module at startup
```
echo "ath5k" | sudo tee -a /etc/modules
```

Maybe you have to reboot before it takes effect.

---

### Post by wisstnb on 2008-12-24
I've just done the steps above. I rebooted, then did "sudo modprobe ath5k", but it still says "FATAL: Module ath5k not found".

By the way, when I type "sudo aptitude install linux-backports-modules-intrepid", I see "couldn't find any package whose name or description matched "linux-backports-modules-intrepid".

---

### Post by luks911 on 2008-12-25
Hmmm... the ath5k module is installed with the linux-backports-modules-intrepid package, that's the first problem. Now, ¿are you using Intrepid or another version? Because in Intrepid you should be able to install the package and you shouldn't receive the message about ubuntu can't find it. Of course, you have to be conected to the internet for the instalation.

Another posibility, for Intrepid or another Ubuntu version, is to use madwifi driver instead ath5k. You have to follow the instructions below, one line each time in a terminal, also with an internet conection.
```

echo "blacklist ath_hal" | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake linux-headers-$(uname -r)
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz
tar xzf madwifi-hal-0.10.5.6-r3879-20081204.tar.gz
cd madwifi-hal-0.10.5.6-r3879-20081204.tar.gz
make
sudo make install
sudo modprobe -a ath_pci wlan_scan_sta
sudo ifconfig ath0 up
echo "ath_pci" | sudo tee -a /etc/modules

```

---

### Post by wisstnb on 2008-12-25
Yes, I'm using intrepid (Ubuntu 8.10). I connected the laptop using a wire and followed exactly what you told me to do. When I type "sudo modprobe ath5k" I get the error. However, when I type "sudo modprobe ath9k" there is no error. I applied this HOW-TO to ath9k to see if it works (added it to startup modules) but wireless is still disabled. No wireless connection are detected and the wireless light is red (should be blue when working properly) I know it can work without the light being blue.

---

### Post by luks911 on 2008-12-25
The light is not going to turn on, not with the ath5k module. But it's strange the error mesagge you get when you try to load the module. Because, if I'm not wrong, ath5k and ath9k are part of the linux-backports-modules.
You could try one more time looking for the package in Synaptic. If you find it, install the one that match with your kenerl version (to see your kernel version type uname -a in a terminal).
Or you can download it from Ubuntu Packages[0] and install the .deb archive.
Also, you can try installing madwifi with the instructions in the post above.

[0] [http://packages.ubuntu.com/intrepid-updates/linux-backports-modules-2.6.27-9-generic](http://packages.ubuntu.com/intrepid-updates/linux-backports-modules-2.6.27-9-generic)

---

### Post by wisstnb on 2008-12-26
Hi,

Thank you so much for your help. It's finally working using these instructions: 
[B]
echo "blacklist ath_hal" | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake linux-headers-$(uname -r)
wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz)
tar xzf madwifi-hal-0.10.5.6-r3879-20081204.tar.gz
cd madwifi-hal-0.10.5.6-r3879-20081204.tar.gz
make
sudo make install
sudo modprobe -a ath_pci wlan_scan_sta
sudo ifconfig ath0 up
echo "ath_pci" | sudo tee -a /etc/modules[/B]

(I got some errors at the end while executing the last but one code) but wireless is working after reboot.


Thanks a lot, we now can say it's SOLVED.

---

### Post by luks911 on 2008-12-26
Excellent. You get an error because that code (sudo ifconfig ath0 up) sometimes is unnecesary. It's for activate the wifi device and I'm sure that the network-manager activated it when could recognize it.

PS1: sorry if my English it is not good enough, I'm trying to improve it. :lolflag:
PS2: One more thing: remember that you have to repeat the driver installation (steps 5 to 8 ) after every kernel update, because you compiled it for your actual kernel. Anyway, it's simple.

---

### Post by wisstnb on 2008-12-26
Don't worry about your English: it's excellent.

I'll keep this thread in safe place, in case it's needed again after an update.

Thanks!

---

### Post by etobian on 2008-12-27
> **wisstnb said:**
> Hi,

sudo ifconfig ath0 up

It worked after rebooting once.  The second time, ath0 doesn't exist, and sudo ifconfig ath0 up returns "No such device."

---

### Post by luks911 on 2008-12-27
> **etobian said:**
> It worked after rebooting once.  The second time, ath0 doesn't exist, and sudo ifconfig ath0 up returns "No such device."

Open a terminal and try with```

sudo modprobe ath_pci
```

---

### Post by marianomocoroa on 2009-01-25
> **wisstnb said:**
> When I do "sudo modprobe ath5k" I get "FATAL: Module ath5k not found". I'm new to Linux, so please, bear with me!

I've been trying to find a solution for this for days now. Nothing seems to work.

I get the same message,I solve it with:

sudo apt-get install linux-backports-modules-$(uname -r)

(on a laptop compaq presario cq50-111la)

---

### Post by Lego Dragon Rider on 2009-01-31
[B][COLOR=Red]EDIT[/COLOR]: Followed [bmartin's Atheros Wireless How-To]("http://ubuntuforums.org/showthread.php?t=792158&highlight=cq50+atheros+wifi") and found that the problem was my BIOS settings. By default, the lan card was not booting up with the rest of the machine. So I changed the bios to enable "Wireless Boot" ( or whatever ) and it works great! :)
[/B]
Since I am running Hardy, I installed "linux-backports-modules-hardy" and added "blacklist ath_pci" and "blacklist ath_hal" to "/etc/modprobe.d/blacklist". 

The wireless driver will start up when I log in ( hooray! ), but it doesn't see any networks. 

So I tried to manually connect to my network, and something works because the network icon on the panel changes to a set of white bars. The bars should all be blue ( the laptop is only a few feet away from the wireless router ), but at least they are there. So far, so good. I click on "Connection information" and I get 0.0.0.0 everywhere. Something's not working right. Anything I can do about it?

Thanks!

---

### Post by iamkrazee on 2009-01-31
I have a really very dumb question here.

I installed backports packages of the latest kernel using an extra LAN wire that I had, I figured the modprobe ath5k, added it to /etc/modules etc. Works fine for me. 

The problem is, when I went to this friend's place to do the same, I realised I can't follow the same procedure(no lan wire). Now according to what I read somewhere, the backports package for 2.6.27-7 is available on the installation disk. And I can't find it on the disk. Can someone help please?

And @Mods: If you think this question is too dumb or irrelevant, please move/remove it.

---

### Post by luks911 on 2009-01-31
> **iamkrazee said:**
> I have a really very dumb question here.

I installed backports packages of the latest kernel using an extra LAN wire that I had, I figured the modprobe ath5k, added it to /etc/modules etc. Works fine for me. 

The problem is, when I went to this friend's place to do the same, I realised I can't follow the same procedure(no lan wire). Now according to what I read somewhere, the backports package for 2.6.27-7 is available on the installation disk. And I can't find it on the disk. Can someone help please?

And @Mods: If you think this question is too dumb or irrelevant, please move/remove it.

Maybe this[0] helps you. Also, you can download the deb package from Ubuntu Packages[1] in a PC with Internet connection and bring it to your friend's PC using a CD or a pendrive, then you will be able to install it with a double click.

[0] [https://help.ubuntu.com/7.10/add-applications/C/offline.html](https://help.ubuntu.com/7.10/add-applications/C/offline.html)
[1] [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by iamkrazee on 2009-01-31
Yeah, that doesn't work CD as a repository. Some strange problem. I was getting some read errors before in the boot up of the liveCD, so maybe it's my disk. 

And yeah, that second solution was the simplest one. I donno why I never thought of that.

Yet, I am still curious as to how to find that specific package. I mean, there has to be a ".deb" right? Somewhere?

---

### Post by luks911 on 2009-01-31
Here[0] you have the package you need. You have to click on i386 or amd64 , (of course, it depends of the ubuntu version you are using) and then you will have a list of mirror where you can download the deb package.

[0] [http://packages.ubuntu.com/intrepid/linux-backports-modules-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-2.6.27-7-generic)

---

