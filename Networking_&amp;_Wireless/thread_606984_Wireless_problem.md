---
title: "Wireless problem"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Luna.jp on 2007-11-08
I haven't ever gotten my wireless to work on my Dell D610. I've read that the Intel card should work out of the box, but mine isn't in System>Network.
Same problem as here: [http://ubuntuforums.org/showthread.php?t=110493](http://ubuntuforums.org/showthread.php?t=110493)

Can anyone help in this issue?

lshw -C network

```

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:d6:04:e3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72.1 duplex=full firmware=5751-v3.29a ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dfdf0000-dfdfffff irq:16

```

lspci -nn

```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]

```

dmesg | grep ipw

```

[  144.064000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1
[  144.064000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  294.612000] ipw2200: Unknown parameter `rtap_iface'
```

Iwconif comes back as "Lo" & "eth0" : No wirelwss extensions
& sudo lsmod | grep ipw2200 returns nothing...


I also need help in getting this wireless card to work. Tried everything, need some advice...

---

### Post by Lambert on 2007-11-08
Have you tried this computer with windows or any other OS and have the wireless work.

If you run lshw and don't have any output for the device, basically the device is not seen at all, like it's not connected.

Possible the device is defective or has a bad connection.

---

### Post by mpierce on 2007-11-08
Your card should work out of the box as I have a Dell I9.3K with a similar card.

Do a search on my posts, mpierce as I've described to get the card to work. You have to set it up manually.

Hope this helps...

---

### Post by SpiritIsReality on 2007-11-09
howdy
> Lambert:  Have you tried this computer with windows or any other OS and have the wireless work.did you try windows yet?

[http://www.uluga.ubuntuforums.org/showthread.php?p=2799317](http://www.uluga.ubuntuforums.org/showthread.php?p=2799317)
[http://www.google.ca/search?as_q=Dell+D610&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=Dell+D610&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)
[http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=)
all the best
trails

---

### Post by Luna.jp on 2007-11-09
According to all I've read, this card, ipw2200, should work right out of the box.

When I do
lspci -nn | grep Network

I get nothing which tells me that the wireless card isn't even being read. I guess I have to try in windows first, then I'll get to you on what I've discovered.
Thank you.

---

### Post by MSchenker on 2007-11-09
Let me jump in here as well...

For a while, I had Kubuntu on my desktop and Windows XP on my laptop.  My laptop has an Intel Pro Wireless 2200 card, and it was working great.  I was able to connect to the laptop and share files.

Lat night, I installed Kubuntu on my laptop, and suddenly my wireless card doesn't work!

Can someone please tell me what I need to do to get the card working again on my laptop?

Thanks,
Matt

---

### Post by MSchenker on 2007-11-09
Everyone,
OK, I just found a simple fix.  When I went in and set the I address to match the IP address on my desktop, it worked!  Now I have Internet access from my laptop.

One problem I still have is that Adept does not seem to work.  Any packages that are not already installed are ghosted out.

Matt

---

### Post by MSchenker on 2007-11-09
Follow-up note: I restarted my laptop, and now I am able to get Internet access, and I can access the repositories through the wireless connection.
Matt

---

### Post by Luna.jp on 2007-11-09
My Follow-Up:

Well, instead of installing Windows I talked to the person who sold it to me. The government. According to them, the wireless was working the day I came and bought it. They cleaned out windows and gave it to me so everything is working as it should be...

So I guess my question is...
How do I get the kernel to recognize that I have a wireless card?
How exactly do I know which make and model I have if the OS doesn't even know I have a wireless card? ( internal )
Should I try windows anyways?

---

### Post by SpiritIsReality on 2007-11-09
howdy
any help here?
[http://www.dell.com/content/products/productdetails.aspx/latit_d610?c=us&cs=28&l=en&s=dfb](http://www.dell.com/content/products/productdetails.aspx/latit_d610?c=us&cs=28&l=en&s=dfb)
It looks like that's a list of possible wireless cards that dell puts into Latitude D610 Notebooks? How about trying a Knoppix live cd and see if it recognizes your wireless card? It's supposed to be pretty good at that. You could try your hardware discovery commands to see?
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
[http://unit.aist.go.jp/itri/knoppix/index-en.html](http://unit.aist.go.jp/itri/knoppix/index-en.html)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+Dell+D610&btnG=Google+Search&meta=]("http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+Dell+D610&btnG=Google+Search&meta=")
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+Latitude+D610&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+Latitude+D610&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=Dell+Latitude+D610&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=Dell+Latitude+D610&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=Dell+Latitude+D610&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=Dell+Latitude+D610&btnG=Google+Search&meta=)
trails

---

### Post by Luna.jp on 2007-11-11
Hello All.
Well, I managed to figure out the problem. And you'll be upset to know that right after I made the purchase of this laptop, the government not only wipes the hard drive clean, but they also remove the bluetooth adapter and wireless adapter because of crypto reasons.

Sad to say, I didn't check this before they gave it to me. So for all the help offered, thank you very much for taking time out to look at this issue.

I am in route to purchase a IPW2200 so hopefully, after an install, it works out of the box.

Thank you all!

---

