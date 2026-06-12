---
title: "Compaq F700 Broadcom wireless not working after Wubi install"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by ozzy19 on 2008-07-29
Hi, I just acquired a Compaq F700 laptop and I'm trying to get an install of hardy working through wubi. I've been messing with ndiswrapper and the broadcom cutter thing and I've now gotten to a point where the networking manager will show the known wireless connections in the area, but when I try to connect to any of them, it tries for a couple of minutes and then gives up. I know that these connections work when I'm using the computer under Vista from the same location. 

Sorry if I haven't included enough technical detail, if it is necessary then let me know how to acquire it and I'll do my best. 

Thanks!

---

### Post by tashmooclam on 2008-07-29
You are doing things correctly. The problem is Broadcom card and no Linux native drivers for it. I had a similar problem, and my fix was get an intel card on ebay. After it was installed, and turned on, it just worked because Ubuntu contains real drivers for the Intel card. Wrappers and whatnot are ways to let Ubuntu use the Windows drivers. I found it unsatisfactory. Others may have had great success. I wasted more of my brain and time trying than the $25 it cost for an Intel card on eBay. Just my two cents. I consider the $25 my "Ubuntu wireless tax".

---

### Post by ozzy19 on 2008-07-29
Thanks for the quick response...I guess the biggest problem with that is that it's a laptop and the wireless is all internal. Oh well, I guess I'll just get to use ubuntu on the desktop.

---

### Post by tashmooclam on 2008-07-29
Here is a case that it evidently worked out. 
[http://ubuntuforums.org/showthread.php?t=803281](http://ubuntuforums.org/showthread.php?t=803281)
It also may be easy or hard to replace the card. On my laptop there was a little door on the bottom of the laptop, it was not hard to swap it out. 
Maybe others who have more ability/experience can guide making your wireless work.Wait for them to read/reply to your post.

---

### Post by zxscooby on 2008-07-29
I have the same laptop and have working wireless.
I used the same procedure in the post that tashmooclam pointed out. 
did you blacklist bcm43xx?

```
sudo rmmod bcm43xx
```

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

---

### Post by ozzy19 on 2008-07-30
Thanks for the help everyone! One of the linked articles solved my problem! You guys rock.

---

