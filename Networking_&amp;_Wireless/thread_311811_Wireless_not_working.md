---
title: "Wireless not working"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Ultimadark on 2006-12-03
Hello

I installed Ubuntu 6.06.1 today, and this is the first time I've installed Linux (I installed it in safe graphics mode if that matters). I'm having trouble connecting to my wireless network, it has 128-bit WEP encryption. Here are some screens from my network settings.

Does anyone know why its not working? I have the correect password and everything :P



[[img]http://img159.imageshack.us/img159/6089/screenshotbf0.th.png[/IMG]](http://img159.imageshack.us/my.php?image=screenshotbf0.png)
[[img]http://img45.imageshack.us/img45/51/screenshot1zn1.th.png[/IMG]](http://img45.imageshack.us/my.php?image=screenshot1zn1.png)
[[img]http://img239.imageshack.us/img239/6549/screenshot2sq7.th.png[/IMG]](http://img239.imageshack.us/my.php?image=screenshot2sq7.png)
[[img]http://img162.imageshack.us/img162/2196/screenshot3pu4.th.png[/IMG]](http://img162.imageshack.us/my.php?image=screenshot3pu4.png)

---

### Post by hippy4life on 2006-12-03
what kind of card is it?

wireless problems are well documented in ubuntu, but solutions are often card/chipset specific.

---

### Post by Ultimadark on 2006-12-03
> **hippy4life said:**
> what kind of card is it?

wireless problems are well documented in ubuntu, but solutions are often card/chipset specific.
I dont know exactly, because I took it from a OEM PC :p In the windows "hardware manager" it says "CREATIX 802.11g Adapter" and it has a configuration utility in windows called "Intersil Prism" or something.

---

### Post by hippy4life on 2006-12-03
sounds like the prism chipset then, i'd search the forums and wiki for help with those cards.

try looking at the output of lshw to find out exactly what the card is

it'll be in there somewhere.

---

### Post by Ultimadark on 2006-12-03
I just went into Linux to write iwconfig, this is what it says:

> 
eth2
          IEEE 802.11b  ESSID:"Simon Acc"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



---

### Post by Ultimadark on 2006-12-03
When I type lshw it says this about my wireless network card

          *-network
                description: Wireless interface
                product: ISL3886 [Prism Javelin/Prism Xbow]
                vendor: Intersil Corporation
                physical id: 6
                bus info: pci@03:06.0
                logical name: eth2
                version: 01
                serial: 00:07:ca:04:e1:06
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=islsm_pci ip=192.168.0.236 multicast=yes wireless=IEEE 802.11b
                resources: iomemory:fdefc000-fdefdfff irq:50


Btw it said something about "Warning:You should be a superuser to do this." I thought I was a superuser I have only created one account in Ubuntu.

---

### Post by hippy4life on 2006-12-03
If you want to 'do' something as the super user or 'root' in a command line you must proceed the command with the sudo command, its just a matter of safety and security. eg sudo gedit, followed by your password would open gedit as root or superuser.

Like i said im not that familiar with this card or chipset but im sure with this information you can track down people who are.

i did a search for ISL3886 in this forum and it chucked up a whole load of stuff so have a poke through that and see if you can find the answer you seek.

Good luck!

---

### Post by DavidJE13 on 2006-12-04
(Re: my thread on this [http://ubuntuforums.org/showthread.php?p=1843988#post1843988](http://ubuntuforums.org/showthread.php?p=1843988#post1843988))

I'm not exactly sure what solved it for me, I think it was a combination of things, so I'll tell you what I remember doing.

btw, I was trying to get 2 cards working - one which worked through a USB (this one was working relatively soon) and one which was built in to the computer. As far as I remember, it was the USB that was a CREATIX, but I'm not sure.

Please note that I am not on Ubuntu right now, so cannot check this. Anyone who knows better should correct me.

First, you need to get ndiswrapper. This is on your live CD; Insert the CD and go to the package manager. Click Advanced, and when the new window opens, you need to change the repositories used (I forget where this is - look through the menus) to enable the CD sources (tick both of them). Once you've done this, refresh the list (button on the toolbar) and find ndiswrapper. Mark it for installation and apply changes.

This page may be useful to you: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Ok, that's ndiswrapper installed (hopefully) now you need the windows drivers for the device. I can't remember where I found them (sorry) but it shouldn't take too long with a Google search. (it should be a zip with 3 files in - save it to your USB and put it in a folder in your Ubuntu file system (you can't install them from a removable device))

Install them with:
> sudo ndiswrapper -i /[path_to_files]/[filename].inf

(You can check everything is ok with ndiswrapper -l)



The magic steps (as mentioned in my last post of the other thread) seemed to be:


You must add the following line to the end of /etc/modules to ensure the ndiswrapper is also loaded at boot time

sudo gedit /etc/modules

[add this line to the end of the file & save:]
ndiswrapper

then:

sudo gedit /etc/modprobe.d/blacklist

[...add to the bottom of the listing....]
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb



then hope for the best and reboot. I did a lot of other things in between, and any one of them might be important, but those are the ones which seem most important and hopefully that's the solution in a nutshell.

---

