---
title: "Lucid shuts down unexpectedly"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-05-20
I upgraded (Syn. Pkg. Mgr.) to Lucid a week ago. When I walk away from the computer for 30 minutes (more or less), the computer shuts itself OFF. I have to "re" power up. I've looked at the power settings in Screensaver and saw they were set to 30 minutes and spin the disks down, but I don't know if that is the "culprit" here.

Anybody know what causes a power down without the menu item "shutdown" being selected, please let me know.

---

### Post by Crafty Kisses on 2010-05-21
Hello,

It's kind of hard to say why it shut down, there could be many reasons, overheating, driver issues, etc. We can try and narrow it down though to see what's causing this issue. Can you post a couple of logs so others and myself can look?

```
cat /var/log/kern.log
dmesg
```

Post the results, than I or somebody else can help you out further.

---

### Post by Mark_in_Hollywood on 2010-05-21
Dear Not in Montana:

I ran the commands cat and dmesg. They are lengthy and both scrolled off the terminal screen. When I copied and pasted what was left I received this message from [www.ubuntuforums.org:](www.ubuntuforums.org:)

The following errors occurred with your submission:
You have included 9 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again. 

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

I don't use "Smileys" and couldn't see "images" in the text. Thanks for your trouble.

---

### Post by lanetherif on 2010-05-21
> **Mark_in_Hollywood said:**
> I upgraded (Syn. Pkg. Mgr.) to Lucid a week ago. When I walk away from the computer for 30 minutes (more or less), the computer shuts itself OFF. I have to "re" power up. I've looked at the power settings in Screensaver and saw they were set to 30 minutes and spin the disks down, but I don't know if that is the "culprit" here.

Anybody know what causes a power down without the menu item "shutdown" being selected, please let me know.

I have run a similar problem with yours. [http://ubuntuforums.org/showthread.php?t=1477907](http://ubuntuforums.org/showthread.php?t=1477907)

As I mentioned in above thread, using kernel 2.6.32-21 has somewhat solved the problem. May be you should give it a try. :)

---

### Post by Mark_in_Hollywood on 2010-05-21
Ahhh... I read the thread/post, but I'm having the shutdown problem after more than 30 minutes, not 10 minutes. It's not likely to be a heat problem. Karmic worked quite well for 6 months and no such problems. Why would Lucid "overheat" the cpu? And, I'm using the CPU Montor on the panel and rarely do the 4 cores go (and stay) over 800MHz. (overclocked AMD can run about 3.2gigHz.)

---

### Post by Mark_in_Hollywood on 2010-05-22
While I can see no reason for the improvement, I have changed the Power Management settings in Screensaver. This 'puter is NOT a laptop. It has NO battery. ('cept CMOS battery). Whatever problem I had with the machine arbitrarily shutting down is gone. The solution is not understood. At least by me.

---

