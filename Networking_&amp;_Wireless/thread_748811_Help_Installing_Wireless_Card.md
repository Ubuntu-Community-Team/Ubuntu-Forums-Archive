---
title: "Help Installing Wireless Card"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by whitedragon551 on 2008-04-07
I reinstalled Ubuntu 64-bit after a while of not having it installed. Im dual booting with Vista 64-bit on a laptop. Under the restricted drivers manager it says I need BCM43XX so I downloaded it in Vista and transfered it to Ubuntu. I cant hook up to the router via ethernet wire. Its a wireless hot spot. Also the default connection thing that is on the bar at the top by default disappeared. I think I accidentally closed it. How do I get it back?

---

### Post by dstew on 2008-04-08
> I need BCM43XX so I downloaded it in Vista and transfered it to Ubuntu.Did you get the Ubuntu package and install it? Which package did you get? Did it work for you? You can get packages and updates off-line using the [nonetdebs]("http://nonetdebs.homeip.net/") service.

The thing on the top bar is the Network Manager applet. To get it back, try```
sudo /usr/sbin/NetworkManager restart
```You should be able to configure your network in the System --> Administration --> Network window also.

---

### Post by whitedragon551 on 2008-04-08
I downloaded the latest BCM43xx-fwcutter.deb package and installed it with the debian installer. I also downloaded some other file because I was offline and put that file in my documents and when I used the restricted drivers it asked to install the driver or get it offline. I picked the file I put in my documents and rebooted and it didnt work. It said connecting for about 15 minutes and then never connected.

---

### Post by dstew on 2008-04-08
Post the output of```
lspci
iwconfig
```

---

