---
title: "No Wireless on HP laptop"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by Framewerk13 on 2008-05-25
Hi, I just installed ubuntu on my HP laptop and i've encountered a problem with the wireless internet.  I've gone through ubuntu wireless networking guide [https://help.ubuntu.com/8.04/internet/C/wireless.html](https://help.ubuntu.com/8.04/internet/C/wireless.html) and i have installed 'using windows wireless drivers' and followed the step by step of that, and when i went to install the driver, it came back with "invalid driver!'

Any help would be greatly appreciated!

---

### Post by Ayuthia on 2008-05-26
> **Framewerk13 said:**
> Hi, I just installed ubuntu on my HP laptop and i've encountered a problem with the wireless internet.  I've gone through ubuntu wireless networking guide [https://help.ubuntu.com/8.04/internet/C/wireless.html](https://help.ubuntu.com/8.04/internet/C/wireless.html) and i have installed 'using windows wireless drivers' and followed the step by step of that, and when i went to install the driver, it came back with "invalid driver!'

Any help would be greatly appreciated!
I am sure that this come to no surprise to you, but NDISwrapper does not like the driver that you are using.  I am not for sure what driver you used, but NDISwrapper does not use Vista drivers as of yet.  The best bet is to see if you can get the XP drivers for your laptop at [http://www.hp.com](http://www.hp.com).  Another option is to try the drivers from this site:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope that helps.

---

### Post by chinaxmsink on 2008-05-26
Now I know.Thanks you very much.---------------------------------------------------------------->We are the creators of beautiful handmade [copper sinks](http://www.china-sinks.com).

---

### Post by packman1234 on 2008-05-26
If you have the atheros chipset...go here.....   [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984). Especially if the HP laptop is new!!

---

### Post by Framewerk13 on 2008-05-26
Ok, I just tried to do use [https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)
but i came up with the same problem. i got to step 3 and it told me that bcmwl5.inf was invalid (and it was the one that i downloaded from the walk through)

my laptop isn't really new either I bought in fall of 06 so i'm not sure if it has the atheros chipset or not

---

### Post by Ayuthia on 2008-05-26
> **Framewerk13 said:**
> Ok, I just tried to do use [https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)
but i came up with the same problem. i got to step 3 and it told me that bcmwl5.inf was invalid (and it was the one that i downloaded from the walk through)

my laptop isn't really new either I bought in fall of 06 so i'm not sure if it has the atheros chipset or not

How about posting your lspci -nn (from the Terminal)?  Then we can tell what kind of wireless you have.  I am thinking that it is not, but we can see.  It could even be an Intel.

---

### Post by Framewerk13 on 2008-05-26
I just finished reinstalling unbutu and i went through the how to fix wireless link that was posted before, and it is now working. thank you all for you help!!

sorry about not knowing the proper terms for any of these things, this is my first time with linux and i'm having a lot of fun with it, and i hope i will be able to learn enough so i don't sound like a n00b when i'm talking about it.

Cheers-

---

