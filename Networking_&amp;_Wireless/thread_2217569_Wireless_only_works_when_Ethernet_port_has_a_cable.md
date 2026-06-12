---
title: "Wireless only works when Ethernet port has a cable in it"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by rion2 on 2014-04-17
Hi everyone,

I was happily using Lubuntu 12.04 for the last month without any issues, so I decided to install 14.04 and see if that would add anything to the experience. I wiped the HD on my Dell X1 (Centrino, 32bit CPU, had to use the forcepae install option) and installed 14.04. I ran into problems trying to connect to wireless networks: During the install it just wouldn't work, so I skipped it.

After the install completed I rebooted and logged in. I could not find the Wifi applet. After a few hours I realized I had to right-click on the 'task bar' area at the bottom of the screen and enable it. Unfortunately it shows "No wireless networks available" even though I'm just a few feet away from dozens of access points. After fiddling around some more I found that if I plug in an ethernet cable I can see wireless networks, but as soon as I unplug the ethernet cable from my gigabit switch the wireless networks disappear and all I see is "No wireless networks available".

Has anyone else seen this issue? I'm running an Intel(R) PRO/Wireless 2200BG Wifi card.

---

### Post by kalehrl on 2014-04-18
This is a known bug.
Use 'nm-applet' command until it is fixed.

---

### Post by rion2 on 2014-04-18
Thanks, that did the trick!

---

### Post by KBD47 on 2014-04-19
To make it permanent:
go to preferences
default applications for lxsession
autostart
and in the box put: nm-applet
click on: add
Do a restart and it should be in the panel.

---

