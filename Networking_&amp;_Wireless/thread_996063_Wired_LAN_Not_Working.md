---
title: "Wired LAN Not Working"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by mossmotorsport on 2008-11-28
Hi all, sorry to be such a noob, lots of experience with computing but today fancied installing Ubuntu to start playing around.  Ran it off Live CD and internet etc was working perfectly.  Installed it to HDD and it will not automatically detect internet at all.  It just keeps saying "Network Disconnected" and "No Network Connection."

Searched forums, and google but cant find any answers.  Not sure what other useful comments to put down - other than its the latest 8.10 version and I'm using Virgin Media Cable as my ISP through a Linksys WRT300 Wireless N Router.  Any help greatly appreciated!:)

---

### Post by meastwood on 2008-11-28
I guess your're using dhcp -

1. can you ping your router?
2. what's the ouput of
# ifconfig
# route
3. are your nameservers set up in /etc/resolv.conf
4. is your NIC set to be automatically enabled on boot
/etc/network/interfaces
5. is your wireless router acting as a dhcp server

---

### Post by debeyt on 2008-11-28
I have the same problem. I am using Apple's Time Capsule to which the Ubuntu machine is attached by wire, not wireless. I also keep getting the "Disconnected" message. I have also tried another NIC but to no avail. When I attach a spare MacBook onto the wire, it works fine.

Any ideas?

---

### Post by mossmotorsport on 2008-11-28
No ideas from me yet, I've had enough of it and gone back to Windows Vista - at least that works out the box.  I cant see how it works from the CD but as soon as you install a local copy it forgets everything.  Its probably really simple, but with Linux there is no simple step-by-step plain english how to guides.

Im not a novice with computers either, I have a degree in computing science and design websites for a living!

---

### Post by debeyt on 2008-11-28
For me it has worked all along with the previous version of Ubuntu. I had a disk crash and put in a new drive and installed version 8.10. Now no more internet. By the way, it didn't work for me running it from the CD either.

Thanks:(

---

### Post by cariboo on 2008-11-28
Can you run in a Applications-->Accessories-->Terminal:

```
sudo lshw -C network > network.txt
```

This will create a text file with all the network hardware details. If you can copy the text file to your windows partition and paste it into your next post this  would help a great deal in solving your networking problem.

Jim

---

### Post by mossmotorsport on 2008-11-28
I will try pasting that code in tomorrow - thanks for that it will be useful to see what network problems I might be facing

---

### Post by debeyt on 2008-11-28
> **cariboo907 said:**
> Can you run in a Applications-->Accessories-->Terminal:

```
sudo lshw -C network > network.txt
```

This will create a text file with all the network hardware details. If you can copy the text file to your windows partition and paste it into your next post this  would help a great deal in solving your networking problem.

Jim
Tried that but get "bash: network.txt: Permission denied" message

Also, suddenly I was connected - how I don't know. Tried to open FireFox which kept looking for about 8 minutes getting nowhere. Then connection disconnected again. hasn't come back since.

Further suggestions?

---

### Post by debeyt on 2008-11-28
> **debeyt said:**
> Tried that but get "bash: network.txt: Permission denied" message

Also, suddenly I was connected - how I don't know. Tried to open FireFox which kept looking for about 8 minutes getting nowhere. Then connection disconnected again. hasn't come back since.

Further suggestions?

Again connected(?)- somewhat. Icon stated that I was not connected. However I was able to ping machines on the network and even google! Running dhclient also seemed to think I was connected as it stated:
"DHCPACK of  10.0.1.193 from 10.0.1.1"
"bound to 10.0.1.193 .. renewal in 5974 seconds"

Mean anything?

---

### Post by mossmotorsport on 2008-11-28
Under Live CD (which internet works fine on) it brings up

  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:22:15:02:98:38
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:83:50:32:9b:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Will post up local HDD copy when its installed again...

---

### Post by mossmotorsport on 2008-11-28
Below is the result from my local copy once installed to the HDD.  Still wont go online though or connect to local LAN 

 *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:22:15:02:98:38
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:67:f5:86:0d:3b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mossmotorsport on 2008-11-29
Bump!  Anyone got any ideas on how to fix this issue?  I have a few PM's from people having the same problem too.

---

