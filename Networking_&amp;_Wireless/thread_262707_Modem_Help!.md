---
title: "Modem Help!"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by someonedumb on 2006-09-22
Hi, I'm still unable to get my modem to work, here is what I've figured out so far.

I have the same behavior on 3 different dial up software packages, pppd, wvdial, and the GUI one. The modem initializes, dials the number, does the buzzing and beeping, turns off the sound(all exactly normal so far), but then the connection suddenly closes.

With wvdial it prints this:
Carrier detected, waiting for prompt.
Connected, but carrier signal lost! Retrying...

My computer is set to dual boot Ubuntu and Windows XP. The modem works *perfectly* in Windows XP, so I can rule out line noise or other hardware or ISP failures.

I've been leaning toward blaming the driver as the problem. It is a Lucent Winmodem, and I can't seem to find any evidence that it is supported with the kernel version Ubuntu uses (2.6.15-26 correct?) Should I be thinking about getting a real modem?

Any ideas?

---

### Post by someonedumb on 2006-09-22
bump, please help :P

---

### Post by acefreely on 2006-09-22
Been a long time since I have messed with modems, but I remember enough to hopefully point you in the right direction...

Probably whats going on is that there is an error with your username / password to connect.  I used to have to write my own connections scripts most of the time, it was something like...
expect: username?
send: [email]user@att.net[/email]

expect: password?
send: pass

Don't remember the exact syntax, but something like that.  Anyway what you need to do it try to connect using a terminal and see what the ISP is asking for and enter them manually.  You may have to write a custom script...

---

### Post by someonedumb on 2006-09-22
I've verified the username/password many times (including just now when I read your suggestion). I think I'm in the correct ballpark atm, been trying to navigate through linmodems.org. Its the most poorly laid out driver website I've ever visitied and I'm finding it very hard to figure out which file to download. ScanModem is an alright tool though.

---

