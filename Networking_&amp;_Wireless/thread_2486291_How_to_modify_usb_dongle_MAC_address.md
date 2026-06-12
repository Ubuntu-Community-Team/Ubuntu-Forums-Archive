---
title: "How to modify usb dongle MAC address"
date: 2023-04-25
forum: Networking &amp; Wireless
---

### Post by gipsyshadow on 2023-04-25
I use my 4G Huawei E3272 usb dongle with my PC on ubuntu 18.04 and I wonder if it's possible to modify its MAC address.
Here're some data about it:
- lsusb
```
Bus 001 Device 004: ID 12d1:14db Huawei Technologies Co., Ltd. E353/E3131
```
- sudo lshw -c network
```

  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enx582c80139263
       serial: 58:2c:80:13:xx:xx
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.1.100 link=yes multicast=yes

```
- ifconfig -a
```

enx582c80139263: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::165c:d2b8:d0b3:eb41  prefixlen 64  scopeid 0x20<link>
        ether 58:2c:80:13:xx:xx  txqueuelen 1000  (Ethernet)
        RX packets 177409  bytes 184125258 (184.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 106059  bytes 12807673 (12.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
Hope this helps a little bit :)

---

### Post by chili555 on 2023-04-25
> ether 58:2c:80:13:xx:xxI suspect that the four digits that you redacted are 9263. Am I right?

Do you want to change the MAC address shown on your own computer, lshw, ip a, etc. or do you want to change the MAC address that your router, your ISP and the internet may see?

---

### Post by gipsyshadow on 2023-04-25
1. Yes, you're right! How could you know?
2. The 2nd one. Is this possible?

---

### Post by The Cog on 2023-04-25
1: It's in the logical name: enx582c80139263
2: I don't know if this will work, but you could try:
```
sudo ip link set enx582c80139263 address 12:34:56:78:9a:bc
```
Note that the first byte **must** be even, and the second digit ought to be 2, 6, a or e to indicate that it is locally administered (although I don't think that's so important).

---

### Post by gipsyshadow on 2023-04-25
I see.
Let me ask a very newbie question: how/where can I check the MAC address my ISP "sees" from my dongle? In other words, I think it's not enough to inquire only my ubuntu command line to be sure of this modification, is it?

---

### Post by jeremy31 on 2023-04-25
If you change too many things your ISP sees, you might not have service any more

---

### Post by gipsyshadow on 2023-04-25
I'd like to change only my usb dongle's MAC address and consider that now I'm only evaluating to switch to another ISP because my actual ISP lets me surf the internet using its sim within my Huawei usb dongle but the ISP I'm evaluating claims not to do it, it "doesn't guarantee" its sim will work within an usb dongle but only within a smartphone (-> I've got no one and I don't want to by any).

---

### Post by jeremy31 on 2023-04-25
If that is what you are doing, I don't think cellular companies care about MAC address, however they will know the IMEI of the device and ICCID(SIM card number) when it tries to go online

---

### Post by gipsyshadow on 2023-04-26
I thought any ISP could see "something" about these devices in remote and understand if it was a smartphone or a dongle or a wifi hotspot device. Due to this "something" some ISPs don't allow to use their sims for, eg., tethering and forumers confirm it's impossible.
Nowadays my case is quite rare because nobody surfs the internet via dongles anymore so its very difficult for me to get informed about that before switching to a new ISP.

So if "cellular companies [don't] care about MAC address", how is it possible for them not to allow users to use their sims for tethering, hotspot and so on?
If MAC doesn't matter in this scenario, is this an IMEI matter?

---

### Post by jeremy31 on 2023-04-26
I know they can see the IMEI as my cellular provider used to have a website where you could search by IMEI to see if you could use the device on the network.  I bought a 4G router that I was going to use as it was advertised as compatible but when I checked the website using the IMEI it said it wasn't

---

### Post by gipsyshadow on 2023-04-26
> **jeremy31 said:**
> my cellular provider used to have a website where you could search by IMEI to see if you could use the device on the network
Lucky you, mine doesn't!
So definitely it's an IMEI matter and my "researches" must address to IMEI modification (if possible), right? Is it better if I open a new thread or we can go on here?

---

### Post by jeremy31 on 2023-04-26
I don't think it is a matter for Ubuntu support.  It may be something the users at [https://www.xda-developers.com/](https://www.xda-developers.com/) can help with

---

### Post by gipsyshadow on 2023-05-03
> **chili555 said:**
> Do you want to change the MAC address shown on your own computer, lshw, ip a, etc. or do you want to change the MAC address that your router, your ISP and the internet may see?
Is there any way to change my dongle's "LAN MAC address: 00:0D:87:....." via ubuntu? I mean the one *your router, your ISP and the internet may see*? Or is this another question just for xda-developers group?

---

### Post by chili555 on 2023-05-03
Please see: [https://askubuntu.com/questions/1393693/how-to-prevent-real-mac-address-leakage](https://askubuntu.com/questions/1393693/how-to-prevent-real-mac-address-leakage)

---

### Post by gipsyshadow on 2023-05-04
As far as I could understand I can use macchanger only to change my "inner" dongle's mac address (I mean the mac address as seen by my pc as "inner"), right? Maybe I misunderstood but it's only written how I can get my "outer" dongle's mac address and nothing more about that, isn't it?

---

### Post by chili555 on 2023-05-05
Your USB wireless MAC address is visible within your network, including your router.If you are connected to your router, I believe your ISP only sees the MAC address of the router. That means that they see that someone in your network searches for, as an example, roses for mothers day, but they can't see if it was you or your father or your son or your week-end visitor.

From my link above:
> The MAC addresses visibility is limited to the broadcast domain only. It means the MAC cannot go through router to other network segments. Any network router is the OSI layer 3 (L3) device and removes any layer 2 information including the MAC in normal circumstances.Also see: [https://networkengineering.stackexchange.com/questions/42122/can-isp-know-computer-mac-address-in-local-network](https://networkengineering.stackexchange.com/questions/42122/can-isp-know-computer-mac-address-in-local-network)
> A mac address doesn't make it past the first hop (most likely your home router). It stays local to the broadcast network.

IMEI isn't transmitted over wifi, so your ISP will also not see your IMEI. Your cell provider definitely sees it though.So the short answer is that you can use macchanger to change the MAC your router sees, but why would you?

---

### Post by gipsyshadow on 2023-05-06
I'm less than a newbie about this matter but I know for sure some phone carriers/ISPs block your internet connection if you put their sim cards within a router or an usb dongle; I red that many times from a lot of forumers. Therefore my question is "how" they can do that, in other words how a certain ISP can understand my sim is put within a smartphone or a usb dongle. Due to that I'm almost sure now my current ISP can see my dongle's "data" (IMEI?) and permits me to surf the internet.

I've understood how to change my dongle's IMEI so I'm "quite" sure I solved this issue *but* I just wonder if an ISP can see other data from my dongle, eg. its MAC address. If so I'm afraid that changing IMEI won't be enough because ISP will see my dongle as, eg., a smartphone (due to new IMEI) but with a router/dongle manufacturer's MAC address at the same time and it will decide to block my connection. In particular, my dongle's MAC address (I mean the "outer" one) is 00:0d:87... and it belongs to "elitegroup computer systems co.,ltd."; I've checked it via [https://dnschecker.org/mac-lookup.php](https://dnschecker.org/mac-lookup.php)
So now I wonder if and how I could change my dongle's MAC address (00:0d:87...) possibly via ubuntu to be "more sure".

Do you think I'm on the wrong way to get my goal (do not permit any ISP to block my internet connection if I use its sim within an usb dongle)?

---

