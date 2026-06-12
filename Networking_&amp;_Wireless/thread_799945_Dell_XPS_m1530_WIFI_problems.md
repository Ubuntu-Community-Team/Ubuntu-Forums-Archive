---
title: "Dell XPS m1530 WIFI problems"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by sleepyenglish on 2008-05-19
I just installed hardy on my dell xps m1530 and the wifi is not working or showing up in the drop down list as an option. I have connected to the net via a network cable and fully updated, the wifi is switched on via my laptop and still no luck. I googled around and found that the wifi card/chip is an Intel 4965, can any give me any advice?

Thanks

---

### Post by sleepyenglish on 2008-05-19
I found the below page via google and he stated

> Wireless networking

 Works out-of-the-box. Click the networking icon in the top right of the screen, select my WiFi network and enter the network password. I'm using WPA2 encryption.

when testing 8.04 on the exact same laptop, so does this mean im missing something?

[http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

---

### Post by sleepyenglish on 2008-05-20
Can no one please help me?

I reinstalled vista just to confirm the card is working and it works just fine but after i reinstalled hardy the exact same problem no wifi is detected.

Is there any way i can install the driver required manually?

---

### Post by sleepyenglish on 2008-05-20
I tried fedora 9 and the same problem persists, its like i don't even have wifi capabilities. I hate to say but i might have to switch back to vista :-(

---

### Post by Ayuthia on 2008-05-20
Have you tried going to the terminal and checking to see if you can see any wireless connections:
```
sudo iwlist scan
```

EDIT:
By the way, make sure that you are not connected through the wired connection or else you might still not be able to connect.

---

### Post by sleepyenglish on 2008-05-20
I did as you suggested and i got the below, thanks for the reply by the way.


lo        Interface doesn't support scanning

eth0       Interface doesn't support scanning

---

### Post by Ayuthia on 2008-05-20
> **sleepyenglish said:**
> I did as you suggested and i got the below, thanks for the reply by the way.


lo        Interface doesn't support scanning

eth0       Interface doesn't support scanning

A silly question--is roaming enabled on Network Manager?

Can you post your lshw -C network?  Also, what happens when you do ```
sudo ifconfig wlan0 up
```

---

### Post by sleepyenglish on 2008-05-20
There is no option to roam.

-----------

> wlan0:  ERROR while getting interface flags: No such device

------------

Concerning lshw -C network i just get some output options, im not sure what i have to do with them.

---

### Post by MickSulley on 2008-05-23
Hi,
I have a M1710 with exactly the problem described.  It used to work until I did a clean install of Hardy, now no wireless.
output from my  lshw -C network is - 

  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:dc:e7:14
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.19 ip=192.168.0.3 latency=0 module=tg3 multicast=yes

From other info I have found I think the UNCLAIMED bit means that the driver is not installed correctly.  I have tried follow the info at [http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095) but it does not seem to work.  Can anyone help please?

---

### Post by lviggiani on 2009-04-22
Hi Guys,
I have the same problem with XPS M1530 and Kubuntu 9.04 RC (fresh installation)
The blue led sidewise the bluetooth led showing that the wireless in active doesn't illuminate too.

The funny thing is that wireless works 100% with UBUNTU (with gnome NetworkManager Applet) 9.04 rc upgrading from 8.10

The doubt come: is it a problem related to KDE network manager is it related to a fresh installation vs upgrading from 8.10?

---

### Post by &gt;hankim&lt; on 2011-09-16
I leave you there this link that seems to solve the problem, it hasn't worked for me as I don't know how to install with make install from the console yet, if anyone tries it and works for him, I beg please send me a clue! thx! I'll try to research anyway but it always makes things far complicated... 

[http://debii.curtin.edu.au/~pedram/thoughts/linux/80-howto-solve-dell-xps-m1330-freeze-problem-on-ubuntu-810]("http://debii.curtin.edu.au/%7Epedram/thoughts/linux/80-howto-solve-dell-xps-m1330-freeze-problem-on-ubuntu-810")

farewell!

EDIT> P.S. ; It sholud work for[COLOR=Red] M1530[/COLOR] and [COLOR=Red]M1330[/COLOR] models.

---

