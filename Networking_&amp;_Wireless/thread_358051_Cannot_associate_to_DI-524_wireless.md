---
title: "Cannot associate to DI-524 wireless"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by Neatchee on 2007-02-10
Acer Aspire 5003WLCi running x86_64 Ubuntu 6.10 (manual upgrade to kernel 2.6.19.1)

Followed all instructions for installing ndiswrapper with the proper x64 bcmwl5 drivers (pulled directly from Acer's ftp)

On boot, on first modprobe of ndiswrapper, or when enabling the device through the Networking control panel the device will automatically connect to any non-secured router in the area EXCEPT my own D-Link DI-524.  I was originally trying to connect using WEP, but now I'll settle for any connection at all.  The device refuses to associate.

I've tried using Ubuntu's built in network manager, Kwlan, and command line configuration, but nothing seems to be working.  Any help would be greatly appreciate.

If you need any additional info, such as logs, configurations, steps taken, or hardware setup info, don't hesitate to ask.  Thank you in advance!

---

### Post by jan247 on 2007-02-10
Do you have DHCP on from your router?

---

### Post by Neatchee on 2007-02-11
Yes.  Even if I statically assign an IP, it still won't associate.  The router shows up in an iwlist scan it just won't...freaking....associate!  ARGH! *head...on...keyboard!*

---

### Post by mike78_at on 2007-02-25
I can't help you, I just can assure you: you are not alone! I also have setup ndiswrapper with the bcmwl5-driver (directly from Dell in this case, as I have a Latitude X300). NOTHING works: not unencrypted, not WEP, not any of the flavours of WPA (although the network manager shows me the network and also asks for the correct authentication type). The router just shows me messages like that it disassociated me "because WPA retey failed"...

The router works with the original bcm43xx-driver (only WEP not WPA), but horribly slow and unreliable. I consider Ubuntu to be superior to Windows in almost all areas, but the wireless setup never works for me and is not better or easier than when I first tried it with Gentoo several years ago.

If anyone has a hint, I also would greatly appreciate it.

---

### Post by mike78_at on 2007-02-25
A small update: for example with WPA1-Personal and AES I actually get a connection. The IP-address is correctly set with DHCP and the knetworkmanager shows me that I am connected. But: I still can't even ping the router, I always get a "Destination host unreachable". The route-command returns exactly the same configuration as when I connect with a cable (which works), only with the other interface-name (eth1 instead of eth0). So IMHO it should work, but it doesn't. I officially give up now, after spending more than 10 hours on this... :-(

---

### Post by Neatchee on 2007-03-20
I've managed to get everything working smoothly by enabling WPA-PSK on the router, installing wpasupplicant (sudo apt-get install wpasupplicant) and a little application called Wicd ([http://compwiz18.blackhole.cx/wicd/wb](http://compwiz18.blackhole.cx/wicd/wb))  The utility is very complete and worked on the first go.  Supports several WPAsupplicant drivers as well, so it should work no matter what NIC you're using.  I highly recommend you give it a shot.

---

### Post by nezus on 2007-07-21
I've found a so called workaround: start "iwevent", then try to connect. God knows why, but it worked for me.

The other weired thing is that my computer has no problem connecting to my other Access Point (Edimax EW7203APg) without "iwevent". For some reason the "iwevent" workaround is only required for connecting to DI-524.

After the connection is established, stopping the "iwevent" does not drop it - "iwevent" is only required for establishing the connection.

I used WPA2 AES PSK for connecting to both wireless devices.

Hope it helps.

---

### Post by mike78_at on 2007-08-26
> **nezus said:**
> I've found a so called workaround: start "iwevent", then try to connect. God knows why, but it worked for me.

The other weired thing is that my computer has no problem connecting to my other Access Point (Edimax EW7203APg) without "iwevent". For some reason the "iwevent" workaround is only required for connecting to DI-524.

After the connection is established, stopping the "iwevent" does not drop it - "iwevent" is only required for establishing the connection.

I used WPA2 AES PSK for connecting to both wireless devices.

Hope it helps.

This is not possible! ;-) I can't believe it, I have finally WLAN on my Ubuntu! You have made my day! Thanks a lot!

---

