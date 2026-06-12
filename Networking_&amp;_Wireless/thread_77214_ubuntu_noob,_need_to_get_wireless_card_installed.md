---
title: "ubuntu noob, need to get wireless card installed"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by azp on 2005-10-16
I recently installed ubuntu, to get familiar with linux, I have gotten all my devices installed, except my wirless card(buffalo wli2-pci-54g) I need this to get to the internet, I tried installing the terminal, but it couldn't because it needed to get online to install, which I thought was weird. Ubuntu recognizes the card, in the "device manager,"  but that is it. All help is appreciated, I finally got the terminal working, sorry I am a big linux noob, so right now, I just need to know how to get the wireless card installed

---

### Post by azp on 2005-10-16
I just found a netgear 11mb usb drive, and it doesn't seem to be recogicnized either, I can use either if this would be easier to install to connect to the internet, I did some more research, and a site said to use the .inf in the ar directory, it said that it works with ndiswrappers 0.11 and rhel 3, if that helps

---

### Post by bionnaki on 2005-10-16
install ndiswrapper

---

### Post by knappen on 2005-10-16
Install ndiswrapper-utils

ndiswrapper-i /path to the .inf file

ndiswrapper -l to see if the driver is installed and hardware is present

ndiswrapper -m

Do not forget to modprobe ndiswrapper and add ndiswrapper to etc/modules

---

### Post by azp on 2005-10-16
I did 
nstall ndiswrapper-utils

ndiswrapper-i /path to the .inf file
t

ndiswrapper -m

Do not forget to modprobe ndiswrapper and add ndiswrapper to etc/modules
and it all worked, but nothing else happens, it doesn't show up in the administration->networking, and in the device manager, everything about it is still unkown :(

---

### Post by knappen on 2005-10-17
Can you see the card if you type lspci ?

---

### Post by azp on 2005-10-17
ok,  ndiswrapper -l it says invalid driver, but I used the driver like last week, it says nothing about the hardware.

---

### Post by azp on 2005-10-17
Ok I tried to use my usb ma111 usb network driver, and it gets recognized, I install the linux-wlan-ng and then install the .inf with ndiswrapper, and then I do modprobe, then type ndiswrapper -l and it says invalid driver for both

---

### Post by breakthestate on 2005-10-17
[quote=azp]ok, ndiswrapper -l it says invalid driver, but I used the driver like last week, it says nothing about the hardware.[/quote]

You used the driver last week..... on ubuntu or windows?

---

### Post by azp on 2005-10-18
windows

---

### Post by azp on 2005-10-18
I think my best bet is to just format, and reinstall ubuntu, can some1 give me a step by step guide? from when I boot up, to install a wireless carD?

---

### Post by Skid on 2005-10-18
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

May help, I've not read all of the forum posts but it'll at least let you know if it's supported or not

---

### Post by breakthestate on 2005-10-18
Azp,

If you are willing to learn and you haven't done too much with your new setup, it is never a bad thing to reinstall.  You will learn more each time.  Go ahead and reinstall and then post in this forum when you have done so.  I will try and help you out tomorrow to find out exactly what the chipset it that your card uses.

---

### Post by azp on 2005-10-19
Well I got on the mirc# and I got sorta some help, I reinstalled ubuntu, and tried to work with my ma111, which is suppose to work. We did everything , we even installed the header kernel and a bunch of crap.....I am giving up on ubuntu and gonna try fedora I think

---

### Post by facejeans on 2005-10-19
i have a MA111 usb adapter too, v1...and i'm having trouble with it, except i think i'm a head of where you are.  Breezy comes with ndiswrapper, i just installed it from system>administration>synaptic package manager, scrolled to it(because the search doesn't work, or i dunno how to use it) and installed it.  
this helps:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Upgrading](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Upgrading)

and this:[http://www.linuxforums.org/tutorials/1/tutorial-55961.html](http://www.linuxforums.org/tutorials/1/tutorial-55961.html)

so..after installing the version of ndiswrapper that came with ubuntu breezy, 
i unzipped the 2.0 version of the drivers, and did

sudo ndiswrapper -i /location/driver.inf

worked...and i used -l to see it, and it gave me hardware and driver present. great.

So i created the config for it with -m...but now i'm clueless.

I was reading that the next step is to start ndiswrapper by using modprobe ndiswrapper...but that gave me some wack error:

FATAL:  Error inserting ndiswrapper (long directory): operation not permitted.  

so now i don't know what to do...if anyone can help that would be awesome.
sorry, i'm a noob, but i do know somethings about linux...thus far it kinda reminds me of dos.

---

### Post by Pathogenix on 2005-10-19
[QUOTE=azp]I did 
nstall ndiswrapper-utils

ndiswrapper-i /path to the .inf file
t

ndiswrapper -m

Do not forget to modprobe ndiswrapper and add ndiswrapper to etc/modules
and it all worked, but nothing else happens, it doesn't show up in the administration->networking, and in the device manager, everything about it is still unkown :([/QUOTE]


If you get everything else to work, but don't see your device in network manager, try ifup to bring the interface up, and then iwconfig to make sure it's configured properly.

Mine didn't show until I'd manually activated the interface, but has functioned perfectly since.

---

### Post by azp on 2005-10-19
[QUOTE=facejeans]i have a MA111 usb adapter too, v1...and i'm having trouble with it, except i think i'm a head of where you are.  Breezy comes with ndiswrapper, i just installed it from system>administration>synaptic package manager, scrolled to it(because the search doesn't work, or i dunno how to use it) and installed it.  
this helps:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Upgrading](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Upgrading)

and this:[http://www.linuxforums.org/tutorials/1/tutorial-55961.html](http://www.linuxforums.org/tutorials/1/tutorial-55961.html)

so..after installing the version of ndiswrapper that came with ubuntu breezy, 
i unzipped the 2.0 version of the drivers, and did

sudo ndiswrapper -i /location/driver.inf

worked...and i used -l to see it, and it gave me hardware and driver present. great.

So i created the config for it with -m...but now i'm clueless.

I was reading that the next step is to start ndiswrapper by using modprobe ndiswrapper...but that gave me some wack error:

FATAL:  Error inserting ndiswrapper (long directory): operation not permitted.  

so now i don't know what to do...if anyone can help that would be awesome.
sorry, i'm a noob, but i do know somethings about linux...thus far it kinda reminds me of dos.[/QUOTE]
I had this problem also, that was fixed by getting the header kernal
edit: also when I reinstalled during setup a wlan connection appeared, but it could not configure it???

---

### Post by ajack on 2005-10-21
An easier way is to use the synaptic tool and install the gtkndis (sp?) which is a gtk graphical tool for ndiswrapper.  Click install and point to the appropriate .inf file.  No funny scripts or command lines for the noobs and for the lazy knowledgable types.  :)

---

