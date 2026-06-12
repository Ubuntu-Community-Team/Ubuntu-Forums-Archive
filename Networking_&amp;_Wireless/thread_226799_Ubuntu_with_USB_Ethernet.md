---
title: "Ubuntu with USB Ethernet?"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Per2 on 2006-07-31
Hi!


I built a raid-system with Ubuntu. The adding of 4 Sata-cards on the other hand had the shortcoming that I ended up with one PCI-card slot, from which I should get Ethernet and Firewire-connection. (I need to transfer files between two computers and to have a comple of Lacie harddrives connected to the machine with the Ubuntu installed) In an effort to accomplish this I bought Belkin's USB/FIrewire card (F5U508ea, more info from: [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=129021)and](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=129021)and) a D-link DUB-E100 Ethernet Adapter (more info from: [http://www.dlink.com/products/?sec=0&pid=133)](http://www.dlink.com/products/?sec=0&pid=133)).

For some reason I could transfer files from my computer with Windows XP to my computer with Ubuntu installed, but not vice versa. If I tried to transfer files the other way round, the network-connections ceased to function and never came back alive unless I booted the computer. I tried replacing the Belkin's card + D-link Ethernet-adapter with a D-link PCI-ethernet adapter and it is working just fine: I can copy files which ever way I want.

However, I am currently then still short of the firewire-connection and I have been considering getting USB Linksys USB1000 Gigabit Ethernet Adapter in high hopes that it would solve my problems where DUB-E100 failed. The problem of course is that I do not know whether the problem is with my USB/Firewire -card or with the Ethernet Adapter DUB-E100? This webpage seems to indicate that DUB-E100 should work ok: [http://www.linux-usb.org/usbnet/](http://www.linux-usb.org/usbnet/).

Can you guys please some help on how to resolve the matter?

On another topic I would appreciate if somebody could tell, whether Netgear's new HD Ethernet Adapter HDX101 could be used for transferring files via electrical network with the machine running Ubuntu and with the machine having Windows XP installed?


I know there are quite a many questions above. Please however try to take the time to help me with the aforementioned issues. Thanks guys for any help,



Per2

---

### Post by Per2 on 2006-08-13
Bump.

---

### Post by Per2 on 2006-08-24
I decided to buy a 7-port PCI-card with USB2, Firewire and Gigabit LAN. The card has "Realtek RTL8169/8110 Family Ethernet" inside of it. The card is not recognized by Ubuntu and there is no network card found in Ubuntu's networking.

I guess the serial bus got overrun with the Gigabit LAN as somebody had pointed out in some discussion relating to RTL8169. My mobo is an older one, Abit BE6-II.

Any clues how to get the card up and running? If there is not hope, I guess the only thing left to do is to buy a new mobo+processor+memory. Hopefully it will work ok atleast then and I will get the firewire + LAN I need...

Any help is still much appreciated.

Per2

---

### Post by Linux_Noobie on 2006-08-24
I dont know why its not detected. Did you just set it up or was it already up and running. I have 3 ubuntu pc's. One connected by Usb(Directly to rougher) one with a ethernet port.And one with Wireless. Also it is also weird because i have a similar Ethernet to you. (Same company) and it auto detected it.

---

### Post by Per2 on 2006-08-25
Hi!


I just added the card with Realtek chip into my computer (i.e. it had already ubuntu running). There at the start there is a flash with "cannot allocate..." something and it comes in multiple lines. I thought that maybe the gigalan used up all of the serial bus...

Is the USB LAN running fine in your system, cause if I try to copy something from my machine with Ubuntu into my computer running Windows, the network immediately gets messed up? The other way round the copying works ok.


Per2

---

### Post by Per2 on 2006-08-25
I tried to see what kind of messages there are during the booting of the machine. First the bios puts out multiple lines, all the way from 1 to 31 saying "system bus controller" after each number. Then there is a quick flash and what I managed to read is that it says "unable to allocate resource". The card is not recognized by Ubuntu at all. I can try to give further information for you guys via terminal, if you give me suggestions on what kind of commands I should try.

Thanks,

Per2

---

