---
title: "wifi antenna not detected"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by adobrakic on 2010-08-23
Hey guys, I recently got a [HP P6540FY](http://www.bestbuy.com/site/HP+Pavilion+p6540fy+Desktop+%26+23%22+LCD+Monitor+Package/9999133000050033.p?id=pcmprd133000050033&skuId=9999133000050033) desktop computer. I want to install 500GB of the 1TB partition, but when I try the live-cd, no networks show up under the network manager. I'm on Windows 7 now, so I can post any additional information if necessary. Thanks.

---

### Post by Guilden_NL on 2010-08-23
I have a boatload of HPs (I work for them) and haven't had any problems with Lucid finding the networking, WiFi or cabled when upgrading.  

There is a problem with a new Lucid install though. The problem is that due to an oversight, Lucid/10.04 does not have fakeroot on the install CD so in order to get the wifi going you will need to connect to a hard-wire network cable to get the files you need. Without fakeroot neither the proprietary driver or NDISWrapper will work.

---

### Post by adobrakic on 2010-08-23
Well that's extremely inconvenient. I'll just bring my modem up here for a few minutes before installing Linux, then.

To be clear, the name of the download i need to find is "fakeroot"?

--edit--

I'm on live-cd right now, brought my modem upstairs. I installed fakeroot, but I'm not sure where to go from here. I updated Ubuntu, and now in network manager, under Wireless Networks it says, "Device not ready." Any ideas?

---

### Post by stoogiebuncho on 2010-08-23
While you're connected to the internet through your wired connection, try going to System > Admistration > Hardware drivers and see if anything shows up there.  Sometimes you have to restart before your driver will pop up.

---

### Post by adobrakic on 2010-08-23
I tried Hardware Drivers already, all that comes up is my graphics card. I figured I'd have to reboot, so I went ahead and began installing Linux on the second partition. I'll report back once it's installed and I'm off the live-cd, since it might work after installing and rebooting.

---

### Post by adobrakic on 2010-08-23
okay, i'm on ubuntu right now. the network still isnt showing up, and nothing under Hardware Drivers either.

---

### Post by Guilden_NL on 2010-08-24
It won't show up under Hardware Drivers as it doesn't need proprietary drivers.  

Let's go back to the beginning - you installed Ubuntu from the Live CD?  You mentioned that you "updated it" - what do you mean? Which steps did you take?  The latest versions of LiveCD apparently have fakeroot, but I can't vouch for that since I've upgraded all of my systems quite a while ago.

Try this while plugged into the network:
[LIST=1]
[*] sudo apt-get remove --purge bcmwl-modaliases
[*] sudo apt-get install bcmwl-modaliases broadcom-sta-common
[*] Reboot
[/LIST]

Good lucK! Hopefully this will properly install the Broadcom driver and will get your WiFi going.

---

