---
title: "Looking for a firewall that uses different rules when connected to different networks"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by bcat on 2007-06-07
I just installed Ubuntu Feisty on a Toshiba Satellite A35 laptop. (All the hardware seems to work perfectly. Go Ubuntu! :D)

Anyway, I plan to use it mostly on my own wireless network at home, but I also want to connect to the Internet at public wifi hotspots. Now, at home I want all my other computers to have full inbound access (for SSH, Samba, etc.). However, when I'm not connected at home, I want to block all inbound traffic to keep snoopers out.

I tried Firestarter, but it doesn't seem to support choosing a ruleset based on what network I'm connected to. Is there some other firewall I can use that does support this?

---

### Post by Mr. C. on 2007-06-07
You can create your own ruleset config files, and have them loaded upon network bringup.

See this thread for creating such a script: [http://ubuntuforums.org/showthread.php?t=159661&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=159661&highlight=firestarter)

Once you get it working manually, you can next automate it to run based upon network address (eg. run your permissive rules when you connect to your home network, and restrictive set when elsewhere).

MrC

---

