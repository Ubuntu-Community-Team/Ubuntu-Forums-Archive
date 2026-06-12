---
title: "network manager only seeing wired network suddenly"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by digitalcharisma on 2007-03-28
So heres how it started..  

I finally shut down the other day after customizing my desktop and I couldnt log back in.  I searched for a result and found that it was because i was using panel transparency, and there was some bug.  So, as a post said, I CTRL ALT F1'd and typed 

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

that worked beautifully.... 

BUT, now my network manager can only see the wired network, and doesn't see wifi at all. 

I tried reinstalling network manager, but no luck.  Any ideas at all? 

under the network admin thing, it shows eth1 as disconnected.  

thanks for the help

---

### Post by chili555 on 2007-03-28
Are you trying to have wired and wireless working at the same time? NetworkManager doesn't permit that. From Ubuntu Wiki:> The computer should use the wired network connection when its plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.If I misread your issue, post back.

---

### Post by digitalcharisma on 2007-03-28
No, not at the same time.  Only wireless.

---

### Post by digitalcharisma on 2007-03-28
One more thing to add...   

I disabled eth1 inside network admin, rebooted, and now it sees the networks, but cant connect.  The little dots just spin, and neither of them light up. 

Any ideas?

---

### Post by digitalcharisma on 2007-03-28
for whatever reason, it started working again after i closed the screen, walked two blocks, and opened it.   

no idea....  the magic of ubuntu.

---

### Post by nuir on 2007-08-29
I had similar problems, sometimes the network admin would show a message saying the wired network was ready, even when no cable was actually connected to my laptop! 

I haven't found any permanent solution, but just like digitalcharisma, if I close the screen, or put the computer in stand-by mode, the problem is solved...

---

