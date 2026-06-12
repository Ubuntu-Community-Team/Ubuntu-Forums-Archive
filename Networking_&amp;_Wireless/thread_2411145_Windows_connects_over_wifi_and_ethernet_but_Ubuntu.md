---
title: "Windows connects over wifi and ethernet but Ubuntu and Android don't"
date: 2019-01-25
forum: Networking &amp; Wireless
---

### Post by ke2wombo on 2019-01-25
[indent]There's got to be some kind of stupidly simple thing I'm missing here... all devices successfully connect to our current wifi hub / router and thereby to the internet with no problems.[/indent][indent]&#8231;[/indent]  [indent]But I dug out my old Asus WL-500W wireless router to give it to a friend and have discovered that while my roommate's Windows 10 laptop successfully connects and gets an IP address from the router, my Android phone and my Ubuntu laptop don't.  Including connecting the Ubuntu laptop to the router via the same ethernet cable the Windows 10 laptop can connect through.[/indent][indent]&#8231;[/indent]  [indent]I've switched off all security settings on the router: no wifi encryption or passphrase and MAC address filtering is shut off.  But while the Ubuntu system and the Android device can see the wifi SSID and recognize it as unsecured, they never successfully connect and seem to get hung up on acquiring a DHCP lease.[/indent][indent]&#8231;[/indent]  [indent]I plug the Ubuntu laptop in via ethernet and connect it via wifi to the apartment's other, working router and run ```
dhclient -v -1
``` and I can see it pick up an IP address from the working router over the wifi but not on eth0 on the old ASUS router. (DHCP on the old router / eth0 is set to lease a different range of addresses than the current, working one, so that's not the problem.)[/indent][indent]```
[indent]Listening on LPF/wlan0/00:1[...][/indent] [indent]Sending on   LPF/wlan0/00:1[...][/indent] [indent]Listening on LPF/eth0/00:1[...][/indent] [indent]Sending on   LPF/eth0/00:1[...][/indent] [indent]Sending on   Socket/fallback[/indent] [indent]DHCPREQUEST of 192.168.1.10 on wlan0 to 255.255.255.255 port 67[/indent] [indent]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3[/indent] [indent]DHCPACK of 192.168.1.10 from 172.23.23.1[/indent] [indent]RTNETLINK answers: File exists[/indent] [indent]bound to 192.168.1.10 -- renewal in 40487 seconds.[/indent]
```[/indent]  [indent]What am I forgetting here?[/indent][indent]&#8231;[/indent]  [indent](sorry about the weird formatting, something is deleting newlines when I post)[/indent]

---

### Post by TheFu on 2019-01-26
No clue, but is the firmware current?  

Any linux router firmware that hasn't been patched since about July 2018 has major security bugs which allow remote attacks and takeover.

---

### Post by ke2wombo on 2019-01-27
Yeah, good point, thanks!  I never figured out what the hell was going on but it had something to do with the firmware because I installed the latest OpenWRT and everything worked.

---

### Post by TheFu on 2019-01-27
So - please use the **Thread Tools** button near the top to set this thread as "solved." Help the community out.

---

