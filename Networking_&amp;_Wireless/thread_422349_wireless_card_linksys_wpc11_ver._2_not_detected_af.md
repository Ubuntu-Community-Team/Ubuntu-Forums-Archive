---
title: "wireless card linksys wpc11 ver. 2 not detected after feisty update"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by fightingdurden on 2007-04-25
hello all,

i am totally new to ubuntu (and linux in general, unfortunately...but i am loving it so far! screw M$) as i just discovered the greatness of it a couple weeks ago. i have been toying around with it and i am getting more and more comfortable by the day, but am still very new. i had a problem that after i upgraded to feisty my wireless card, a ***linksys wpc11 ver. 2.0***, was not detected. it worked remarkably well on edgy. like i said, i am new, but i know most of the basic stuff and understand how to use the terminal to input commands, but still treat me as a noob. if anyone can help me i would appreciate it. thanks in advance. 

erik

p.s. this is my first post! woo!

---

### Post by chili555 on 2007-04-25
Congratulations! Welcome to the party.

I feel lucky! Please open up that terminal and do:```
lspci -v | grep Network
```Is it a Prism card? If so, then do:```
lsmod | grep prism
```Does it report that prism2_cs is loaded? If so, do:```
sudo gedit /etc/modprobe.d/blacklist
```Add the following on its own line:```
blacklist prism2_cs
```Save and close gedit. Reboot and let us know.

Of course, if this is not a Prism card, post back and tell me this was not my lucky day!

---

### Post by fightingdurden on 2007-04-27
hi chilli555!

thanks for the response.

i did the first step. to check if it is prism or whatever and got: **_Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network_**

im not sure if that will change what i need to do or not. thanks in advance.

erik

---

### Post by chili555 on 2007-04-27
You're right, that doesn't tell us much. Let's try:```
sudo lshw -C network
```If it confirms your WPC11 is a Prism chipset, proceed with the other steps outlined above. If not, post the details and we'll take the next steps.

---

### Post by fightingdurden on 2007-04-28
this is exactly what i get when i do that command:

 *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0e:7f:70:f1:0a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=natsemi driverversion=1.07+LK1.0.17 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:8c00-8cff iomemory:d0003000-d0003fff irq:11
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:00.0
       logical name: wlan0
       version: 20
       serial: 00:0c:41:a6:c8:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.5 multicast=yes wireless=802.11b linked
       resources: ioport:1000-10ff iomemory:22000000-220001ff irq:11

thanks.

erik

---

### Post by chili555 on 2007-04-28
Well, now I am *really* confused! This is the information that tells us what chipset your card has:```
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
```It's not a Prism, so all the steps above are not appropriate. However, this:```
ip=192.168.1.5 multicast=yes wireless=802.11b linked
```Suggests you are linked and have been given an IP address from your router! Does it have an IP address because you've set up a static IP?

By default, if Feisty, the needed driver, r818x is blacklisted because of some nasty problems it sometimes exhibits; for example: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/31857](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/31857)

You can:```
sudo gedit /etc/modprobe.d/blacklist
```and comment out r818x. Change *blacklist  r818x* to *#blacklist  r818x*.

---

### Post by fightingdurden on 2007-04-28
oh umm...i may have left out an essential piece of info. i reverted back to edgy once feisty didn't work. so that is what i am on now. if i needed to be on feisty for those commands to show you what you need to know, that probably wouldn't work. sorry. i'm slightly retarded. i just didn't want to go to feisty and lose connection for who knows how long. let me know if that would be affecting the info that you need. thanks in advance.

erik

---

### Post by chili555 on 2007-04-28
> i reverted back to edgy> it worked remarkably well on edgy.So, I guess you're connected? Or did the reversion to Edgy not fix it?

---

### Post by Lanced on 2007-04-29
Hi, I'm having the same problem.  Same wireless card, same upgrade from Edgy to FF on a Dell Latitude C400.  

I uncommented the r818x driver and that got the wireless connection to show up in Network Settings.  However under Connection Properties it says Status: Disconnected and if I click Configure it says "The interface does not exist".

I'm not really adding to the solution here but at least I know I'm not alone on this one...

---

### Post by fightingdurden on 2007-04-29
yeah, im back on edgy and am connected but i want to upgrade so i want to figure it out. thanks

erik

---

