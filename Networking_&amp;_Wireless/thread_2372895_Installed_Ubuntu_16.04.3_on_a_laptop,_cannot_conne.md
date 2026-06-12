---
title: "Installed Ubuntu 16.04.3 on a laptop, cannot connect to internet via Arris Surfboard"
date: 2017-09-29
forum: Networking &amp; Wireless
---

### Post by brettt on 2017-09-29
I am new to linux and decided to try it out last night, I have no prior experience dealing with networks or resolving issues related to the internet. I installed **Ubuntu 16.04.3** last night and it would not connect to the internet after I got it fully installed from a flash drive, this issue has not been resolved after turning the **Arris Surfboard SBG6580** modem/router combination off and back on again as well as the laptop, which is a **HP m6 notebook**, being restarted since last night. 

It will not connect over Wifi or either of my Ethernet cables, both of which work just fine to connect my windows 10 laptop to the internet. The Ubuntu laptop is just constantly having 'waves' go up its wifi/internet icon in the top-right. Upon finding the forums I saw the '[Before posting Networking and Wireless]("http://ubuntuforums.org/showthread.php?t=370108")' thread and followed its instructions but when I ran the script it only gave me this,
```
####### wireless info START #########
```
Which pretty much tells me nothing and I don't imagine it tells anyone else anything either, but I wanted to complete this step in case anyone can get insight from it or knows what I might have done wrong. The laptop is currently connected to the modem/router via my Ethernet cable and it still has not connected to the internet.

The modem/router has given me plenty of issues before. Recently after start up my windows laptop it connected to the router but not to the internet. Using windows built in trouble shooter this was quickly resolved as the IP address not being configured correctly. The laptop I installed Ubuntu on previously had windows 8 and gave me no end of trouble, it also would not connect to my home wifi either but it would connect to other peoples wifi if I brought it to their house. Windows 8's own troubleshooter however could not solve the problem and I never attempted to fix it as I already had a laptop with windows 10 on that did everything I needed.

Please help I would like to try out Linux/Ubuntu but after spending most of last night trying to solve the problem on my own through google, I am left clueless.
*Note: I have no issue formatting the problem laptop and reinstalling everything if you think that will help and I regard this entire thing as a learning experience.*

---

### Post by TheFu on 2017-09-30
* always post the exact command run **and** the output.  Sometimes people run the command incorrectly.
* I suspect your ethernet network card isn't supported or recognized.  Post **sudo lshw -C network** output - please use "code tags" so things line up.  You'll probably need to install lshw.  lspci might have the info, somewhere.  I just don't like the format of that output.

"code tags" - adv reply (#)

---

### Post by brettt on 2017-10-01
Thank you for your response Thefu, this is what was outputted when I entered 'Sudo lshw -C network' into the terminal.
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:01:00.2
       logical name: eno1
       version: 0a
       serial: 6c:3b:e5:82:d4:cd
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:34 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlo1
       version: 01
       serial: 20:16:d8:5f:21:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.10.0-35-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0100000-f017ffff memory:f0180000-f018ffff
```

---

### Post by TheFu on 2017-10-01
Sorry, don't have time for a more detailed response, but if you search these forums for that specific ethernet chip and that driver, I bet you'd find the solution.

That is a fairly common issue.

OTOH, I could be completely missing the issue at this stage.  Can you ping the router from here?  Can you ping well-known public IPs - like 8.8.8.8?  Can you ping google?  Which of those work and which don't is a key thing to determine where the issue lies.

---

### Post by brettt on 2017-10-01
I have not yet searched the forums for those terms but I know I cannot ping the router or google currently.

---

### Post by TheFu on 2017-10-01
> **brettt said:**
> I have not yet searched the forums for those terms but I know I cannot ping the router or google currently.

Please show your work, completely.

---

### Post by brettt on 2017-10-02
Alright I have fixed the problem with Ethernet not connecting by setting IPv6 to ignore rather than to automatically find an address. This same fix did not work for for my wireless at home, though I am still able to connect to other wireless networks without a problem.

I wanted to post this in case anyone else searches a similar problem. I do not have time until this weekend to properly sit down and figure out the wireless problem, but now that I am past the issue with the Ethernet, I am confident I can find a solution to the wireless connectivity. 

Thank you, TheFu.

---

