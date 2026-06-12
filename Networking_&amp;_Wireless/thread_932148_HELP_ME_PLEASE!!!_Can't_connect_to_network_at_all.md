---
title: "HELP ME PLEASE!!! Can't connect to network at all"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by skippynumnums on 2008-09-28
Hey guys, I just installed ubuntu 8.08 and I can't seem to connect to the internet at all... I would like to eventually get it working with the wireless card I have installed, but that would be a lot easier if I had some form of internet on there at all. It is plugged into the same hub that the computer I am writing this from is plugged into. 

INFO:
1 - when i check the network tools, the only network device that shows up is the loopback interface (lo)

2 - my wireless card is a "trendnet tew-421pc" (A model)

---

### Post by Another Monkey on 2008-09-28
Not sure if it helps much, but it doesn't seem like your card is fully supported: [TrendNet info]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTrendnet").

I assume you have checked out the [sticky]("http://ubuntuforums.org/showthread.php?t=564419")?

There is also a complete list of [supported cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

It looks like your card isn't being registered.  But I am no expert, I am still fighting with my own networking problems.  What follows is just basic trouble shooting.

Disconnect router from internet.
Disable all firewalls, MAC filtering, etc.

Does it work wired?
Yes - Basic networking OK.  Bring firewalls, MAC filtering etc. back on-line one at a time.  Check at each step.  If is suddenly stops working, most likely case is the last firewall/filter to come up blocking things.  Fix this.
No - Basic networking issue.  Check the router, does that say it is connected OK?  Does it show a client list (if using DHCP)?  If it doesn't work in this state, it won't work.  You need to gets this going.  Check for known issues with router, check documentation (you may have a mis-configured router).

Once all firewalls are back.  Check your wireless settings on the router.  is it on?
Yes - OK.
No - D'oh!  But at least you found the problem!

Switch off any wireless security (e.g. WPA), turn SSID broadcast on etc.; you will be running an "open" network briefly.  Try the card again.  Can you see the network?
Yes - Cool.  Try to connect.
No - Poor signal or duff card?  Can you try moving locations or a different card?

If Wifi was found, could you connect?
Yes - Excellent.  Slowly bring the Wifi security on-line one bit at a time (e.g. enable WPA).  Check at each step, if Wifi suddenly fails; you found your problem.  With SSID turned off (safest) you will need to manually connect as the Wifi card won't know your network is there (but it will connect if told to).  This is not the problem!
No - Do you have (or can you borrow) any other devices that can do wireless?  e.g. Mobile phone, Wii, anything?  Try those.  If they won't connect, check your router for odd settings (I had to flash my router BIOS to fix some issues).  Your manufacturer should have details on updates/workarounds.

Or (and this is what I did) but an Edimax PCMIA card.  Works out of the box (and much, much better than the Belkin dongle it replaced).  About UK£10 on Amazon.

---

