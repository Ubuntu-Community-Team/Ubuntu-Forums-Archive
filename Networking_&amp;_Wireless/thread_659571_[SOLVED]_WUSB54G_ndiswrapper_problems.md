---
title: "[SOLVED] WUSB54G ndiswrapper problems"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by philbastian on 2008-01-05
Hi there,
I'm pretty new to Ubuntu and Linux, but I've been on about a billion different threads and haven't found much.  My PC is a brand new Dell with an AMD 64-bit processor.  I am running 32 bit Gutsy because there was just too much that I couldn't do with the 64-bit.

I have a Linksys WUSB54G wireless card.  I'm trying to set it up to work with ndiswrapper.  I should also mention that I have an old D-Link card that I was trying to set up with ndiswrapper and it had the exact same problems.  I am currently using a Netgear WG111v2 card, which Linux detects, but it quits working after about 2 hours or so for some reason, and I'd really like to take it back to the store where I bought it, because I already have two wireless cards.

So, going through all of the normal steps, I get ndiswrapper to install the driver, it says that the hardware is present, suggests another driver (p54usb, which I have blacklisted).  Then it shows up on the network lists, but it doesn't connect.  The link LED does not light, and iwconfig returns:

```
wlan2     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Also, I am using a WEP Hex key, so this shouldn't be a WPA issue.  My networking settings show that everything is as it should be.  Any suggestions you can give me are much appreciated.  Here's the -v info:

```
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 
```

Thanks,
Phil

---

### Post by philbastian on 2008-01-06
Here's an update --
I started the computer this morning and it wanted to check the hard drives.  I discovered this error message:

Error inserting iwlwifi_rc80211_simple (lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_rc80211_simple.ko: Unknown symbol in module, or unknown parameter (see dmesg).

I tried checking the dmesg, but as I said, I'm pretty new to this still, and I couldn't figure out what among the pages and pages of logs might be useful.  The device is connected as wlan2 (the one that works is wlan0 and for some reason there isn't a wlan1), and running a search for wlan2 didn't return anything.

Thanks in advance for the help,
Phil

---

### Post by philbastian on 2008-01-07
Alright, I installed Wicd, and now it works.  I guess it would be kind of nice to know why, but if it works, it works.  Interestingly, it seems to be using wext instead of ndiswrapper.

Anyway, if you are having a similar problem, that might be a solution...

Phil

---

