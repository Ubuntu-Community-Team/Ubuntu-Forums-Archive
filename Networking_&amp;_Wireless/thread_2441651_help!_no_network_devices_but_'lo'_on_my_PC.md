---
title: "help! no network devices but 'lo' on my PC"
date: 2020-04-25
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2020-04-25
Hi all, 
Can't understand what is going on. 
ifconfig returns only 'lo' on my PC. No ethernet and wifi card available. I'm writing this from my notebook where everything is ok so far.

I ran apt-get update; apt-get upgrade on my PC recently (and did not do it on my notebook for a while), is it something that could possibly cause this issue?

I can use my usb modem on PC though, virtual network card appears in ifconfig after I plug it.

18.04.4 LTS on my both computers.

Please help.

---

### Post by Tadaen_Sylvermane on 2020-04-25
most likely a driver issue. wifi I'm not surprised but I thought all ethernet drivers have been pretty much static for years nearly. Run the following command to see if it can even see an existing device.

```
lshw -C network
```

That will tell you what they are. Then you can track down driver issues. Gotta start somewhere.

---

### Post by marchello_lippi2 on 2020-04-25
It returns only my usb modem virtual network device. At least this works... 
```

[FONT=monospace][COLOR=#000000]$ sudo lshw -C network[/COLOR]
[sudo] password for user1:  
  *-network                  
       description: Ethernet interface
       physical id: 1
       logical name: enx0c5b8f279a64
       serial: 0c:5b:8f:27:9a:64
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.8.100 link=yes multicast=yes
[/FONT]
```

Also I must say that I just tried to boot from my old hdd (ubuntu as well, but no updates applied for at least one year) and it shows the same result. It worked fine before. I just upgraded to ssd and left hdd as slave device. So my guess is that it's not driver issue, but rather hardware one. 

I've had few issues with this PC before, one time it was memory error on boot, second time it was video card error on boot as well; repair guy just cleaned it from dust and it started working fine in both cases; don't know, maybe the motherboard is dying... 

I will contact my local computer shop to see if they can help me to install additional PCI network card, hope this will work for me.

---

### Post by Tadaen_Sylvermane on 2020-04-25
Yea. One more thing to be sure maybe boot live image. If doent work then you are 100% positive hardware.  Especially if it used to work. 

Depending on age of hw though, can last long time. But not forever. Nothing these days is built to last sadly.

---

### Post by marchello_lippi2 on 2020-04-26
Live-cd showed no network devices but 'lo' yesterday.

Then... this is weird. Today my built-in ethernet card appeared again and works fine. Hm... I see that I can't rely on it anymore. 

Just recalled that I have usb-wifi dongle also, so I'm covered a bit more. 

What I'm going to do is to buy usb-ethernet dongle just in case. Also will ask in computer shop to install additional ethernet PCI card. If they tell me that the motherboard is dying, then will upgrade it so that I can use intel cpu instead of adm.

---

