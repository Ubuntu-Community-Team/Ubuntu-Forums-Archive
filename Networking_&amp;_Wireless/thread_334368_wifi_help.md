---
title: "wifi help"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by shadylookin on 2007-01-08
for some reason ubuntu is not recognizing my wireless internet. I tried to install ndiswrapper 1.34 but it returned an error when i was trying to install it. i then tried to install ndiswrapper 1.18 i believe from the built in package manager which downloaded and installed without incident. but my wireless connection still is not working.

My wireless connection has no encryption or password so that shouldn't be an issue

i'm running ubuntu edgy

BCM4318 [AirForce One 54g] 802.11g from Broadcom Corporation is my network card

any advice?

---

### Post by teaker1s on 2007-01-08
terminal

[COLOR="Red"]sudo modprobe ndiswrapper
sudo ndiswrapper -l[/COLOR]

post results

---

### Post by shadylookin on 2007-01-08
$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

sudo ndiswrapper -l
No drivers installed

---

### Post by teaker1s on 2007-01-08
looks like a bug it's discussed in the link below should help
[http://www.linuxquestions.org/questions/showthread.php?t=498542]("http://www.linuxquestions.org/questions/showthread.php?t=498542")

---

### Post by shadylookin on 2007-01-08
well i managed to get a further with ndiswrapper. i started with make when i was supposed to start with make uninstall](*,) 

now it just says i need to find the proper windows drivers for it. does anyone know where i can get the proper windows drivers to make ndiswrapper work on an acer aspire 5100-3583? the wiki link provided in the readme doesn't have my model listed.

---

### Post by chili555 on 2007-01-08
Did you get a restore CD with your lappy? Does it have the drivers on it? You are looking for a .sys file that goes with your wireless card. You can identify your wireless card with sudo lspci -vv. Skip all the stuff that doesn't seem to pertain to wireless. In my case, I get:

03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
        Subsystem: Netgear WG511 Wireless Adapter

So I Google up "Netgear WG511" and find the Windows .exe which I cabextract until I get a warning that I have an InstallShield file, which I expand with unshield. Eventually, I drill down to the .sys file and install it with ndisgtk.

sudo apt-get install ndisgtk cabextract unshield.

Also this forum is thick with ndiswrapper instructions. 

Have fun and let us know if we can help.

---

### Post by shadylookin on 2007-01-08
how do i cabextract it until i get a shield file? then how do i unshield it?

---

### Post by shadylookin on 2007-01-08
nevermind i got it working now. thanks for the help guys i really appreciate it

---

### Post by teaker1s on 2007-01-09
:mrgreen:  another great result

---

