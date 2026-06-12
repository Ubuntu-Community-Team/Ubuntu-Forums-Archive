---
title: "orinoco_pci module not available in gutsy to get wireless working"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by H-Radical on 2007-10-28
Hi all,

I have an Intersil Corporation Prism 2.5 Wavelan Chipset to connect to my wireless network. After a Gutsy upgrade, it is not recognized and no wireless connection shows up in Network Settings. After the upgrade to Feisty, the following used to fix it:
```

# modprobe -r orinoco_pci
# modprobe -r hostap_pci
# modprobe -r prism2_pci
# modprobe orinoco_pci
```
but now, the last command returns:```
 FATAL: module orinoco_pci not found
```

I have installed the restricted modules and enabled them but that didn't help.
I know this usually has to do with a kernel upgrade, but does anyone know what exactly is causing this?

Cheers

---

### Post by Lambert on 2007-10-28
The module is just orinoco not orinoco_pci

---

### Post by H-Radical on 2007-10-28
Well, what I had in feisty that made it work was orinoco_pci... I still have the commands in my rc.local . I just tried orinoco, too. that one didn't give me a "not found" error but it didn't fix things either.

---

### Post by H-Radical on 2007-10-28
I just booted back to my old kernel: 2.6.20-16-generic . Now I have my old orinoco_pci module but that still doesn't work. Does anyone know of a way to get a prism2 chipset working in gutsy?

---

### Post by Lambert on 2007-10-28
Ok, saw this bug

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126220](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126220)

can't offer anything else as the prims cards have always been confusing to me with all the different drivers.

---

### Post by H-Radical on 2007-10-29
OK! I'm accessing the internet using my wireless right now. I don't quite know what I did that fixed it but here it goes...
```
# modprobe hostap_pci
# modprobe prism2_pci
# modprobe orinoco_pci
```
Notice that I'm booting into 2.6.20-16-generic kernel. Then I opened the Network Selector Application which I'd added a while back and saw that it hadn't connected to anything. Then I did```
# modprobe -r orinoco_pci
# modprobe -r prism2_pci
```
and all of a sudden I saw network selector change icons and wlan0 was connected. The weird thing is that in network manager, after I added all of the modules, I got two wireless networking entries, non of which worked. But I edited the properties on one of them to include the information of my network, and then when I removed those other modules, that entry that I'd edited wasn't even checked but network selector connected to the right network. (maybe it knew from before?) Anyway, I still have the default gnome wireless network icon on my panel with a red dot on it and when I click on it, I get:```
Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device
```
I'm guessing that after a reboot I won't have wireless, but we'll see.

Cheers.

---

### Post by Lambert on 2007-10-30
My guess is you're using the hostap_pci driver. You can run 

sudo lshw -C network

which will list your device and on the configuration line it will show you what driver is bound to the device. If it is hostap_pci then you just need to blacklist orinco and prism2 modules and you should get wireless on boot. If hostap_pci doesn't auto load, you can add it to config file to load.

The bug report I listed showed that driver was preferred in gutsy and why orinoco_pci was left out. If you boot into the 2.6.22 gutsy kernel and make sure hostap_pci is loaded, you should get wireless with that kerenl also.

---

### Post by H-Radical on 2007-10-30
Well... this is something interesting that I found: After I rebooted, of course, wireless was gone. lsmod showed that neither hostap nor prism2 modules were loaded (In feisty, I'd put the commands in rc.local to remove them and add orinoco, so its not surprising) and orinoco and orinoco_pci were indeed loaded. I started network selector, which showed that I was not connected to any network. But then, before I could remove orinoco and add hostap, network selector connected to my wireless network. Yesterday, I'm sure that I'd removed everything except hostap, so there was nothing else for it to work with. So I think its something Network Selector can do and nm-applet can't.
Today, sudo lshw -C network showed that the driver is orinoco and the module is orinoco_pci. But still nm-applet doesn't see my wireless, so the interface is wlan0 rather than eth1. Also, wifi-radar doesn't see any networks, so I'm not sure what I should do if I need to connect to a network away from home. Still looking to get my eth1 back.

cheers

---

### Post by kevdog on 2007-10-30
Just to clarify -- its the hostap driver that is working for you now?

---

### Post by H-Radical on 2007-10-31
No; its orinoco.  Actually, today I started my computer and the wireless worked with only the orinoco module loaded, no network selector. I still have no eth1 interface (which is what it used to be called in Feisty), but wlan0. I don't know what the different names mean, but the wireless network icon on the panel is still showing only a dead eth1.

---

### Post by kevdog on 2007-11-01
Not to beat a dead horse, I thought in the first post of this thread you said the orinoco driver didnt work.

---

### Post by dbushong on 2007-11-04
Just to add to this post, I used to have working wireless on my Thinkpad T23 (Prism2.5 Intersil, yadda) in Feisty as long as I had prism2_pci blacklisted.  As of Gutsy, there doesn't even appear to be a prism2_pci module to blacklist, orinoco and orinoco_pci no longer load (just hostap_pci), and wireless no longer works.  

An iwconfig eth0 to view my wireless settings shows the device, and I can even browse access points with iwlist, but:

[LIST]
[*]my ESSID shows up with a "u" or "w" (randomly) at the end of it; in other words i type "iwconfig eth0 essid foo" and it shows up as "foou" or "fooW" etc.
[*]"dhclient eth0" never returns, and statically setting the ip doesn't get me net either.  in other words, the device seems to work for everything except actually transmitting and receiving packets.
[/LIST]

---

