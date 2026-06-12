---
title: "wireless Dell E4310"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by anneg on 2010-09-23
The laptop came with windows 7 professional pre-installed. Wireless worked fine. 

I used wubi to install ubuntu 10.4

It rebooted once and then froze on a purple page with rotating dots.
It did that again when I tried to soft reboot from the ubuntu reboot. 

On hard power off reboot it went to the ubuntu GUI and I was able to run some commands in terminal but it does not have wireless connection -- and wire connection is not an option where I live.

the device driver on windows7 says 
broadcom 
PCIbus 2 device 0 function 0 DW 1501 wireless N WLAN half-mini card. 
driver version 5.60.48.35
there are dll and sys files listed in the driver files. 

whereas ubuntu says only
lshw -C network
network, ethernet interface etc
network unclaimed, network controller. 

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#manual](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#manual)
says to do some kind of manual install
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)

I have no idea what this would look like for my card. 
  bind "ath_pci"

---

### Post by anneg on 2010-09-23
1)system
2)administration
3)update manager. 
or some such.
On wired internet. It found packages to update. 
this proceeded, ok reboot. 

After that ubuntu no longer booted up. Made a sound and froze on a grey screen.

---

### Post by anneg on 2010-10-10
I followed the broadcom instruction to install sta drivers for linux. 

Wireless worked. 

But the next time I started Ubuntu, there was no wireless. 

I went back to the download directory in which I had made the driver. 
I ran the last two instructions
sudo modprobe lib80211
sudo insmod wl.ko

and I have wireless working again. 

I don't know anything about linux. can you
1. let me know what to do so wireless is permanent
2. or what I need to understand to know what makes a change permanent or something not in linux.

---

### Post by anewguy on 2010-10-10
Well, the 2 steps you did manually - the modprobe of lib80211 and insmod wl.ko, are only good for 1 session - power off and you lose them.  However, there is a file to which you can add these so it will be permanent across power downs, etc..  The first thing you should probably have a basic understanding of is modprobe versus insmod.  Modprobe is sort of an advance insmod, and indeed uses insmod.  This loads a kernel module - in your case the apparent files needed for your wireless to work.

So, first off understand I am not familiar with your particular adapter, so I have to take your word on it being those 2 modules.  To make these thing permanent, do the following:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo gedit /etc/modules <press enter>  You are calling up an editor so we can modify the contents of the file "modules" in the "etc" folder.  This file contains the module names we would like the kernel to load at boot.

Using the editor, go to the end of the file and add these 2 lines:

lib80211
wl.ko

Then save the file and exit the editor.

Since you'll be back to the command line in a terminal window, request a reboot:

sudo shutdown -r now <press enter>

Once your system is back up the wireless should work.

Dave ;)

---

### Post by anneg on 2010-10-10
Thank you

I sudo edited /etc/modules
and copied the wl.ko file into /lib/modules/*/kernel/net/wireless/wl.ko
so linux could find the module

lib80211 is not in the downloads/hybrid_wl directory so I assume that it is part of linux. 

The computer still boots up without wireless 
lsmod |grep wl 
comes back with nothing.

---

### Post by anneg on 2010-10-10
got it. Had to run 
depmod -a

---

