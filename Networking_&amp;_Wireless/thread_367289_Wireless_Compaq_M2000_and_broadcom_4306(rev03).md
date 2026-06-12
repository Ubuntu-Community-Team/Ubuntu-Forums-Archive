---
title: "Wireless Compaq M2000 and broadcom 4306(rev03)"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by jasonbrisbane on 2007-02-22
Hello All,

I have been hunting through the myriad of wireless/WPA/WEP/ndiswrapper/networking Howto's and Stickies in order to get it working.

I have a Compaq presario M2000 Laptop running an inbuilt Broadcom 4306 Wireless (rev 03) adaptor, as listed on the NDISwrapper list. I have tried following all the examples (with varying success) but have not actually got the adaptor (completely) up yet.

(NOTE: The AP works fine under Windowxs XP, DHCP is enabled and WPA was enabled - have changed it to OPEN for testing...)

In every scenario I have tried the iwconfig shows the AP as "Invalid". I have tried setting:
> iwconfig eth1 ap any
but still get the same result.

On the last attempt (around 10PM last night) I reinstalled Ubuntu 6.06 LTS (dapper?) and installed the NDISWRAPPER following the instructions to the letter (only one .sys and .inf file in the directory and install using ndisgtk).

The iwconfig and ifconfig actually reported an IP address!
Only problem is, its IPv6, which I'm not using, and the AP is still invalid and it hasnt picked up an IP, or any DNS settings that the AP should have assigned it over the wireless.

This is the closest I have gotten.

I previously had installed network-manager-gnome and gotten the it to search for the wireless LAN but the PC had the ethernet plugged in and was communicating over that. When I pulled the cable out it immediately fell over - no wireless connectivity at all. (So ethernet and IP settings are all fine since I can use the wired ok but the wireless is falling over)

I figured the problem was with the Device driver, so I'm only using ndiswrapper now.

How do I get the AP to be picked up by the laptop?
Is this Iv6 a false positive since I havent got the AP settings?

Did anyone else have similar issues (with similar hardware)  and how did you work them out?
If so, what did I miss?

---

