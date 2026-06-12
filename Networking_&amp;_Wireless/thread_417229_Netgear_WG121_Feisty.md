---
title: "Netgear WG121 Feisty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by mwaddoups on 2007-04-21
I'm having a problem configuring my USB wireless card in Feisty. The last time I used this with Linux it was in edgy, and it was a simple matter of installing ndiswrapper, installing the driver, modprobe ndiswrapper and it worked. However, in this version it comes with another driver "prism54usb" by default. This seemed to provide no advantage, or show a wlan0 interface in iwconfig, so I added blacklist prism54usb to /etc/modprobe.d/blacklist. I then installed ndiswrapper, but upon modprobing only one light on the device lights up, and there is still no wlan0 interface. I have tried the version from the repos, and the latest version from the website. Any tips on how to make this work?

---

### Post by nikkkko on 2007-04-24
I'm just about to attempt the same and came across this:

[https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121)

Hope it helps

---

### Post by _Paladin on 2007-04-24
I am having the same problem.

---

### Post by nikkkko on 2007-04-25
I followed the howto, (link above), for a clean Feisty install except that I:

1. downloaded version 1.38 of ndiswrapper instead of 1.16. 
2. blacklisted prism54usb and prism54common as well as those on the list

All now working ok.

---

### Post by oimon on 2007-05-14
I'm having the problem on feisty where the machine freezes hard after a couple of minutes of wireless activity on the WG121 using ndiswrapper, and the latest ndiswrapper 1.43(?)
Never had this problem using breezy/dapper/edgy

I've downgraded to my MA111 adapter using ndiswrapper instead. (that's only a 802.11b card though). I'm a bit stumped as to why it is only freezing now. (I've tried the blacklists etc)

Anyone else experiencing the same probs?

---

### Post by alanmzifa on 2007-05-14
Didn't you work out the "how-to" for the WG121?

I've a WG121 and never got it going on Dapperso stuck to XP for my desktop. I'd be very keen to get the WG121 working with Feisty which I just re-installed on my desktop last night.

When you wrote the "how-to" which version of NDISwrapper did you use? Don't want to use 1.43 if it's broken.

I see in the release notes on Sourceforge that 1.43 might break some drivers.



Also, have you PM ed nikkko?

---

### Post by Plupp on 2007-05-20
IT WORKS, IT WORKS!!! Thanks to all you wonderful people in Ubuntu-world. :KS

1. Clean install Ubuntu 7.04 Feisty Fawn
2. Download all the latest updates via the Synaptic Packethandler
3. Restart
4. Follow this how-to [https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121) by Alex Latchford with the addition of the notes from nikkkko, namely:
  downloaded version 1.38 of ndiswrapper instead of 1.16 and
  blacklisted prism54usb and prism54common as well as those on the list.
Used the original diver from the CD (ver 1.1).
Output from ndiswrapper -l then reads:
netwg121 : driver installed
           device (0846:4210) present (alternate driver: prism54usb)
5. When the driver is loaded (with sudo depmod -a and
sudo modprobe ndiswrapper) both LED's are lit!!!
6. Configure connection with Network Manager
7. DON'T FORGET to make it load next time you restart by typing sudo ndiswrapper -m (see part 6 of the how-to)

Surf away!!!

Greatful I am... O:)

---

### Post by oimon on 2007-06-01
hi plupp
interested to see how you're getting on a week later - mine was freezing all the time!

---

### Post by oimon on 2007-09-27
Hello. If anyone comes across this thread from a google search etc then the wiki [https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121) is updated with the feisty details.

Ignore my previous comments about system freezes. I downgraded for a few months because of system freezes until I realised that my power supply was underpowered and causing system freezes. I'm back on the WG121 and it's working fine again.

Anyone had the guts to try it on an early Gutsy release yet?

---

