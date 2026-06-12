---
title: "Networkmanager behaviour on user switch"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by FordTaunus on 2009-03-13
Hi everybody,

I've been reading in this forum for a while, but now that I have a little problem, I thought I'll join and put the question to the knowing.

I searched for this topic, but didn't find anything describing my particular problem, so I thought it was safe to start a new thread.

Maybe a bit on hardware and software: I'm using an akoya mini e1212, which I was told is very similar to a Wind U100. I scrapped the pre-installed XP and installed Ubuntu 8.10.

The scenario: User1 uses the computer, including a wireless network connection. He hibernates the computer.
User2 comes along, starts the computer up, and he doesn't get the NetworkManager icon at the top bar. Still, the network connection is available. It seems like Ubuntu connects in the background to the previous WLAN connection. The 2nd user can't disconnect or switch to another WLAN connection, because he cannot access the NetworkManager.

Is this expected behaviour? How could I change it that every user sees the taskbar icon and can change to another connection?

Thanks for any help :D

Regards,

Ford

---

### Post by lswb on 2009-03-13
User2 can try Main Menu/System/Preferences/Sessions/Startup Programs, scroll down to "Network Manager-Network Manager Applet" and make sure it is checked as enabled. If it is not listed, click Add and for Name enter "Network Manager", for Command enter "nm-applet --sm-disable" and for Comment enter "Network Manager Applet" (The "Command" field is the only one that is really important, you can enter whatever you like for the Name and Comment fields)

If the icon does not appear right away try logging out and back in again. If it still does not appear make sure you have a Notification Area on one of the panels.

---

