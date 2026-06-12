---
title: "Can't connect to any Wi-Fi Network After laptop died."
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by Cody_Morgan on 2015-11-11
OK, I left my laptop charger when I visited home. My C720 running Xubuntu 14.04 finally shutdown due to a dead battery. I went a couple weeks before getting my charger. When I turned it on, I couldn't connect to my school's WPA2 Enterprise with PEAP. 

I had this issue before, so I tried the usual fix, deleting resolv.conf 

This didn't work, and I tried connecting to my phone's hotspot that uses WPA2 Personal. It will not connect. I then tried using dpkg to reconfigure resolv.conf. that also did not work. 

What happens is:
1. Open up Network Manager
2. Select network
3. Enter credentials
4. Network icon spins and spins for hours. 

I've tried to delete these networks and even create them manually. Nothing works. 

Then I noticed today that my date and time was off. It was set to like July 9th 2160.

What could have caused this? What can I do to fix it? Can I fix it without reinstalling? 

Thank you!

---

### Post by tgalati4 on 2015-11-11
Welcome to the forums.

The on-board button battery is dead.  The battery keeps the clock going when your main battery is dead.  You can set the approximate time by booting into BIOS.  The correct time gets set when you connect to the network and synchronize with the national time servers.  It's possible that the wrong time was messing up your network connection.

Enterprise WPA2 can be tricky to connect.  [http://askubuntu.com/questions/279762/cant-connect-to-wpa2-enterprise-peap](http://askubuntu.com/questions/279762/cant-connect-to-wpa2-enterprise-peap)

Work with your school's IT staff to get specific settings.  Since it worked previously, I presume the wireless card is working OK.

---

### Post by Cody_Morgan on 2015-11-11
Is it possible to change the time from the terminal? I'm not sure how to boot into the bios on a C720. In fact, I may have to remove the bios write-lock screw on the inside. Last year I worked hours with OIT to try to get it too connect to their network. I later found the solution on my own, I believe I have all the correct settings. No one here knows "how to linux."

---

### Post by matt_symes on 2015-11-11
Hi

> Is it possible to change the time from the terminal?

Look at the man page for

```
hwclock
```

If your system time is correct the try something like

```
sudo hwclock -w
```

but do check out the man page first.

Whether it'll work if the BIOS is write protected is anybody's guess though.

Kind regards

---

### Post by Cody_Morgan on 2015-11-11
Thank you. I do think that my button battery should have lasted longer than 1.5 years, however. I'll try this and get back to you.

---

### Post by Cody_Morgan on 2015-11-11
```
sudo hwclock -r
```

This showed me that my hardware clock was correct. 

So I set my system clock with ```
sudo hwclock -s
```

Now I'm able to connect. Thank you all!

---

### Post by tgalati4 on 2015-11-12
It is possible that your laptop has a rechargeable button battery, and they don't last very long.  You would think that they would last 10 years, but cheap ones get internal corrosion and just die.  Keeping your main battery charged will keep the correct time and will help with network connectivity.  Glad you got it figured out.

---

