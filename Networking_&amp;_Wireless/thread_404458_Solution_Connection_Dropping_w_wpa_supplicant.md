---
title: "Solution: Connection Dropping /w wpa_supplicant"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by skip27 on 2007-04-08
After nearly tearing out all of my hair, I have found a simple and elegant fix for those who are having problems with a wireless connection using WPA. Everything on Google was a deadend, so I thought it would be best to post this and be the first :) (and if I'm not the first, no biggie). Is your connection dropping after a while of inactivity, or does it drop when there have been a few DHCP reassignments in your local network? Do you get something to the tune of this when logging?

```

1175997932.678989: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
1175997933.656542: RX EAPOL from 00:13:46:bb:e2:c0
1175997933.656556: RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 22 8c c8 18 5f 69 bb c7 66 e6 c3 fc c8 50 ae ec 1c 84 77 11 61 3b 5d 85 29 0f b5 8a e7 9d 14 96 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

```

From this point, it should just keep printing that the replay counter did not increase. The solution, is actually quite simple. I'm using a D-Link VDI-624 (The 'V' in the model name comes from Verizion using their FiOS service) but this should work for anyone who has a picky router.

Edit wpa_supplicant.conf or <whatever>.conf and make sure to include these lines in the global area (i.e. ABOVE where you start defining your 'network' in { } braces):

```

eapol_version=1
fast_reauth=0

```

Some routers will simply drop packets from the get-go using eapol_version=2, so make sure it is set to 1. Additionally, some routers will not work with fast_reauth, so make sure to EXPLICITLY disable it (fast_reauth=0), since it comes enabled by default. Does this mean you'll reassociate slowly? No, it really doesn't. My connection is fast, stable, and very reliable. Plus, it works until I tell it to disconnect--the way it should be.

Other suggestions:

**GLOBAL VARIABLES**
```

ap_scan=2

```

**LOCAL VARIABLES (i.e. under 'network')**
```

network={
   scan_ssid=1
   bssid=<whatever it is>
   psk=<use the output from wpa_passphrase>
}

```

You probably don't need to explicitly specify your bssid. I used it while I was troubleshooting, and should be okay to take out. However, since there's no harm in leaving it there, I'll just keep things the way they are. Also, it's worth noting that these settings are 100% effective with a NON-BROADCASTED essid, so these suggestions should work regardless of whether or not you have set the router to broadcast the essid.

EDIT: Also, another technique I found out that may work if this fails is to set up a cron job and have it ping an internet server every x minutes. That way, the connection will never timeout.

---

### Post by skip27 on 2007-04-09
Well, the problem is back. Not sure what to do... as of now, invoking the following command seems to work.

```

sudo wpa_cli -iwlan0 reassociate

```

But that still doesn't explain why my card is having trouble reassociating by itself. The connection is essentially "timing out" (don't know how else to refer to it, even though that's technically not what its doing). I guess I could just set up the cron job, but I'd like to find an authentic fix before resorting to the dirty hacks.

Is anyone else's WPA connection timing out? This never happened when I had WEP...

EDIT: It *could* be my card and/or the router. Unfortunately, it isn't feasible for me to troubleshoot by trying different routers/cards. What matters is that my connection is fairly reliable anyway. I tried adjusting the txpower to auto, so we'll see if that does anything.

EDIT2: Alright, I'm narrowing it down. It's more than likely a driver issue. I was using ndiswrapper and am currently using the bcm43xx native driver. So far so good. If this doesn't work, then it might very well just be my router. At any rate, I am preserving the same settings (i.e. fast_reauth=0). I had originally tried the bcm43xx drivers /w fast_reauth=1 with the same problems as before, so perhaps now I have finally fixed it! Also, since I have an HP R3120US laptop, I will try using the Broadcom drivers provided by HP to determine if that fixes it. Will update.

EDIT3: I get the same problem at school using ndiswrapper, which means that I can rule out the router as being the problem. At this point, I'm willing to bet it's a driver issue. As of now, I'm trying the bcm43xx + wl_apsta.o firmware. We'll see how this works...

EDIT4: Seems I'm not the only one with this problem (scroll down): [http://ubuntuforums.org/showthread.php?t=348879](http://ubuntuforums.org/showthread.php?t=348879) and [http://ubuntuforums.org/showthread.php?t=208053](http://ubuntuforums.org/showthread.php?t=208053)

---

### Post by skip27 on 2007-04-14
Found the solution. It does seem that ndiswrapper + the BCM4306 chip does introduce problems with the usage of wpa_supplicant. Your connection may "timeout" after a while of inactivity, forcing you to reload wpa_supplicant or use wpa_gui/cli to reconnect it manually.

So, the fix? Use the native bcm43xx drivers and extract the firmware from the wl_apsta.o file. So far, I have had significantly fewer connectivity issues (still not perfect). The only other complaint that I have with this method is that my iwconfig tends to default to 11M instead of the preferred 54M speed. Though the connection is still functional if I use 'sudo iwconfig wlan0 rate 54M', it eventually sets itself back to 11M.

Again, though, the bcm43xx drivers for the BCM4306 chip have proven so far to be fairly reliable. Expect future development to bring even more enhancements.

Anyone else having issues with setting the rate to 54M? If you ever need to temporarily work around this problem, rmmod bcm43xx and modprobe ndiswrapper for 54M speeds.

---

### Post by skip27 on 2007-04-24
And just to make things more complicated, a new discovery. I was originally using the D-Link VDI-624 router provided by Verizon (using their FiOS service--this is NOT the same as the DI-624). A few days ago, I purchased a new router: the D-Link DGL-4300 Wireless Gaming Router. Rave reviews, supports WPA2, 108Mbps, etc. So, I set it up, and just for fun decide to use ndiswrapper to see if I continue having the problems I once did.

My connection is *ROCK* solid. For the few days I've had it, I have not once had my connection drop. Ever. 54M works wonderfully with my BCM4306.

I purchased this new router because my old one was flakey; sometimes I could see other computers, other times no. Now, I can always see the other computers in the network and my connection is remarkably fast and stable.

What can I conclude? A few things for you people who are having problems with a stable wireless connection.

1) Check your AP (access point). How old is it? Is it using the latest firmware? Is it reliable with tasks other than wireless communication? The problem with my router is that Verizon's latest firmware for this router was made in 2005, and the DI-624 firmware is incompatible with the VDI-624.

