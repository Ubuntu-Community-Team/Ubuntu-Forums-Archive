---
title: "Internet Connection Sharing How-to needed"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by bolucpap on 2009-04-14
Hello all,
I don't have access to a wireless router, so in order to connect to the internet using my notebook from the living room, I plug in a USB wireless dongle to my Windows Desktop PC in my study, set up a ad hoc (non infrstructure) network, then using the internet connection sharing tab in the properties page of the adapter, set it up so that my notebook uses the PC as a gateway to access the internet. So far I've managed to get it working pretty flawlessly. 

However, I recently installed Ubuntu (Intrepid) on my desktop PC. At the moment I dual boot, switching back to Windows whenever I need to use the wireless Internet connection. Needless to say, that's a pain. How can I make the same arrangement in Intrepid? I tried fiddling around with the Network Manager, but got no results. A step by step how-to would be much appreciated.

Thanks in advance.

---

### Post by TenPlus1 on 2009-04-14
All I did was setup my wireless card in Ubuntu so it has the same IP, subnet, essid and password as before in Windows, then installed Firestarter in which I turned ON 'Enable Internet Connection Sharing', set my Internet Device and Local Network Device (wireless) and Added a rule in the policy tab to enable any external IP's to connect.  Reboot and it should work...

---

### Post by nandemonai on 2009-04-14
Firestarter is probably the easiest way. Another alternative would be [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370).

---

### Post by Michael.Godawski on 2009-04-14
Hi bolucpap,

let's check if your usb dongle is recognized by Ubuntu in the first place.
Perhaps, as the posters above already stated, only small changes are necessary.  

Please open the terminal  and run these commands:

```
iwconfig
lsusb
sudo iwlist scan
sudo lshw -C network
```

and post the outputs here.

---

### Post by bolucpap on 2009-04-14
It is recognized, I can see the neighbors' wireless networks and connect to unsecured ones. I am at work now, so running those commands won't be possible before 6 hours or so.

---

### Post by bolucpap on 2009-04-15
After I got home, I twiddled with the network manager a bit to create and set up an adhoc wireless connection. It is erratic at best, sometimes the connection shows up, sometimes it doesn't. Once I had it up, I followed the instructions in nandemonai's link except for the final edit of the configuration file and the reboot. I got the desired result relatively quickly. However, when I rebooted the Desktop PC (without the edit). I totally lost all wired network connectivity (ping requests got an error). I then uninstalled both dnsmasq and ipmasq and got connectivity back.

In conclusion, this is the right track, but with some glitches that I am confident can be ironed out. Thanks for all the quick replies.

---

### Post by bolucpap on 2009-04-15
I retraced my steps, doing all the steps in the linked how-to, then edited the sysctl file to include ipforwarding. The laptop was able to connect through the Desktop PC to the Internet just fine. I rebooted the Desktop again, and once again I lost all wired connectivity. After some fiddling I discovered doing ```
sudo /etc/init.d/ipmasq start
``` did the trick. So what I want to know is this: What should I edit so that the ipmasq starts everytime the PC boots up?

Thanks in advance.

---

### Post by freak42 on 2009-04-15
you can also try something different: namely replacing the gnome network manager with wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)), it has an option to create an ad-hoc wireless network with a internet-connection sharing checkbox.. might be worth a try.

hth

---

### Post by bolucpap on 2009-04-15
Yes, I will try wicd sometime soon, since the network manager has been giving me so much grief lately. I will first check out if the problems have been ironed out in Jaunty first, though.

---

### Post by freak42 on 2009-04-15
I've heard wicd is in the jaunty repos, so installing wicd might be even easier in jaunty than hardy.

---

