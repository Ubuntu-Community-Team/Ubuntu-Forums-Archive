---
title: "USR5411 config??"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by jevharr on 2007-01-20
I installed USRMAXG.inf with ndiswrapper, but when I run
>ndiswrapper -l
I get "invalid driver!"

Does anyone know where to get a good driver for this card?

Thanks,
James

---

### Post by teaker1s on 2007-01-20
really you need to tell us the chipset as well, terminal type
[COLOR="Red"]
lspci
lsusb
[/COLOR]

post results

---

### Post by jevharr on 2007-01-21
[FONT="Courier New"] $>lspci[/FONT]
[FONT="Courier New"]  Broadcom Corporation BCM4318 [AirForce One 54g] 802.11 Wireless LAN Controller (rev 02)[/FONT]

This is in an HP Omnibook Xe2.

I have tried a couple of different drivers including the one that came with the card, but after I install them (ndiswrapper -i <driver.inf>), ndiswrapper -l returns the invalid driver error.

I have not tried installing the driver on a Windows laptop. I guess that is the next step. Do I then only need the .inf file transfered to my Xubuntu laptop?

Thanks for any help.
James

---

### Post by teaker1s on 2007-01-21
if you installed from repositories then I would suggest you try the link in my signature. sometimes a .sys file is required-I'm only familiar with BCM4306 AND BCM4311

---

### Post by jevharr on 2007-01-21
I have followed the instructions in your link, but when I run [FONT="Courier New"]**iwconfig**[/FONT] I get output from eth1 instead of wlan0 (no listing at all for wlan0.
[FONT="Courier New"]**ndiswrapper -l**[/FONT] returns "[FONT="Courier New"]**bcmwl5   driver installed, hardware present**[/FONT]"

---

### Post by teaker1s on 2007-01-21
> **jevharr said:**
> I have followed the instructions in your link, but when I run [FONT="Courier New"]**iwconfig**[/FONT] I get output from eth1 instead of wlan0 (no listing at all for wlan0.
[FONT="Courier New"]**ndiswrapper -l**[/FONT] returns "[FONT="Courier New"]**bcmwl5   driver installed, hardware present**[/FONT]"

Great work, we now have hardware and software done.

if you haven't done so in terminal

[COLOR="Red"]sudo gedit /etc/modules[/COLOR]

Add the word ndiswrapper and save the file using "save as" this will then load everytime you boot 

Do you have a wired  internet connection on ubuntu at the moment? if so 

[COLOR="Red"]gksudo synaptic[/COLOR]

search and install
**network-manager-gnome**

now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key 

and don't worry about wireless showing up as eth1 it's a minor issue that should resolve it'self by
[COLOR="Red"]
sudo gedit /etc/iftab[/COLOR]
 . If you don't comment out the eth1 entry, ndiswrapper won't be able to alias the device as wlan0.)

to comment out put the symbol below in front of the line and save file
[COLOR="Red"]#[/COLOR]

---

### Post by jevharr on 2007-01-22
AAARRGH!!

I commented the ETH1 line out of iftab, but I am still getting the ETH0 listing instead of the WLAN0 when I run iwconfig. Also the ETH0 is not associated, so everything is "0" and "off". There are no lights on the card itself either. NDISWRAPPER -L still looks good "driver installed, hardware present".
IFDOWN WLAN0 returns "ifdown: interface wlan0 not configured".

Any more ideas for me? Thanks for the help so far. I seem to be soooo close!

James

---

### Post by teaker1s on 2007-01-22
put the /etc/iftab back as it was and make sure any wireless switches are on
[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]

any lights

---

### Post by jevharr on 2007-01-22
iftab looks like this:

[FONT="Courier New"]**eth0 mac 00:10:a4:bb:b7:ac arp 1**[/FONT]

that's the only line. Should I have a wlan0 mac address?

I uncommented the eth0 line and ran [FONT="Courier New"]**sudo modprobe ndiswrapper**[/FONT]. Same results as before.

Continued thanks,
James

---

### Post by jevharr on 2007-01-25
Alright, after many hours working on this I have it up and running!!! WOOO HOOO!! Many thanks to Teaker1. Now to try and clean up those little annoyances...

I have to run the following comands every time I reboot or switch from wired to wireless:
[FONT="Courier New"][B]sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo dhclient wlan1[/B][/FONT]
bcm43xx is an 'alternate driver', but I can't seem to remove it with 
[FONT="Courier New"]**ndiswrapper -e bcm43xx**[/FONT]

Is there a way to run these automatically on startup? Is there a more elegant way of solving this problem?

Thanks,
J--

---

### Post by teaker1s on 2007-01-25
sent you a pm, you need to follow the link in my signature 
blacklist the module and edit your modules file,  as per the howto;) ;) ;)

---

### Post by jevharr on 2007-01-26
Yep, did those things, but the behavior persists. Not a huge deal, but inconvenient especially if someone else in the house has to restart for any reason. Then I get a call at work asking why the internet won't work!! :) 

I'll keep trying stuff. These things eventually resolve.

Thanks
James

---

### Post by jevharr on 2007-02-19
So, I had my wireless card working perfectly. Then one day, I decided to shut down. When I reboot the next day, no wireless!! No lights on the card, no nothing!

iwconfig returns:
[FONT="Courier New"]lo        no wireless extensions.

sit0      no wireless extensions.[/FONT]

ndiswrapper -l returns
[FONT="Courier New"]usr11g : driver installed
        device (104C:9066) present (alternate driver: acx)[/FONT]

ndiswrapper -m returns
[FONT="Courier New"]module configuration contains directive install pci:v0000104Cd00009066sv000016ECsd0000010Dbc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 706, <MODPROBE> line 400.
module configuration contains directive install pci:v0000104Cd00009066sv000016ECsd0000010Ebc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 706, <MODPROBE> line 401.
module configuration contains directive install pci:v0000104Cd00009066sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 706, <MODPROBE> line 402.
module configuration already contains alias directive[/FONT]

I tried to figure out how to uninstall ndiswrapper so that I could re-install, but I couldn't figure out how. I installed from binaries and the ndiswrapper directory that contains teh Makefile says that there is no directive for uninstall.

HELP!!

Thanks,
J--

---

### Post by teaker1s on 2007-02-19
in terminal "cd" into directory containing source and make file
[COLOR="Red"]sudo make uninstall ndiswrapper[/COLOR]

---

