---
title: "Wireless not working in Ubuntu 13.01 64 bit"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by garyevansbtc@gmail.com on 2013-11-16
Hi Forum: My first post but not the first time I've received help from this forum. Thanks!

Recently I purchased a Toshiba Satellite S75D-7272, A10-5750, that came with Windows 8. It has a 1T HD and is my first experience with UEFI partitions. I learned how to get Ubuntu 13.01 64 Bit working and booting but no dual boot yet. 

My primary question is why the wireless does not work. Windows 8 has a soft-key (F12) to turn Wireless On/Off. This does not work with Ubuntu 13.01. The orange light on the front, right, edge of the notebook is ON meaning the wireless is ON (I think). I ran this command to ID the wireless card:
 gary@Duane:~$ sudo lshw -class network  

 *-network  
 description: Ethernet interface  
 product: AR8162 Fast Ethernet  
 vendor: Qualcomm Atheros 


 and this:
 

 gary@Duane:~$ lspci -nn | grep 0200  

 01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)  
 

 Ubuntu versions as far back as 10 have worked flawlessly with my recent Toshiba Notebook. I'm not finding links that work with this new Notebook. Suggestions appreciated.

---

### Post by chili555 on 2013-11-16
> gary@Duane:~$ lspci -nn | grep 0200

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10) That's ethernet, not wireless. Let's see:```
lspci -nn | grep 0280
```

---

### Post by garyevansbtc@gmail.com on 2013-11-17
Hi chili555: Thanks for responding. 

My bad . . . but I've been checking my Notebook and found this reference on a label stuck to the bottom:

Radio Device: RTL8188EE

Is this Realtek (RT) and the part number needed to find a driver?

---

### Post by garyevansbtc@gmail.com on 2013-11-17
Hi Chili555:

Now I have this, which answers part of my question:

gary@Duane:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)
gary@Duane:~$ 


Thanks.

---

### Post by Bucky Ball on 2013-11-17
Please post the full output of:

```
sudo lshw -C network
```

Thanks.

---

### Post by chili555 on 2013-11-17
Just for the benefit of you and the searchers, the pci.id or usb.id, in your case 10ec:8179, is everything! Once we have that, Google finds us this brilliant piece of work: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

Hook up the ethernet and copy and paste all the steps and you should be all set, however, if you get stuck, please post back and I'll be happy to help.

---

### Post by garyevansbtc@gmail.com on 2013-11-17
Hi Buck Ball and Chili555:

Here is the data you requested:

   gary@Duane:~$     sudo lshw -C network 
 [sudo] password for gary:  
   *-network                
        description: Ethernet interface 
        product: AR8162 Fast Ethernet 
        vendor: Qualcomm Atheros 
        physical id: 0 
        bus info: pci@0000:01:00.0 
        logical name: eth0 
        version: 10 
        serial: 08:9e:01:b7:87:9a 
        size: 100Mbit/s 
        capacity: 100Mbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s 
        resources: irq:16 memory:f0100000-f013ffff ioport:3000(size=128) 
   *-network UNCLAIMED 
        description: Network controller 
        product: Realtek Semiconductor Co., Ltd. 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        version: 01 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list 
        configuration: latency=0 
        resources: ioport:2000(size=256) memory:f0000000-f0003fff 
 gary@Duane:~$  

Thanks.

---

### Post by chili555 on 2013-11-17
Your ethernet is hooked up and working. Please proceed as above. You should have wireless in just a few minutes!

---

### Post by garyevansbtc@gmail.com on 2013-11-17
Yaaaaaa!!!!! It works! Thank you, thank you, thank you! You are the greatest!!! :-)

---

### Post by chili555 on 2013-11-17
> **garyevansbtc@gmail.com said:**
> Yaaaaaa!!!!! It works! Thank you, thank you, thank you! You are the greatest!!! :-)Awesome! Glad it's working.

Please make note of the final part of my post:> You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:....And also please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Have fun!!

---

### Post by Bucky Ball on 2013-11-17
> **chili555 said:**
> Awesome! Glad it's working.
... please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Have fun!!

+1.

---

