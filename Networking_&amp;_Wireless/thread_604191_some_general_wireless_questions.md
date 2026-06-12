---
title: "some general wireless questions"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by travis2 on 2007-11-05
Hi all,

Ok, I am pretty Linux illiterate.  Just installed Ubuntu 7.10 on my X31 Thinkpad, completely replacing my version of WinXP (this is not my primary computer, but I hope to move to Linux full time).

My home network is (was) setup with a MAC Filter and WEP 128 bit HEX and I was using Key 2.  I could never figure out how to get wireless working after studying a number of forum appends.

After disabling the MAC Filter and specifying Key 1, I was able to connect using nm-applet.

In a number of appends the directions are to disable the MAC Filter - is this not supported in Linux?

Using nm-applet, is there any way to specify using a key other than Key 1?

Should I create a script to invoke wireless access?  Seems few on this forum are using nm-applet - is there a reason for this?

Thanks for what I guess might be obvious answers.

--travis

---

### Post by kevdog on 2007-11-05
I dont think network manager can change the key, however if you connect from the command line, you can specifiy the key number.  The general procedure how to connect from the command line is in my signature.  You will need additional options to specify the key index in addition to what is stated in the thread.  man iwconfig has some examples that should meet your needs.

---

