---
title: "Deluge &amp; Pidgin Kill Wireless Connection"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by mav5150 on 2008-03-15
So I don't know for sure if this is the right section for my problem, but I figured I would start here and see where it takes me. So I've been using Ubuntu for a couple months now (and loving it) but the only problem I've been having lately is with Pidgin and Deluge. Whenever I launch these programs I end up loosing my wireless connection after a few minutes and the only way to get myself reconnected is to restart my computer. I don't know where the really look to solve this so I was wondering if anyone else has had this problem or would know how to fix it. At first I thought it was the hidden "HTTP Cache Cleaner" that would launch whenever I used KTorrent, so I uninstalled it and starting using Deluge instead. It was working fine for a few days, but now when I launch it I seem to loose my connection every time. I just setup Pidgin so I could use it and after a few minutes I lost my connection again. So any help would be great. Thanks

---

### Post by pytheas22 on 2008-03-15
First, what kind of wireless card do you have and what driver are you using for it?  I think there's a good chance that the problem could lie there, as the card may not be able to handle certain kinds of traffic.

Second, a way to figure out what's wrong might be to try using Ethereal (which may be renamed Wireshark?), a packet sniffer and analysis tool that you can install from Synaptic.  You can look at the network traffic and see if any particular kind of packet is being sent or received at the time the connection is dropped.  This will require some work, so it might be easier to try troubleshooting the wireless driver first, but this could help if that doesn't.

---

### Post by mav5150 on 2008-03-15
I'm using the Linksys WUSB54GC and here's the output from the ndiswrapper commands: 

```
mavrik@mavrik-desktop:~$ ndiswrapper -l
rt73 : driver installed
        device (13B1:0020) present (alternate driver: rt73usb)
mavrik@mavrik-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko
version:        1.48
vermagic:       2.6.22-14-generic SMP mod_unload 586 
mavrik@mavrik-desktop:~$ 

```

I'm pretty sure the wireless usb drive could handle this type of traffice, since I was using azureus on windows for a while downloading torrents and was using Pidgin for a couple months on the windows system as well without any complications. Thanks again for the help, I'll look into the packet sniffers as well to see if I can find something.

---

### Post by pytheas22 on 2008-03-15
I've had strange problems with ndiswrapper in the past.  I had one card with some kind of Broadcom chipset (before there were native drivers) that would crash every time I visited certain web pages.  Otherwise the card worked great.  I never figured it out and just bought a card with native Linux support once I switched to Linux full-time.  Your problem could be similar.

According to this thread [http://ubuntuforums.org/showthread.php?t=646687](http://ubuntuforums.org/showthread.php?t=646687), your card should work out-of-the-box, using a native driver, in Gutsy.  Are you using an earlier version of Ubuntu?  If you are, try at least burning a Gutsy live CD and see if your wireless works while running that.

Otherwise, you could try installing different versions of the Windows drivers for your card in ndiswrapper.  If the card's flaky behavior is caused by a bad version of the driver that ndiswrapper is using, this would solve it.

---

### Post by mav5150 on 2008-03-18
Okay thanks Pytheas22, I don't know how I fixed it but it apparently is working now. I checked for an updated driver and the current driver I had was the most up to date driver, and when I tried running from the live cd, I couldn't get the wireless network to stay online for more than 10-20 minutes before it would die. So I rebooted my computer and the Network Manager in the top right corner didn't even show a connection so I unplugged the USB Adapter, waited a few minutes and plugged it back in and everything worked fine. I was able to use Deluge, which worked all night but when I woke up in the morning my internet was gone again. The network manager showed it was connected, but I couldn't get into any web page and nothing was working again, so I think it has something to do with the network manager and not the USB Adapter itself. So tonight I'm going to look for some other Wireless Network finder and see if that changes anything. Thanks again for your help

---

### Post by pytheas22 on 2008-03-19
glad it seems to be working better.  Network Manager is notoriously unstable (I think it's not so much NM's fault as the lack of standardization across the wireless drivers it has to deal with, but the bottom line is that it tends to cause problems).  A lot of people have better luck with wicd, [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/).  I'd give that a try next.

---

### Post by mav5150 on 2008-03-20
Thanks, I'll give it a shot and see how it works.

---

### Post by carlosqueso on 2008-04-22
I had the same problem, both with the native drivers and ndiswrapper. Using naim instead of pidgin for IM seems to help greatly....what could pidgin be doing to mess up NetworkManager or the wireless drivers?

---

### Post by froghunter on 2008-04-30
I also have had issues with pidgin and my wireless. Strange part is that in order to get everything back up and running I have to re-start my router also. I am using a Netgear wirless firewall router, WGT-624 v2 and my wireless card is an Intel/Pro Wireless 2200BG card (actually this is a guess, but I am running a Dell Inspiron 6000). Should this go under some bug post? Here or affiliated with Pidgin. Will try wicd and see how that works. Thanks.

---

### Post by froghunter on 2008-05-06
To add to the complexities of Pidgin causing some issues, I just installed it on my Nokia N800 which runs a linux based OS called [Maemo]("http://maemo.org"), officially this was OS2008. So, I installed Pidgin, which apparently works great on everyone elses N800s, and low and behold, it crashes my router almost immediately, such that my laptop running Hardy can no longer access web pages. Again, solution, reboot router and modem, and uninstall pidgin on N800. Anyone out there know of serious issues with router firmware? (since last post I attempted using a network manager alternative, but with the Intel 2200 BG card, I ran into too many issues, just for Pidgin when meebo works just fine).

---

