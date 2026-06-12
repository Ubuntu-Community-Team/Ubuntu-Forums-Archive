---
title: "Netgear WG121 problems"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by talon on 2007-01-17
Hello again all,

One of the main problems with my attempts to go completely open source is linux's seeming inability to be able to:
a) find my wireless device. ubuntu is MUCH better than most here (6.06 LTS), in that it not only picks up my netgear WG121, it also recognises it as a wireless device! Most other distros refuse point blank to accept it even exists.
b) (and this is where ubuntu is falling flat on it's face) CONFIGURING the wireless device. No matter how hard I've tried in 6.06 (ubuntu and kubuntu) it refuses to accept my network information. I've tried to set it up like my windows is set up using DHCP, but it refuses to connnect to my router. Static also isn't working, and I have no idea why.:confused: ](*,) 

I'm not sure what else I can say on the issue, please ask questions requesting more information if you need it, I would really like to get this problem sorted.
(Also replys starting "use apt-get to download....." are NOT helpful, as I CANNOT YET CONNECT TO INTERNET!!)
thanks in advance

---

### Post by teaker1s on 2007-01-20
install
network-manager-gnome

this can be installed from alternate.iso and using either apt or synaptic to add cdrom source


now on your desktop panel you want to click system administration networking

it's important to make sure that devices show unconfigured so network-manager-gnome can control them. Shutdown and remove ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in passphrase or network key
_

---

