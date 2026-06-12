---
title: "How to do clean re-install"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by JauntyJack on 2009-12-14
Ok, minor problem. I have had my Mom running Jaunty for months and it was great. I upgraded her to Karmic when it came out. Last week she wanted to play her DVDs on  computer, so I ran the appropriate commands from the Comprehensive Multimedia and Video Howto:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 

Immediately it got weird. Now her big monitor goes to sleep part-way through boot up and only the laptop monitor works. I have to hit escape repeatedly to wake the main monitor. Also, even when it's awake, if I play a video in VLC, it will show on the small laptop monitor, but the big monitor, showing the same desktop and all the same elements, has only an empty gray box where VLC is on the laptop display. I didn't think this was possible.

Anyway, now Mom can't even do email because the display keeps konking out. I think I should just do a clean re-install of Karmic without all the video tricks. But I'm not sure how to execute the install. I have the live CD, but how do I start it re-installing over the current install? I tried searching the forum but often the really obvious things are just assumed. Tips?

---

### Post by chaanakya_chiraag on 2009-12-14
If you want to keep all the files intact **and you have a separate home partition**:
1) Select manual partitioning in the disk management part of the installation and click "Next".
2) Click on all your partitions and assign them to the appropriate mountpoints.  When you get to the root partition, check the "Format" checkbox. **For all other partitions, DO NOT check the "Format" checkbox.**
3) Complete the installation as usual.  You should be good to go.

If you selected the default partitioning scheme, where everything is on one partition:
1) Copy all the files you want to save onto a flash drive or something. **THEY WILL BE LOST IN THE REINSTALLATION PROCESS** if you fail to do so.
2) Select manual partitioning in the disk management part of the installation and click "Next".
3) When you get to the next screen, only one thing should be there.  Right-click on it, select "Options" or something similar, set the mountpoint to "/", the Format to "Ext3", and **check the "Format" checkbox**.
4) Complete the rest of the installation as normal.  When you boot up the reinstalled Karmic, copy all the files back over from the flash drive and you should be good to go!

If you have any questions, don't hesitate to ask, because some of this may be unclear and if you do this improperly, you may lose all data.
- Chiraag

---

### Post by JauntyJack on 2009-12-14
Good information, thanks!

> **chaanakya_chiraag said:**
> 
If you selected the default partitioning scheme, where everything is on one partition:

I think I will go with this. Mom has only a few files and I can export her Firefox profile etc.

> **chaanakya_chiraag said:**
> 
4) Complete the rest of the installation as normal. 

Silly question: to get the reinstall started, I change the boot order and have it boot from the live CD, correct? 

Thanks.

---

### Post by Geoff918 on 2009-12-14
> **JauntyJack said:**
> Good information, thanks!



I think I will go with this. Mom has only a few files and I can export her Firefox profile etc.



Silly question: to get the reinstall started, I change the boot order and have it boot from the live CD, correct? 

Thanks.

That should be fine. Your BIOS may already be setup to select the CD before the HDD. There's almost always a key that can be pressed to change the boot order on the fly as well (less permanently).

---

### Post by chaanakya_chiraag on 2009-12-15
Usually it's the Escape key or the Delete key.  To change the boot order permanently, the key is usually F1

---

### Post by Bucky Ball on 2009-12-15
Reinstall what works for a 'Mom' computer and allow your own machine to live on the bleeding edge. When you have all the bugs sorted out with 9.10 (which will probably still be some time by the looks) then 'upgrade' her machine if you really think it's necessary.

I built a machine for my mother-in-law and use the theory 'if it ain't broke, don't fix it'. Makes no difference to her having the version released 10 minutes ago! That machine will be LTS releases only, as are mine (but I need them rock solid 95% of the year).

I haven't helped probably, but I often wonder why people 'upgrade' to the 'latest' bug filled version when their machines are working perfectly. I imagine she doesn't do much beyond vids, music, word processing and email. What difference? Just make it stable for her. That's all moms are generally interested in (and, in my experience, most non-tech users).

---

### Post by JauntyJack on 2010-01-02
> **Bucky Ball said:**
> Reinstall what works for a 'Mom' computer and allow your own machine to live on the bleeding edge. When you have all the bugs sorted out with 9.10 (which will probably still be some time by the looks) then 'upgrade' her machine if you really think it's necessary.

I built a machine for my mother-in-law and use the theory 'if it ain't broke, don't fix it'. Makes no difference to her having the version released 10 minutes ago! That machine will be LTS releases only, as are mine (but I need them rock solid 95% of the year).

I haven't helped probably, but I often wonder why people 'upgrade' to the 'latest' bug filled version when their machines are working perfectly. I imagine she doesn't do much beyond vids, music, word processing and email. What difference? Just make it stable for her. That's all moms are generally interested in (and, in my experience, most non-tech users).

Completely right and very good advice. I've never been an early adopter, don't know why I did it with Karmic. Mom gets the rock steady setup from now on.

---

