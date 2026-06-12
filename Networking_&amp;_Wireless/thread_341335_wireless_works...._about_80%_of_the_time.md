---
title: "wireless works.... about 80% of the time?"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by ac251404 on 2007-01-18
I have a thinkpad x31 which I have had Ubuntu Edgy installed on for a few weeks. I am frequently changing wireless networks moving from home to campus and to where I work. For the most part it works fine, I have 3 profiles setup - one for each location and I usually just load the appropriate profile up and everything is fine. The problem is sometimes when I boot up my laptop, it doesnt detect and wireless! Usually my wireless shows up as eth0 and wifi0 but occasionally there is just nothing there. It can sometimes take like 4 reboots in order for it to appear. It was working immediately after my Edgy install so I haven't added any other packages. Also, when it didn't show up in the networking application I tried doing 'iwconfig' in the terminal and still nothing showed up. Anyone have any ideas?  

Also is there any kind of package which will just let me choose to view wireless networks and connect/reconnect to them at will (i.e. win xp)? As of right now I have to know the ESSID in order to connect.

Thanks,
-alex

---

### Post by spd106 on 2007-01-18
I think you probably have an atheros based card, in which case your card should have an interface called ath0, the wifi0 also belongs to it. You can check this by running **lspci** and **sudo lshw -C network** at a terminal.

This card should just work, make sure that you have the linux-restricted-modules-2.6.17-10-generic package installed, you can check this in System -> Admin -> Synaptic Package Manager.

For easy connection you could install [network manager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"), it's not without problems, but most people find it useful. Sometimes it can have trouble finding non-broadcasting APs.

---

### Post by ac251404 on 2007-01-18
Well I ran the 'lshc -C network' and it showed my wireless and ethernet interface. The wireless card is an Cisco AIRONET 802.11b and it is shown at network:0.
The odd part is that is showing it as DISABLED when in the System > Admin > Networking application it is showing it as enabled. However I do not have the linux-restricted package installed so that could be the problem. Weird that it would work *sometimes* though. I guess I will try getting that package when I get home and can plug in an ethernet cable. Thanks for the help!

---

### Post by ac251404 on 2007-01-18
well now i cannot get either interface enabled, ethernet or wifi. In the network settings they say enabled but lshc shows them as disabled. I cant get any connection whatsoever. Is there any way to start the devices from the terminal where I can get some output or something?

thanks

---

### Post by spd106 on 2007-01-19
Try **ifconfig** at terminal to give you more information and **iwconfig** for wireless specific details. Can you also say what the lshw command has for the driver.

You should be able to bring up the interfaces manually by issuing **sudo ifup eth0** , or if that doesn't work **sudo ifconfig eth0 up**.

---

### Post by ac251404 on 2007-01-19
Okay Im going to give the outputs of those commands but bear with me cause I had to type them all out since I have no way of getting the text off my laptop.

**lshw -C network**
```

*-network:0 DISABLED
      description: Wireless interface
      product: Cisco Aironet Wireless 802.11b
      vendor: AIRONET Wireless Communications
      physical id: 2
      bus info: pci@02:02.0
      logical name: eth0
      version: 00
      serial:   *dont think it matters*
      width: 32 bits
      clock: 33mhz
      capabilities: bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=airo multicast=yes wireless=IEEE 802.11-DS
      resources: *a lot of numbers i dont have time to type right now*
*-network:1 DISABLED
      description: Ethernet interface
     product: 82801DB PRO/100 VE (MOB) Ethernet Controller
      vendor: intel corp
      physical id: 8
      bus info: pci@02:08.0
      logical name: eth1
      version: 81
      serial: ****
      width: 32 bits
      clock: 33mhz
      capabilities: *same as network0*
      config: broadcast=yes driver=e100 multicast=yes
      resources: ****

```

I have to go for a little bit but I will try to edit in the rest later. Let me know if what I have here so far tells you anything. Also using **ifup eth0** made my wireless get a signal (94%) but still no connection.

---

### Post by spd106 on 2007-01-19
You don't need the restricted-modules package as your driver is not in that package. 

Try looking through this thread for some ideas [http://ubuntuforums.org/showthread.php?t=315236](http://ubuntuforums.org/showthread.php?t=315236)

---

