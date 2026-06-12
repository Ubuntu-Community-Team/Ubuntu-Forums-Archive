---
title: "Connecting a network storage device via a router."
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by s1wood on 2013-09-06
I've got a secondhand network storage device without instructions. It connections to my router by a cable, my computer is connected to the router by wireless. I thought I should be able to access the storage device from my computer but I can't find any way of doing this: after several hours of internet searching and experimenting I can't make any of the instructions work - probably because I don't understand them. Too many meaningless strings of letters and numbers required.
Could anyone talk me through this in simple terms?

Susan

---

### Post by steeldriver on 2013-09-06
Do you have access to a web based admin interface on the router? if so, can you find a page that lists the attached devices? That would be a good first step (it will allow you to find the storage device's LAN IP, if it has been assigned one). After that it depends how you want to connect.

If you can't access a suitable router web page then you could install a program called 'nmap' and use that to probe the LAN for your device's IP

If you can't see it at all then it's possible the device was previously configured with a static IP that is outside of your LAN IP range - in that case some extra steps will be required e.g. resetting the device to 'factory settings' which should allow it to accept a DHCP IP

---

### Post by s1wood on 2013-09-07
I can access the router interface but I can't find anything about attached devices. I will try nmap.
Thanks,

Susan

---

### Post by prodigy_ on 2013-09-07
> **s1wood said:**
> I've got a secondhand network storage device without instructions.
What without any instructions at all? Now that's cruel. How are you going to access it? If it runs Linux, for example, you at least need to know its root password and its web-interface or SSH port. And its IP address if it's static.

I guess both devices are on the same (internal) network so the router acts as a switch for them. What do you need to ensure is that they both are on the same IP subnet. If the storage is configured to obtain IP automatically (via DHCP) it probably gets one from the router. Can you see active IP reservation in your router web-interface?

If the storage is configured to use a static IP (no DHCP), you'll probably need a way to access it directly (at least temporarily - to reconfigure it). Maybe via a crossover ethernet cable - then you'll need to set another static IP from the same subnet on your computer manually.

---

### Post by steeldriver on 2013-09-07
just fyi a couple of basic nmap scans are

1. basic ping scan of the 192.168.1.0 - 192.168.1.255 IP range
```
 nmap -sP 192.168.1.0/24
```

2. port scan (lets you see what services - if any - are running on each discovered host)
```
 nmap 192.168.1.0/24
```

3. port scan plus attempted OS discovery (may help to pinpoint a particular type of device e.g. if you know the NAS is running Debian whatever) - SLOW!
```
 sudo nmap -A -T4 192.168.1.0/24
```

but as prodigy_ says, if it's not got an address in your current LAN IP range (either through luck, or DHCP) you may need to connect directly and fix that before you can even see it from your other devices

---

### Post by SeijiSensei on 2013-09-07
If you try scanning ports with nmap, you must use sudo.  Only the root user can do that.

---

### Post by s1wood on 2013-09-07
I installed nmap but couldn't work out how to start it (I did say things needed to be simple). However, going back into the router interface and searching all the subsections I did find a Net Disk listed with it's own IP address so I put that in the browser and found myself in the set-up for the storage. I enabled a few things by guess work then tried 'connect to server' using that address and opened the drive successfully. I have also managed to bookmark it and to open it from the laptop so I have now got access.
Now what I need is an explanation of the options on 'connect to server' - I've got it on Public FTP at the moment - are there better options?

---

### Post by sandyd on 2013-09-07
moved to networking and wireless

---

### Post by kurt18947 on 2013-09-07
I know enough about this stuff to be dangerous:p but I have a somewhat similar situation and "filezilla" found in the repositories makes it pretty simple.

---