2) The drivers in Linux (i.e. bcm43xx vs. ndiswrapper) can be sensitive to outside conditions depending on your hardware. My guess is that ndiswrapper required a better AP, since it obviously couldn't handle my old router. Yet, the bcm43xx open-source drivers worked flawlessly with my old router, but lacked 54M speeds. Also, even though my connection is stable at home using ndiswrapper, that may change when I go to school and use their network. I may have to temporarily revert back to the bcm43xx driver.

3) Your hardware is another potential problem. Broadcom support in Linux is sketchy at this time. I'm willing to bet anything that had I been using another wireless card, I wouldn't have any problems with any router, regardless of age or firmware used. I almost bought a D-Link wireless card to replace this Broadcom crap. Even though my card worked in Windows many months ago, Linux is a different beast altogether. Be mindful of this.

**_Conclusions?_**

If you're having any wireless problems, **CHECK YOUR DRIVERS**. I had to jump through 10 billion hoops before I figured this out (sounds self-evident, but not while your busy isolating the problem when it could be many different things), which says something considering that I'm a seasoned Linux user. Always try the open-source drivers if you're having ANY connectivity issues whatsoever. Even though the bcm43xx drivers are incomplete, they still proved more stable with an inferior router than ndiswrapper did.

Finally, if you simply don't want to deal with all this hassle I've outlined, **BUY HARDWARE THAT HAS COMPLETE OPEN-SOURCE DRIVER SUPPORT.** Believe me, you will save yourself a lot of aggravation and time.

---

### Post by keith11 on 2007-04-25
I am facing the connection dropping out problem too but with a WEP encryption. EVen without encryption, the connections seens too slow and fluctuates too much. I am using ipw2200 and I am not using ndiswrapper. DO you think applying the changes that you suggested in the first post on this thread will work for WEP too? My problem has been posted here in case yu want to take a look to have a better idea about what I am saying: [http://ubuntuforums.org/showthread.php?t=423075](http://ubuntuforums.org/showthread.php?t=423075)

Thanks.

Keith.

---

### Post by skip27 on 2007-04-27
Keith,

Looks like this complicates things even more for my theories :) A couple of suggestions:

1) Try [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/). You can also visit Intel's site and download from there using a quick Google search for ipw2100 linux drivers. Recompiling a new set of drivers may solve your problems.

2) Experiment with ndiswrapper. It could simply be that, based upon your specific hardware configuration, it just works better.

3) Try another distribution's LiveCD, e.g. Knoppix (or Gnoppix) and see if you have the same problems.

So, it looks like I'll have to revise my theory: "try everything." That isn't very helpful in it of itself, though :(

---

### Post by keith11 on 2007-04-27
Thanks for your suggestions. I am averse to compiling anything based on my experiences earlier in 6.10 or linux in general. With compilation I am not sure whether it will work or not and I can't risk it right now. I may try using ndiswrapper but I don't know how to uninstall my current drivers and then use ndiswrapper. I will search that.

Keith.

---

