---
title: "manual configuration wireless issue"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by slamp on 2007-10-20
when I set my wireless in Network Manager to roaming mode and I "Connect to Other Wireless Network" in the applet I am able to connect wirelessly. BUT when i configure manually so that my laptop connects automatically it does not work. how is this possible? if manual configuration will not work, how do I save the roaming mode so that it connects automatically next time? it seems that when in roaming mode and laptop is restarted, the settings i put is not saved. where does the roaming mode config gets saved to?

i have an inspiron 1420 with intel pro 4965 AGN.

---

### Post by Trueno22 on 2007-10-20
it's been like this for a while in Gutsy my advice is to install Wicd.  It works flawlessly on my system.  The issue is with the network manager.

---

### Post by slamp on 2007-10-20
yes i have actually taken this route. wicd is great. how the hell can they release this as stable when things arent working properly.

---

### Post by kevdog on 2007-10-20
WICD is great -- if you want the manual configuration put it in a script file and then add it to your startup sessions (wicd probably a better alternative but there are many ways to skin a cat)

---

### Post by antillas21 on 2007-10-22
I think I have a similar issue in Gutsy amd64. Gutsy detects my wireless card and lists available wireless networks, but when choosing to connect to one of them, Gutsy freezes when in roaming mode and when trying to use Manual Configuration it freezes after the second or third attempt.

After three or four freezes (had to use the power button to restart, no other option available) my system would not load and displayed a message of kernel panic.

Anyone else has been experiencing this kind of problems?

---

### Post by bozotheclown on 2007-10-22
> **antillas21 said:**
> I think I have a similar issue in Gutsy amd64. Gutsy detects my wireless card and lists available wireless networks, but when choosing to connect to one of them, Gutsy freezes when in roaming mode and when trying to use Manual Configuration it freezes after the second or third attempt.

After three or four freezes (had to use the power button to restart, no other option available) my system would not load and displayed a message of kernel panic.

Anyone else has been experiencing this kind of problems?

I am, I've not found a decent solution yet.

---

### Post by antillas21 on 2007-10-23
OK, I first followed the instructions that kevdog posted here ([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)) to manually connect to my home network. After following his instructions I successfully connected, but I couldn't comment out from the blacklist file the proper drivers for my card (rtl8180) because they weren't there.

So I tried the Wicd approach and now I can successfully connect wirelessly to my network, but even when my wireless router does have the broadcast ESSID enabled, Wicd can not see any networks around automatically, I have to use the Hidden Network tab and enter my network name every time I want to connect to it.

At least I am able to connect wirelessly for now.
Also I have realized that WEP encryption freezes my computer when enabling it on the router wireless settings. I don't know why this happens, but if I set my wireless network without encryption everything just works, and if I activate WEP, my computer freezes when attempting to connect.

---

### Post by kevdog on 2007-10-23
What driver are you using??

To blaclist the driver you need to add it to the blacklist file.  Like:
echo "blacklist r8180" | sudo tee -a /etc/modules

---

### Post by sbennettgso on 2007-10-23
A lot of people seem to be having trouble with the RTL8180 driver.  I know I was.

I was having the issue of hang-ups when using the native driver to connect to WEP-enabled networks.  I could connect to open networks, though.

I ultimately used ndiswrapper to get around this.  I used the Win98 driver from RealTek (per Kevdog's thorough tutorial on ndiswrapper) and blacklisted the 'r8180' driver.  I seem to be up and running now as I would expect.

Thanks,
Scott

---

