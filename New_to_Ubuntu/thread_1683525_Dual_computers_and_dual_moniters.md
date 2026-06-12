---
title: "Dual computers and dual moniters"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by mschuh21 on 2011-02-07
Hey I'm just wondering if there is any way I could hook my mac up to my ubuntu computer and be able to run both side by side so I could move my mouse between them.

Thanks,
Michael

---

### Post by themusicalduck on 2011-02-07
Look into using Synergy. It works over a network and you can share your mouse and keyboard between computers.

Install quicksynergy from the software centre. Pretty sure you can find the same software online for mac too.

---

### Post by 1clue on 2011-02-07
Yes, but not the way you're describing.

It's called a remote X11 connection.  I recommend doing it through ssh.  It's been a long while since I tried a full X connection, though so I don't have exact directions.

What this will get you is you will have a window on your mac that is your Ubuntu desktop.  If you like you can disconnect your Linux monitor and do everything from the mac.

---

### Post by mschuh21 on 2011-02-07
Thanks, I got it working.

---

