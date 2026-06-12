---
title: "&quot;sudo halt&quot; disables all wired devices plugged into the same router"
date: 2019-05-12
forum: Networking &amp; Wireless
---

### Post by becauseinternet on 2019-05-12
Yesterday, I ssh'd into my Dell PowerEdge T20 server running Ubuntu 18.04.2 LTS and ran "sudo halt" to shut it down. This normally works fine, the system usually shuts down and powers off. Except this time, a few minutes later, my internet went down.

I powercycle the modem, login to the router (Asus RT-AC56R) with my phone and reboot that. No joy. I wait a bit and try again. Nope. Modem refresh from the Spectrum site. Nada. The network still appears to be working, because the router can see whenever I unplug the modem. I get bored and try to get an ebook off my headless (note: wired) Banana Pi Nextcloud server, but I can't connect to that either. Couldn't login to the modem config through a browser on my wireless laptop, but I could access the router config. Alexa let out the saddest boop.

Nine hours and a call to Spectrum later, I check on my server. Instead of being powered off, it's hung on the TTY with a "system halted" message. Boot it back up and two minutes later, internet works! Everything works! I could even connect to the Banana Pi, which I thought had just hung--it tends to do sometimes.

Anything wired directly into the router was disabled by using "sudo halt" on Ubuntu. This included the modem, Pi, a couple switches, etc. Wireless still worked fine, since I could login to the router. I just reran it and confirmed that it's a repeatable bug. Except this time it hung on the Ubuntu shutdown progress bar screen. Shutting down the system normally through the GUI works fine. The "poweroff" and "shutdown -h now" commands also work as expected.

Not sure where to even start troubleshooting this one. It could be a combo of Ubuntu and the PowerEdge's crappy onboard networking. Maybe something PoE related? I'll get my LAN Tap from work tomorrow and see if it's throwing out anything packet sniffable.

---

### Post by TheFu on 2019-05-12
I suppose we should be using **sudo systemctl something** at this point.

The systemctl manpage has descriptions for the halt/poweroff/shutdown/reboot targets.  Looks like **sudo systemctl halt** should work. Same for poweroff, shutdown and reboot.  Turns out rescue and suspend are a valid targets too.  These are coded to be full _systemd start {target}_ stuff.

No clue how to do any of this with a GUI.  I reboot and shutdown servers all the time - well - as needed during weekly scheduled maintenance. Have never seen the issue above.  I could see where the GUI target in systemd might interfere with the server targets to shutdown a system.

---

### Post by kpatz on 2019-05-13
Seems odd that a halted server took down everything on the LAN... maybe it put something on the port that disabled the router's switch somehow?

In any case, I found running **sudo halt** on my 18.04 VMs just resulted in them "shutting down" but staying "powered on" and frozen... much like your server did.  Better to run **sudo shutdown -h now** if you want to power down.  If you want to use systemctl, use **sudo systemctl poweroff**.  Or to reboot, **sudo systemctl reboot**.

Me... I've been using **sudo shutdown** for so many years... this new systemctl stuff just messes me up.  Heck, poweroff/halt/shutdown are just symlinks to systemctl anyway, so the end result is the same.

---

### Post by becauseinternet on 2019-05-16
No yeah, I have no problems using other shutdown commands, I just thought it was a really interesting bug.

I stuck the LAN-tap in between the server and router and fired up tshark to see what it was doing. Looks like it spit out two NAT-PMP packets before everything died: "Map TCP Request" and "Map UDP Request." Right after those packets, there's a bunch of ICMP "Destination Unreachable" packets between the server and router before everything stops. Sort of looks like it borked NAT on the router somehow, but still no clue how or why everything is fixed immediately by powering off the machine completely.

---

