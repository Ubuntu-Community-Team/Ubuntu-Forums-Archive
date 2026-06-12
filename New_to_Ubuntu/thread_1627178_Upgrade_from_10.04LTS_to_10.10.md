---
title: "Upgrade from 10.04LTS to 10.10"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Trandre on 2010-11-21
I successfully installed the 10.04LTS alongside win7 on my laptop computer. And used it for some days. Then I tried to upgrade through softwaresources and so on. Everything was successful so far. But when the computer restarted to go into the fresh install it reboots when I choose Ubuntu, and I am not able to start the Ununtu partition. 

Anybody who knows a solution to this issue?

Sysinfo

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=176157&stc=1&d=1290339651

---

### Post by Trandre on 2010-11-21
Additional info. The same thing happen when I use recovery partition

---

### Post by coffeecat on 2010-11-21
Boot up a live Ubuntu CD. It doesn't matter whether you use a 10.04 or 10.10 CD. Go to this page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the bootinfo script and post the contents of the RESULTS.txt file. Don't forget to enclose the output in code tags when posting. You can do this with the # icon which you can find in the toolbar just above the message field.

Hopefully, with that information we might be able to see what has gone wrong.

---

### Post by Trandre on 2010-11-21
Thank you Coffecat, I downloaded and burned the file to a cd. But on a closer look to "how to" I had to be in a Linux environment, which is my problem in the first place. Only the win 7 is working. Is there anything i can do to get this info from an Win7 environment? I have dual boot

---

### Post by coffeecat on 2010-11-21
> **Trandre said:**
> on a closer look to "how to" I had to be in a Linux environment

....

Is there anything i can do

> **coffeecat said:**
> Boot up a live Ubuntu CD.

:wink:

No, you can't run it in Windows 7 but the script is easily run in a live Ubuntu CD desktop environment.

**EDIT:** just a thought. In your first post you say 'alongside win7' which I took to be a conventional dual-boot with Ubuntu in its own partition. Is that so, or are you running Ubuntu in Wubi within the Windows C: partition?

---

### Post by Trandre on 2010-11-21
:-) I decided to downgrade to 10.04 after I was prompted to give a password I did not have :-)

---

