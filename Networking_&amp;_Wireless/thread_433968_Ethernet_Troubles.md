---
title: "Ethernet Troubles"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by johnbellone on 2007-05-05
I've been trying for the past few weeks to get Ubuntu installed on this old system that I have had lying around but I can't seem to get the Ethernet card working. Unfortunately due to school I have not had the time to search the forums or Internet for anything so I decided to just come here and post up the information about the system.

Its an old stock Dell machine. Pentium 3 550MHZ and TNT2 graphics card with 768MB of SDRAM (rated probably at 133MHZ). I can get the operating system installed perfectly fine and it even works. I am looking to just run a server (no Gnome or KDE). But like I said I am getting errors with the network card and it seems not to be recognizing upon bootup. I've checked through some of the diagnostics (haven't troubleshooted Linux in quite a bit of time) and it seems to be using a Realtek driver (from what I understand is a fallback/default driver?). 

Here's the information off the card itself:
3Com 920-BR03 (Etherlink 10/100 PCI 3C905C-TXM)
Broadcom chipset (5904)

Unfortunately I don't have any extra cards lying around to test in the machine. I'm almost certain the machine worked before I received it (person upgraded after a number of years of just web browsing). I formatted Windows 98 off the machine immediately and let it sit around the shop. We're looking for a fileserver and something to hold some SVN depositories (nothing needing too much processing power). So I loaded it up with ram, a decent hard-drive and booted it up. I was surprised with the network card not working and just expected it to be driver related. Now that I have some time (just finished exams) I plan on getting this working. Anyone have any suggestions?

---

### Post by chili555 on 2007-05-05
> I am getting errors with the network cardLike what, for instance? What does *dmesg* say about it?> seems to be using a Realtek driver (from what I understand is a fallback/default driver?).

Here's the information off the card itself:
3Com 920-BR03 (Etherlink 10/100 PCI 3C905C-TXM)
Broadcom chipset (5904)So far, it might be a Realtek or a 3com or a Broadcom? I'm sure it's one of them, but let's try to find out more precisely. Please let us see:```
sudo lshw -C network
```

My sixth sense tells me it's a 3com. Please try:```
sudo modprobe 3c59x
sudo ifconfig eth0 up
sudo dhclient eth0
```Let's see if we are lucky today!

---

### Post by johnbellone on 2007-05-05
> **chili555 said:**
> Like what, for instance? What does *dmesg* say about it?So far, it might be a Realtek or a 3com or a Broadcom? I'm sure it's one of them, but let's try to find out more precisely. Please let us see:```
sudo lshw -C network
```

I can't post everything because I don't feel like typing it all but it is indeed a 3c905C-TX/TX-M [Tornado] using the driver 3c59x.

> 
My sixth sense tells me it's a 3com. Please try:```
sudo modprobe 3c59x
sudo ifconfig eth0 up
sudo dhclient eth0
```Let's see if we are lucky today!

This is what I got when I did that sequence:
```

Listening on LPF/eth0/:00:50:da:2b:37:82
Sending on LPF/eth0/:00:50:da:2b:37:82
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

```
It continues incrementing intervals from 9, 10, 13, 18 and 5. When I attempt to ping my router (which is running the DHCP) I get the following:
```

connect: Network is unreachable

```
When this is done before the instructions you gave me it just hangs and finally gives me a 100% packet loss.

Oh, not sure if it matters but I'm running Ubuntu Server 6.10.

---

### Post by johnbellone on 2007-05-06
Anyone thing that the new version would fix anything? I've been looking around for another ethernet card to no avail.

---

### Post by chili555 on 2007-05-06
I do not think the new version will change anything. The card appears as eth0, asks for an IP address, pings, unsuccessfully so far, which suggests the hardware and operating system are working well together. Is this connected to a router or switch or directly to the cable modem or what?

Please do the command:```
sudo ethtool eth0
```Please post the result here. One thing we will be looking for is 'link detected: yes.'

---

