---
title: "wicd and firestarter"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by irober02 on 2007-08-02
After a few frustrating months using networkmanager (reliable WPA connections with Intel 3945 but very unreliable WPA connections with my atheros-chipped devices + madwifi driver), I'm giving wicd a try. (All my computers are running Kubuntu Feisty.)

It seems to do a better job at making a reliable connection and makes it easy to set a static IP. It also connects the machine at boot-up without a user logging in which suits me for a couple of desktops.

However, I can't get the firestarter init script to set up the firewall at boot time although it runs fine after I've logged in. I haven't yet been able to diagnose what's going on at boot time (boot logging seems pretty suboptimal at the moment). :-(

I did have firestarter running from a script in /etc/NetworkManager/dispatcher.d/ but can't see that wicd has functionality like that and so have reverted to the firestarter installed /etc/initi.d/firestarter. I have simplemindedly tried re-ordering the startup symlinks in /etc/rc2.d so that firestarter runs after wicd but still no luck. :-(

Does anybody know how to configure things so that firestarter runs correctly at boot with wicd?

---

### Post by pezz on 2007-10-03
I have got wicd now for 1 month and like it very much but I have the same problem and haven't found a solution. I also tried to modify de boot sequence of de programs but no luck...:-(
I have even another problem and that is that wicd needs my root password for accessing my networkcards. 

Can someone help?!?!

Pezz

---

