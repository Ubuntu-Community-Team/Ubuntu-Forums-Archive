---
title: "Orange Screen Hang"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by mahimahi42 on 2009-03-27
Ack, this is annoying.

Ok, I've been using Ubuntu with Wubi for a few weeks now, and have fell in love. Lo and behold, my Dad had an extra Gateway tower that he didn't use, because of a possible virus. I snatched that opportunity up quick. So, on my Windows XP machine, I burned an 8.10 Live CD so I could put it on the Gateway and not give it access to the Internet in case there was a virus/worm. Well, I seemingly successfully installed Intrepid, so I was happy. Well, whenever I try to boot up, everything seems to go well, but then it hangs indefinitely (left it overnight to check) at the pre-GUI orange screen. I tried every option in the recovery mode, but I don't know if there's a command that will help me. If someone could help me out, it would be greatly appreciated!

---

### Post by perrti-y02 on 2009-03-27
Are you sure the hardware is sound in the tower? I had a similar problem which was due to a dodgy processor that had burnt out. I could install but not boot. I tried to reinstall and it hung. try booting off the live cd and see if it works. If that hangs I suspect it may be a hardware issue.

---

### Post by mahimahi42 on 2009-03-27
That might be an issue, but before I nixed the Windows XP that was on there, I booted that just to be sure the tower hadn't been damaged/eaten by my brother. It booted fine, but I didn't try any internet apps, because of the "virus". Dad said that certain cmd commands related to Internet access (ipconfig was a big one) didn't work. I'll try booting from the Live CD, and see if it works.

EDIT: I'm able to boot in Safe Graphics Mode on the Live CD. Is there something I can try here?

---

### Post by perrti-y02 on 2009-03-27
What do you know about this virus? I am simply hypothesising that that may be due to a hardware fault?

---

### Post by perrti-y02 on 2009-03-27
Not sure safe graphics mode is much use over normal graphics.

---

### Post by mahimahi42 on 2009-03-27
Knowing my Dad, it could be that he just has a lot of temp files. The only reason I did safe graphics was to see if it would work at all (it does). Should I try reinstalling Intrepid?

---

### Post by perrti-y02 on 2009-03-27
It might be worth a go but I fear you may get the same problem. It is always worth a second go.

---

### Post by mahimahi42 on 2009-03-27
Eureka! Success!

It works! But, I have a problem. For some reason, I'm stuck in safe graphics mode. Any ideas on how to change the screen resolution? I tried, you know, Screen Resolution, but it only had the default 640x480 as an option.

---

### Post by perrti-y02 on 2009-03-27
try running xserver config. I forget how but if you put it into google then it should give you some useful stuff. The screen will basically go crazy and the entire thing will reconfigure itself.

---

### Post by perrti-y02 on 2009-03-27
I think it is "Xorg -configure"

---

### Post by mahimahi42 on 2009-03-27
I tried that but it came up with

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock and start again.

But, .X0-lock is locked, so how do I unlock it so I can remove it?

---

### Post by rahul_bhise on 2009-04-09
may be this post will help
[http://ubuntuforums.org/showthread.php?p=6075895#post6075895](http://ubuntuforums.org/showthread.php?p=6075895#post6075895)

---

