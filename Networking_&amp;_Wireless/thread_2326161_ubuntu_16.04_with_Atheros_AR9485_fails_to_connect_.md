---
title: "ubuntu 16.04 with Atheros AR9485 fails to connect to Wifi"
date: 2016-05-28
forum: Networking &amp; Wireless
---

### Post by tess2 on 2016-05-28
I installed ubuntu 16.04 on my HP Pavilion dv6 about two weeks ago. It had a couple of hiccups but was basically running fine. Then, three or four days ago, it just stopped connecting to Wifi.

Symptoms:
 - Will not connect to either of the Wifi networks I've tested. Other devices can connect to these networks.
 - When I try to connect to the local Wifi, I am prompted for the network password. If I input the correct password, the Wifi icon indicates that it is "connecting" for about thirty seconds to a minute, then disconnects me. Trying again just loops. If I input the incorrect password, it prompts me for the password again, so my computer must be at least talking to my router.
 - This started a few days ago, I think the first time I rebooted after running a software update.

Attempted Fixes:
 - Rebooting computer/router/wireless card. Each have been done about a dozen times.
 - Manual connection to Wifi, rather than automatic through Network Manager
 - Deleting all other connections in Network Manager before attempting another manual connection to Wifi.
 - A few other things that googling the issue has led me to believe might help, but I don't remember precisely everything.

The one thing I can think of that I haven't already tried is running another software update. I expect that's not likely to solve the problem on its own, but once I post this I'll scrounge up a cable and see if I can connect directly, and I'll update this if that solves the problem. UPDATE: No dice.

If anyone has any other avenues I can explore, I'd appreciate the help.

Thanks in advance!

---

### Post by connor23 on 2016-06-01
Hey dude,
I was having a similar issue (with the same wireless adapter). I don't know exactly what I did to fix it, but here is what I remember doing. 

- Connect via Ethernet and start the "Software Updater" program.
- The connection would drop after 30 secs so I had to keep unplugging/replugging in the cable
- I didn't finish updating so I restarted the laptop
- Used the key combo on my keyboard to disable and re-enable the wifi (Fn + F2 on my laptop)
- Deleted all connections in network manager and create a new one for my wireless
- In the settings for the wifi connection, I disabled the IPv6 settings (by choosing "ignore" on the IPv6) as I only use IPv4
- Connected to the wifi 

It all seems to be working fine now, I'll try again tonight when I get home and see if there are any important things I did.

---

