---
title: "zonbu min running hardy 8.04"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by netipot on 2010-04-06
I bought a zonbu mini about 2 years ago and zonbu seems to have disappeared. Since working in zombu os is fruitless I installed ubuntu 8.04 and it works very well, in fact it is faster than zonbu os. However there is one thing that is not working and that is that the eBOX-4854/4864 will not mount a usb thumb drive. My wireless keyboard and mouse work fine and even an external hard drive and cd drive will work. I want to know if this is a problem in the software or perhaps in the BIOS. There is very little storage and working with thumb drives would be great.

---

### Post by Kakers on 2010-04-06
Might just be a problem with compatibility, you could always try installing 9.10.

Also if you think 8.04 runs fast, well from my experience on installing on multiple systems, 9.04+ should run even faster.

---

### Post by netipot on 2010-04-06
I first tried jaunty remix because I had it on a usb from installing it on my netbook and I had real issues with it, one being that the curser was invisible but it was there, you would see it light up buttons. I did change settings in the bios to get it to boot but I have since played with it and nothing.

---

### Post by netipot on 2010-04-06
I've been talking to a very helpful man, at wdlsystems.com, a distributor for the ebox in the US. He told me to try another usb drive. I was using a sandisk cruzer. I tried a pny attache and it worked. OK I can work with this fine. Not really because when I went to download photos from my Lumix camera, ubuntu could see it but was unable to mount it. I thought I could work around this too so I took out the sd card put it in the card reader, but this also failed to mount. Is it ubuntu or the ebox? The man at wdl systems said my model ebox had usb issues, but I saw on one forum that someone installed windows xp and had no problems. Perhaps all the did was surf the net. I can get  a bigger cf card, which is the drive for this thing. The one it came with is only 4GB.... so 8 or 16GB would give me some room to store files but I do need to use my camera.

---

### Post by netipot on 2010-04-14
Well I eventually found the info I needed at [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) and was able to mount usb sticks and sd cards. Thank you ubuntu.

---

### Post by boost915 on 2010-05-15
Can you tell me where in the bios you were able to enable USB booting. I can get into the bios on the Zonbu mini, but can't find any way to enable USB booting.

Thanks.

---

### Post by netipot on 2010-05-16
> **boost915 said:**
> Can you tell me where in the bios you were able to enable USB booting. I can get into the bios on the Zonbu mini, but can't find any way to enable USB booting.

Thanks.

Sure, do you have the ebox-4 manual? I find it very helpful. I downloaded it from the ebox website I think. Also go to zonbu documentation [http://www.zonbu.com/doc/doku.php?do=index&id=other_distributions](http://www.zonbu.com/doc/doku.php?do=index&id=other_distributions) look under other distributions, in there is how to boot from USB drive. I found it is a good idea to insert a usb drive before turning on the mini because then you are sure to see it listed when you set up your boot preference. Also in the zonbu documentation it says Enable Port 64/60 Emulation and disable BIOS EHCI  Hand-Off, which I did and then after I installed ubuntu I went back into the bios  to restore the BIOS defaults. I chose optimal over failsafe defaults.
You will love ubuntu. I am using lucid lynx 10.04 and it is great, so fast and no issues yet.

---

### Post by boost915 on 2010-05-17
I got 10.04 to work on the Zonbu mini. Thanks for the information.

This is with a wired network connection. So far haven't got the wireless to work.

ifconfig is not showing a wlan0 connection.

Here's the output of sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth0
       version: 10
       serial: 44:4d:50:02:0b:5f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:d800(size=256) memory:feaffc00-feaffcff
  *-network:1 UNCLAIMED
       description: Network controller
       product: VIA VT6655 WiFi Adapter, 802.11a/b/g
       vendor: VIA Technologies, Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32
       resources: memory:feaff400-feaff4ff ioport:d000(size=256)

Any ideas?
Thanks.

---

### Post by netipot on 2010-05-17
> **boost915 said:**
> I got 10.04 to work on the Zonbu mini. Thanks for the information.

This is with a wired network connection. So far haven't got the wireless to work.

ifconfig is not showing a wlan0 connection.

Here's the output of sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth0
       version: 10
       serial: 44:4d:50:02:0b:5f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:d800(size=256) memory:feaffc00-feaffcff
  *-network:1 UNCLAIMED
       description: Network controller
       product: VIA VT6655 WiFi Adapter, 802.11a/b/g
       vendor: VIA Technologies, Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32
       resources: memory:feaff400-feaff4ff ioport:d000(size=256)

Any ideas?
Thanks.

My zonbu mini does not have wireless so I don't have your problem. I did have a similar problem with another computer. I see that you have an "unclaimed" message so you need to install a driver. Under "unclaimed" it looks like the product & vendor. I used NDISWrapper which had to be installed. Check out your help guide on the top panel and go to wireless troubleshooting,...it is pretty much explained there. Now finding your driver?...I guess you can google it. Also I got a lot of help from this guy at WDL systems that sells the e-mini in the US. His email is 
Donnie Springfield  <donnie@wdlsystems.com> He might help with the driver. This is a little 
off subject but I bought an 8gb CF card from them so the mini has a little more memory. 
I think the new card is a little faster then my old one. My mini is 3 years old. I kind of
wish I got the 16gb card. Anyway if you want another card he will steer you to one that will 
work with the mini. It is also nice to be able to switch out my new card for the old one 
which still has the zonbu OS on it.

---

### Post by netipot on 2011-11-22
Just as an update to this thread, I thought I would let you know about other distros I have been working with. I decided that something more lightweight might be better suited to the mini. I tried siltaz & macpup and though they work fine & are fast I was not happy with them. Elementary I didn't think was light enough so I tried lubuntu. I think it's very good.....better than the LXDE versions of mint & opensuse, but wattos is the best of the bunch and I like their forum. I think LXDE is great and it's light......the Zonbu runs pretty fast on it but then I tried bodhi Wow! Enlightenment IS FAST! It's pretty to..... maybe too much bling,.. but it is hands down fast. I love the simplicity of LXDE but bodhi is what you need to get the most out of this little machine.

---

