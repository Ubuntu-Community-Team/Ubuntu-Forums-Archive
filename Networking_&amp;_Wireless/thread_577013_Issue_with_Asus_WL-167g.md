---
title: "Issue with Asus WL-167g"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by WeKnowBetter on 2007-10-15
I'm having knock-my-face into a bloody wall issues with the WL-167g. 

The driver loaded by ubuntu is the rt73usb driver, and for some reason, satanic or otherwise, ubuntu can see two wireless cards. One, dubbed wlan0, seems to work, the other, dubbed wmaster0, seems to be a ghost card. Something intangible and useless. 

EDIT: The lsusb-command gives me the following device ID: 0b05:1723. Does this make sense?

I can see several wireless networks, and I can attempt to connect to my own network, but it simply attempts (with the swirly thing circling in the sys-tray), and then stops. I can attempt to connect ad nauseam, but it doesn't work. I've had the same issues with my laptop (on which I am writing this), but a manual config solved the problem eminently. 

The issue is not wpa nor is it wep. I've unsecured the network and added all the network adapters to a mac-list on the router. I've double-checked this a multitude of times, to ensure that it was not my inherent retardedness that caused malfunction. I cannot even do a manual config. It just sits there like a magnificent fat toad, burping and doing nothing. 

Help me, Ubuntu-Wan-guys, you're my only hope. 

WeKnowBetter (Well, obviously we don't, per se, but it sounds good.)

---

### Post by Tomosaur on 2007-10-18
I have this exact same issue on Gutsy 7.10 (release version, not pre-release) - same card, same symptoms. I've tried disabling avahi and setting the connection up manually (I heard avahi was causing some people issues, evidently avahi is not my problem). Sometimes it appears to connect, but Firefox and any other internet app still give me a no-connection error.

In the terminal, 'netstat -rn' gives an empty report. Sometimes iwconfig shows wlan0 as having an SSID, an AP, and generally looking good to go, but still no network activity. I have Windows on the same machine and the internet works fine.

I have tried disabling WEP, still have the same problem.

Any help would be much appreciated!

---

### Post by Tobis84 on 2007-10-23
I have that same problem, but it seems to be af problem regarding the chipset rt2500. It's not an ASUS specific problem, though I'd like a solution too... 

I'm totally green in Ubuntu just downloaded Gutsy last week and I'm still not online with this card.

Any help would be nice...

---

### Post by mogie on 2007-10-29
Confirming the same problem here. 

I get up one wlan0 and wmaster0 with same MAC. (only that wmaster0 has a bunch of ..00-00-00-00-00 after it.)

If I bring the wmaster0 down, the wlan0 does down.

First, I would like to point to that I've been searching for solutions for this WLAN-adapter to Asus for years now. I've testet a bunch of different distro's, and the only one which has a stable right out of box driver with packet injection support is Slackware Backtrack 2.

Maybe I will need a .tar.gz install like I tried back in the days..however I hope the people compiling/reorginizes the drivers in Ubuntu to this adapter can get a stable one as they have on Backtrack2.

NOTE: I forgot to mention that Ubuntu has changed the if-name to the device from "rausb0"  to "wlan0"... it makes me pissed every time I try to configure the network..

---

### Post by Tobis84 on 2007-11-01
Same here.
I can just join the corus of you people with this issue.
I have tried something regarding the RT2500 chipset, but nothing works so far.
Maybe the solution is to adopt the Slackware driver mentioned above.
Hopefully something come out soon, so I don't have to get another wireless card.

---

### Post by forcheville on 2007-11-13
Same problem here too. I'm glad you guys have tried removing MAC filtering and WEP etc because they were on my list to do next and I can scrub them.

I started with KNetworkMaster in Kubuntu Gutsy 7.10 
It found all the dozen or so WAPs in my building with the same range of signal strengths I was used to seeing in Windows. All it seemed to need was the WEP key but when I entered that it just hung on "Configuring device".
I tried ndiswrapping the Windows drivers etc. 
"> ndiswrapper -l"  always showed the rt2500usb driver as "alternative device" even when there was no other driver visible.  
I guess rt73usb is hidden in there somewhere and over-riding it.

The more things I did the fewer networks it seemed able to find.
In the end it could only see two of the other local ones, neither of which was mine. 

Much reconfiguring seems to have affected the dongle because it now no longer works in Windows. :confused:

I'm going to rearrange the furniture and go back to cable.:)

---

### Post by Tomosaur on 2007-11-23
Just thought I'd post here - my internet connection now works in Ubuntu Gutsy with this dongle. I have no idea why, I tried about a million different things. After I removed ndiswrapper and removed rt2500usb from the blacklist, THEN set up my connection manually (IP addresses, DNS etc), the internet suddenly came to life - ironically much faster than it seems to go in Windows.

Sorry I can't describe exactly what I did to get it working - but it just goes to show that with a little patience and perseverance, things will work out in the end!

---

### Post by RoboRat on 2008-02-01
I got the same result as Tomosaur.  The trick with this dongle is to use it with static IP.  It has the same odd behaviour of losing its IP in DHCP even in Windows.

Cheers!

RoboRat

---

