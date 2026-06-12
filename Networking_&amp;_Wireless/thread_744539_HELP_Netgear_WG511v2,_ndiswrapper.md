---
title: "HELP Netgear WG511v2, ndiswrapper"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by shuster on 2008-04-03
Hi. I´m new to Ubuntu. I´d like to configure my wireless PCMCIA WG511V2.
After trouble installing ndiswrapper I got it working (utils1.9)
Now I got the ndiswrapper -i wg511v2.inf and he installed the driver.
at ndiswrapper -l I get
invalid driver!
If I want to reistall he tells me driver already installed.
If I try to remove, ndiswrapper -r wg511v2 i get
Inapropriate ioctl for device
I really don´t know what this means. And its some days now I don´t get out of this :mad:
THANKS:
by
Rob.

---

### Post by Bosk22 on 2008-04-16
Hi

I used this reference to get  my PCMCIA WG511V2 up and running 

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)

It is a excellent reference on all things wireless and linux

I expect your problem relates to the need to load the microcode for the firmware of your card

Good luck

---

### Post by dstew on 2008-04-16
Was the .sys file in the directory along with the .inf file when you did sudo ndiswrapper -i wg511v2.inf?

---

