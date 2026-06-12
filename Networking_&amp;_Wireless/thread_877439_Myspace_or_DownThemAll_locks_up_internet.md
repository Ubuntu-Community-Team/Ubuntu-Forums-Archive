---
title: "Myspace or DownThemAll locks up internet?"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by Databit on 2008-08-01
I wouldn't necessarily believe it myself but I can actually duplicate it at will. If I visit myspace and just go to default profile view then maybe to my friend request or messages internet will start timing out everywhere. Downloads via DTA or 'save link as', web pages in Firefox or Konqueror...or lynx.. Can't even [http://192.168.0.1](http://192.168.0.1) to get to the router page. Clicking the nm-applet and clicking on my router so that it reconnects to the wireless seems to fix it. 
Running Hardy Heron/gnome on a Dell D620 laptop. Visual Effects disabled. No WEP or WPA or any security whatsoever on the wireless.

it's very odd..Happens a lot with facebook as well. Does my laptop hate social networking?
If you want anymore info just tell me how to get it and I'll send it along

---

### Post by Databit on 2008-08-01
More info
My wireless card is listed as PRO/Wireless 3945ABG Network Connection and the driver was auto installed on installation

---

### Post by dmizer on 2008-08-01
Well, social networking sites have lots of Java.  They also have loads of extremely poor (and sometimes downright dangerous) code.  Most people on social networking don't have the first clue as to how to put together a properly functional page, let alone how to secure it.  They have automatically running scripts and applets and all those dirty little trinkets that look so neat, but bring your browser to its knees.  My computers just crawl when I make the mistake of visiting those places (Windows or Ubuntu).

There could be a number of problems in your case, but I suspect you're simply getting disconnected from your router by NetworkManager (nm-applet).

I suggest you disable NetworkManager by following these directions: [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

Then, configure your wireless network by going to System > Administration > Networking.

---

### Post by mordak13 on 2008-08-01
I have various slowdown issues with both sites from time to time but I attribute it to excessive traffic to those two sites. Same issues for my wife on her XP laptop.

---

### Post by Databit on 2008-08-02
dmizer. Thanks for the tips. I had high hopes but it doesn't look like it fixed it.

mordak13. You and dmizer are right Myspace and Facebook are notoriusly slow and just plain horrible. I was mainly giving those as an example because I can typically duplicate the issue with either one of those or DownThemAll downloads.
If somebody told me they where having this issue I just plain wouldn't believe them. "Websites knock out my internet connection" Like I said before it's just weird.

Whenever duplicate the problem the same thing happens. Suddenly all pages start timing out and I have to reconnect to my router. It isn't just the 1 or 2 sites themselves. Once the problem occcurs all of my network connectivity goes bye bye. Pidgin, SSH, Lynx, everything. 
I've been trying to narrow it down a touch and I think it has something to do with Firefox. If I browse the web with Konquror and hit myspace, facebook, random digg.com stuff then I don't lose network. But if I hit the same sites with Firefox suddenly everything starts to drop.

---

### Post by dmizer on 2008-08-03
Sorry to hear it didn't work.  I had high hopes too.

Do you get disconnected if you download a file via bittorrent?

What wireless card are you using, and what chipset does it have?

---

### Post by Databit on 2008-08-09
Didn't realize there had been any more responses on this thread.
I'm not sure about bittorrent downloads because I despise bittorrent.
My wireless is listed as Intel®  3945 WiFi 802.11a/g. Not sure about the chipset where would I go to find that?

---

### Post by dmizer on 2008-08-10
> **Databit said:**
> Didn't realize there had been any more responses on this thread.
I'm not sure about bittorrent downloads because I despise bittorrent.
My wireless is listed as Intel®  3945 WiFi 802.11a/g. Not sure about the chipset where would I go to find that?

If you despise it or not, it's still a good test.  I'm not suggesting that you use bittorrent exclusively, just that it would be a good test.

To find the chipset for your wireless card, please post the output of:
```
lshw -C network
```

---

### Post by Databit on 2008-08-10
Here is the output from lshw -C network


 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:ae:c8:98
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.107 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:be:2d:2e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=half firmware=5752-v3.19 latency=0 link=yes module=tg3 multicast=yes port=twisted pair

I'll suck it up and give the torrent thing a go and let you know how it worked out

---

### Post by Databit on 2008-08-10
Yep looks like bittorrent locks me up as well. Downloading ubuntu-8.04.1-desktop-i386.iso from [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) and it got to 19 of 24 connected peers and about 24 megs then it dropped to 0k and I couldn't browse the web and pidgin started timing out. Tried getting to router web config and no go. Tried internet with another computer (also running Hardy Heron) and it was good. So it's limited to something with this laptop.

---

### Post by Databit on 2008-08-10
Left out the fact that I kept things clean. Was only running Pidgin and Transmission. No web browsers running while I did the torrent test. So pulled Firefox being the culprit out of the picture.

---

### Post by Databit on 2008-08-10
More looking into this on the driver side. My /etc/modules contains:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

```

Since I have a 3945ABG should I be using the iwl3945 drive that's in the kernal already? If so what's the modification I would need to do to use this driver?

---

### Post by dmizer on 2008-08-11
> **Databit said:**
> Since I have a 3945ABG should I be using the iwl3945 drive that's in the kernal already? If so what's the modification I would need to do to use this driver?
According to your lshw output, you are using the iwl3945 driver:

> **Databit said:**
>        product: PRO/Wireless 3945ABG Network Connection
[snip]
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.0.107 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

What kind of wireless security are you using?  Try using sequentially less security settings on your wireless access point.  For example, if you're using WPA, does the problem still exist if you use WEP?  If the problem exists with WEP, does it still exist if you have your wireless wide open?

Not suggesting that you run this way for a long period of time, just trying to isolate the cause of the problem.

---

### Post by Databit on 2008-08-11
dmizer,
That was one of the first things I tried. Disabled security completely

---

### Post by dmizer on 2008-08-11
Well, about all I have left to suggest is for you to try a different driver for your card.  Try NDISwrapper and see if that makes any difference for you: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by sofakingwhat on 2008-08-13
Hi Guys, 
I have a similar issue in that when i visit these pages (mainly facebook) my internet locks up as well. I can still access my router config page ([http://192.168.2.1](http://192.168.2.1)) and resetting the router clears it every time. When the internet locks up, no computer in my house can get on (inc a windows machine and a macbook). It happens using WPA, WEP and no security. 
To confuse things even further, i can get the same thing to happen using the macbook and the windows machine just by visiting facebook. The ubuntu machine and windows machine use firefox but the macbook uses safari. 
My next step was going to be buying a new wireless router and trying that out but any other suggestions would be great. 
Thanks!

---

### Post by dmizer on 2008-08-13
> **sofakingwhat said:**
> Hi Guys, 
I have a similar issue in that when i visit these pages (mainly facebook) my internet locks up as well. I can still access my router config page ([http://192.168.2.1](http://192.168.2.1)) and resetting the router clears it every time. When the internet locks up, no computer in my house can get on (inc a windows machine and a macbook). It happens using WPA, WEP and no security. 
To confuse things even further, i can get the same thing to happen using the macbook and the windows machine just by visiting facebook. The ubuntu machine and windows machine use firefox but the macbook uses safari. 
My next step was going to be buying a new wireless router and trying that out but any other suggestions would be great. 
Thanks!

You should read through this thread (it's only 2 pages at this point) and try some of the suggestions that have already been given, but I think your problem is more serious.

---

### Post by sofakingwhat on 2008-08-13
Yeah sorry, i meant to add that i have read through and tried what i thought may be relevant to my problem with no luck. 
I am going to change out my router, i was really just looking for a second opinion.

---

### Post by Can0n on 2008-08-25
I have this exact problem aswell. Had this for a few months I think but Im using Epiphany when I want to access Facebook, it works fine there.
But the internet starts to work after maybe 2-4minutes without needing to restart the router, and my torrent-downloads/uploads work to.

Have tried the "fix" but it didn't help. Haven't rebooted the computer after I did that but should I have to ?

---

### Post by Databit on 2008-08-26
dmizer
I finally got around to doing the NDISWrapper I ended up having to follow [http://clearpixels.net/2008/07/3945abg-fix-for-ubuntu/](http://clearpixels.net/2008/07/3945abg-fix-for-ubuntu/) which is pretty much the same think as the link you sent but adds iwl3945 to the blacklist.
But is the ndiswrapper supposed to be about half the speed? The connection dying completely seems to have stopped but now I'm getting about half the speed when I download

---

### Post by Can0n on 2008-09-02
Bump. Someone else have this problem or a fix?

---

### Post by Zzzach on 2008-10-09
Having the same problem. Everytime I go to myspace, the internet freezes up til I close the page. It works fine using Wine Firefox though, so it's something to do with Firefox or flash I think.

---

### Post by dmizer on 2008-10-09
> **Zzzach said:**
> Having the same problem. Everytime I go to myspace, the internet freezes up til I close the page. It works fine using Wine Firefox though, so it's something to do with Firefox or flash I think.

I think your problem seems to be more software related rather than hardware related like some of the other posts in this thread.

I would suggest updating to flash 10 as well as trying the non-free sun java.

---

### Post by Databit on 2008-10-24
Hey guys
My initial problem was somewhat alleviated by going to the ndiswrapper but it was slooowww and would occasionally happen with those sites. But only with firefox as I said before. Well recently I tried to go to Flash 10 cause I heard hulu plays well with 10. Had problems so I said screw it and backed up my main stuff out of /home without any of my settings. Reinstalled 8.10 then flash10.
Been going all week and not a single lock up of my internet no ndis required. 


boils down to dmizer was probably right with the old flash being the problem. It was a piece of **** compared to 10.

---

