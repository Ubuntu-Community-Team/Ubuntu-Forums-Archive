---
title: "Lets Try This From A Different Angle"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Cyberbayne on 2007-01-25
OK, I give up. 

After having tried for several days through how-to's, basic Linux tutorials, man pages, forum threads, guides, 2 different wireless adaptors (one pci, one usb), two versions of Ubuntu (Dapper & Edgy, both Live CD installs), native drivers, ndis wrappers, gedits, countless re-boots and repeated fresh OS installs, I surrender. I've tried installing the adaptors before I installed Ubuntu, and after I installed it. Everything worked everytime, except the wireless interface. 

So now I just have one question....
Can anyone tell me the name of a pci or USB wireless adaptor that will work out of the box with either Dapper or Edgy? 

By work out of the box, I mean all I have to do is open the connections gui, click activate, and fire up my browser.

**For the curious, the adaptors are the Belkin F5D6001, and the Linksys WUSB11 V2.5. The router is the BEFW11S4 (1). I'm successfully running a 4 box LAN in my home (3 PCs and 1 laptop). Its on one of those PCs that I have installed Ubuntu (on its own HDD), and the dual boot option works fine.**

---

### Post by aysiu on 2007-01-25
Considering network browsing won't be installed by default in Ubuntu until April, I would say no card will do that. With any card, no matter how good the compatibility, you will have to at least install *network-manager* to get that kind of easy GUI connectivity.

That said, once *network-manager* is installed, there are a plethora of cards that will work without any extra configuration. On the advice of some more experienced (with wireless) forum members, I purchased an Intel Pro Wireless 2200 for my old Dell, and it worked fine without any extra configuration (apart from installing *network-manager*).

---

### Post by Cyberbayne on 2007-01-25
When I selected network-manager-gnome for installation I got a message telling me it was not compatible (or something to that effect). Can you direct me to where I can download the package or bin file that is compatible?

---

### Post by aysiu on 2007-01-25
[This post](http://ubuntuforums.org/showpost.php?p=2064419&postcount=5) may help.

---

### Post by Cyberbayne on 2007-01-26
OK, this is new, so I don't want to mess it up. 

I'm going to start with a fresh install. First question, will this work with either adaptor? 

If so, the USB is my choice. Should the adaptor be plugged in when I install the OS? Or should I wait til I install the packages and then plug in the adaptor? Or should I install the packages, reboot, and then plug in the adaptor?

If the USB is iffier (i know, i know, but i haven't had a cup of coffee yet) then the same questions apply. Should the card be mounted when I install the OS? Or should I wait til I install the packages, reboot, shut down, mount the card, and re-start?

Thanks very much for taking the time to help. If this works you can have my firstborn. The tuition will kill ya tho, so maybe that's not such a good deal. I'll think of something else, like passing the help on in my turn. ;)

---

### Post by teaker1s on 2007-01-26
personally I'd leave the card in and use the alternate.iso and see what happens

---

### Post by Cyberbayne on 2007-01-26
The PCI card or the USB adaptor?

That's something I haven't tried. Might as well give it a shot while I wait for aysiu to get back.
Thanks teak :)

---

### Post by Cyberbayne on 2007-01-29
> **teaker1s said:**
> personally I'd leave the card in and use the alternate.iso and see what happens

Alternate .iso DLed and burned properly.

Install goes fine until:

**Network autoconfiguration failed. Your network is probably not using the DHCP protocol. The DHCP server may be slow or some network hardware is not working properly.** 

In response: 

**My router is using the DHCP protocol.** This same computer with Windows booted has no problems connecting with the router. I'm using it now. There are other computers on this home network that also work fine, and the router DHCP table populates accordingly. **The server is not slow**, but I had the install program try to detect the router twice more just in case. Finally, I really think **the network hardware is working properly**, considering that I'm posting this using the same hardware.

Needless to say, the Live CD doesn't connect either.

The network adaptor is a Linksys WUSB11 v 2.5. The driver is the linux-wlan-ng which is included on the install disc. Once in Edgy, I've installed the driver, network manager, network-manager-gnome, and wifi-radar. I can ping 127.0.0.1, and 192.168.0.1, and that's it.

---

### Post by Cyberbayne on 2007-02-11
Well, its not an 'elegant' solution, and certainly not a purist *nix solution, but I'm up and running and posting this from my new distro (openSUSE - I got MUCH  more help there), and  thanks to the Buffalo Ethernet converter model WLW-TX4-G54HP, 5 minutes was all it took to overcome weeks of frustration. Be well, everyone, and thanks again to those from these forums (fora?) who tried to help.

---

### Post by Durito on 2007-03-22
This is a little after the fact, but I've had exactly the same problem with the ADMTek 8211 chipset--for some reason, in Ubuntu (and a few other distros--SuSE does seem to handle it differently), the router won't respond to DHCP requests from the wireless card. But only certain routers. In one coffee shop it'll work just fine, in other I'll have a strong signal and still get the cold shoulder from the router.

---

