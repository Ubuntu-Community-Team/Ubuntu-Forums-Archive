---
title: "NetworkManager (?) stalls during session start"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by jbro on 2007-05-10
Hello,

First, I want to say that the wireless support in Feisty is the best I've seen in any distro. I've got a ThinkPad with the Intel 2915ABG wireless card and use WPA security, and this is the first distro that I could connect just by selecting the access point and entering my WPA key.

When I first installed Feisty, everything was great. Connections were fast and solid. However, after a few days, during which I was installing software and testing out various GNOME things, I started to see some odd behavior. Now, when I start a GNOME session, NetworkManager doesn't immediately start working (I assume that the notification area icon with the two dots and arrows going between them indicates that NetworkManager is working.) The session start seems to hang with the splash still on the screen for about two minutes. During this time, there is no NetworkManager icon, no disk cranking, and obviously no network connection. After two minutes (this is very consistent) the keyring manager dialog appears asking for my keyring password. At this point, the NetworkManager icon also appears. Once I enter my keyring password, everything works fine. It's just that the two minute pause is rather annoying.

I suspect I may have done something bad to my GNOME session, as I was experimenting with sessions and what they do, but I have tried to delete ~/.gnome/session and I have ensured that gnome-keyring-daemon starts with the session (this was a guess, I don't really know if it's necessary,) but I still get the long delay.

Any suggestions on how to eliminate this pause or any clues on what to look for would be greatly appreciated. At this point I'm not even sure if it's a keyring issue or a NetworkManager issues or both.

Thanks and regards,
jbro

---

### Post by TedyBear on 2007-05-11
I've had the icon with the two dots disappear all together during a update. I haven't been able to restore that icon and now the only way I'm getting my wireless to work is to run wpa_client in a terminal and then run dhclient... There's the icon of two computers which shows the status of wlan0 and I have entered my WPA key into that software but it's not able to log on to the network. It's frustrating to work around the problem every time I start my computer.

---

### Post by jbro on 2007-05-11
I solved the problem.  It had nothing to do with what I thought it was. I had installed Beryl with AIGLX and this was causing the session start stall. I uninstalled Beryl to move to an XGL installation and the problem went away.

---

