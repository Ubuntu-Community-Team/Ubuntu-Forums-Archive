---
title: "No working leases in ersistent database - sleeping."
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Pochen on 2008-07-19
Hi!
Im just installed Ubuntu Server edition and am kinda new with linux in the way of using the terminal and not using GUI.

I have a netgear wireless usb adapter that i have installed by using ndiswrapper.

i followed [this guide]("http://ubuntuforums.org/showthread.php?t=571188") to try to connect to my network at home, but i just get "No working leases in ersistent database - sleeping." instead of getting and IP.

When i run iwlist wlan0 scan i get no result, but im using that wireless network with my laptop right now when im writing this post so i'm pretty sure it is functional ;)

So, someone have any idea why it messes with me? Or do you need more fact about my card/config?

---

### Post by issih on 2008-07-19
Chances are that your wireless card is simply not working. Those errors are related to dhcp failing to aquire an ip address, that and the empty scan list make this the most likely problem . Just because ndiswrapper installs a driver is no guarantee that it will work I'm afraid.

First off give us the results of:

sudo lshw -C network

lspci

lsusb

That ought to let us see what your wireless chipset is, and we can go from there.

Might be worth changing the title of the thread to something else too, get more eyes on the problem as it were.

---

### Post by Pochen on 2008-07-20
lshw -C Network does not find the device wlan0 today. I guess the reason is because of my reboot. It does find my internal device (eth0) and displaying "DISABLED" wich i correct.

lsusb 
Bus 004 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

Since i dont have internet on my server i have a hard time copy/paste the output so i have to write it.

---

### Post by issih on 2008-07-20
have a read here:

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

Sounds like it might be worth blacklisting a few modules.

---

