---
title: "Remote Printing thru SSH"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by WaddleDee on 2008-04-28
Hello Everyone.

I am pretty new and in experianced in things like this.

I have a report I need to print, but I don't have a printer, but I have one at work. How do I print from Open Office at home, to appear at work with only SSH? Is it possible?

Thanks in advance

---

### Post by jhetrick62 on 2008-04-29
I just posted a howto on this subject as I just finished testing this morning.  Good timing for your question.

[http://ubuntuforums.org/showthread.php?t=774213](http://ubuntuforums.org/showthread.php?t=774213)

You could also learn how to install FreeNX and the remote printing option.  I have FreeNX installed and it works fine for me, but I did not install the remote printing option and can't advise you on that.

Goodluck,
Jeff

---

### Post by WaddleDee on 2008-05-06
Oh thanks

I don't think I can do that. Here is my senario:

I am at home and I need to print at work. I connect to [domain].com:2222, and that forwards me to a further server that has my homefolder and that is where I do my ssh'in. That is the only way my admin would let me connect and she won't change anything, because of some yadda about she just made everything work for once and does not want to screw it up again. Oh ya, and the printer is lan, not connected to any comp's.

Please forgive if it would work this way, I then don't understand the tut. Any more suggestions? :(

---

### Post by kevdog on 2008-05-06
Can you explain your situation a little bit more -- are you trying to ssh and jump from 3 computers?  Do you need to employ a bit of reverse tunneling to bypass a firewall?  It looks like what you want to do should be possible, however you need to clarify some info and be as specific as possible about your server, client (middle machine?).

---

### Post by jhetrick62 on 2008-05-06
I agree with Kevdog.  If you are at work and have to log into a remote terminal that contains your home folders, from there ssh to your home system and use the reverse tunneling that I specified above.  If it's different than that, then explain.

Jeff

---

