---
title: "Ubuntu 18.04 - Wireless connection failed"
date: 2018-11-01
forum: Networking &amp; Wireless
---

### Post by codepressor on 2018-11-01
Hi all, this is my first post here, thanks for the amazing knowledge information!

I'm having an issue with my wireless connection, the first ubuntu issue that I'm not able to solve by myself with the information available.
I've been running ubuntu 18.04 for a month with no issues. In the last 5 days or so I cannot connect to my wireless network, receiving the error:
Connection failed: Activation of network connection failed

I have a triple boot pc, Windows 10 connects fine to the wireless network, AV Linux (Debian) stopped connecting too at the same time, although I haven't used this system recently.
I've tried restarting network-manager with no success.
I can connect through wired connection to the router.
I have made no change to my router configuration.

Pastebin of the wireless script: [https://paste.ubuntu.com/p/2V3mzdHCBx/](https://paste.ubuntu.com/p/2V3mzdHCBx/)

Any help is highly aprecciated!

Thanks in advance for the time dedicated to this issue

---

### Post by Autodave on 2018-11-01
Some info on your system may help someone to help you.

---

### Post by codepressor on 2018-11-04
Hi,
I believe the wireless script result attached to my post has all the info needed for these cases, isn't that true?
I'm running Ubuntu 18.04 on a Lenovo Ideapad 110-15AST. The problem happens with any of the desktops available (unity, gnome, unity on wayland)
Wireless 802.11g/n

---

### Post by praseodym on 2018-11-04
Change the encryption mode in your router to pure WPA2-AES (CCMP), not mixed mode WPA/WPA2

---

### Post by codepressor on 2018-11-04
Thanks for the reply!
Amazingly, 9 days after the problem started I have now wireless connection on my linux distros having done nothing at all.
I suspect it was indeed some kind of network configuration that caused the problem, as both my linux ditros were affected at the same time.
If the problem returns I'll try that router configuration and report if it solves the problem.
Thanks!

---

### Post by codepressor on 2018-11-09
Hi!
After a dew days the problem returned. Sometimes I would have wireless connection and other time no connection, with the same error.
I changed the encryption mode in the router as suggested by [**[COLOR=#000000]praseodym[/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497") and, after a router reset, it worked! 5 days now with no break.
Thanks [**[COLOR=#000000]praseodym[/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497") for the tip!

---

