---
title: "Need help: Update preparations - 8.10 / 32 bit to Karmic Koala 64 - ext 3 to ext 4"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by KarenAK on 2009-12-30
Christmas vacations are here, family is gone - it's finally Linux time !

However, still considering myself very much the Linux noob, I am a bit nervous about updating my system..... took me 2 days to evict Windows from my system and have Ubuntu running smoothly last April.

So, here is what I intend to do:


[LIST]
[*] Change from the 32 bit version of Ubuntu 8.10 to the 64 bit version of Karmic Koala
[*]Change ext3 format to ext 4
[*]Change partitions so that /home gets its own partition (I was told that it'll make future updates easier)
[/LIST]

However, I would settle for a less drastic overhaul of my comp if you fine people here tell me it's not really necessary....

My questions are:


[LIST]
[*]How do I save the current configuration so I do not have to start from scratch after the upgrade. I especially hate the thought of having to go through the confusing horror of getting sound working again. Or have flash enabled and all that.
[/LIST]
[INDENT]As a first step I did the FEBE backup for firefox and copied my /home directory to an external drive. Now I need to know about the other steps.
[/INDENT]
[LIST]
[*]Since all data (except home) is stored on external drives does it really make sense / is it really necessary to change the file system to ext4 ?
[/LIST]
[INDENT]And: Am I right in thinking that I could keep ext3 on the comp and reformat the external hard drives to ext 4 ? (or would that be pointless ? I really could use some enlightening advice here...)[/INDENT]
[LIST]
[*]Is there a way to get a list of the software currently installed ?
[*]Anything else I need to consider before the upgrade ?
[*]Any How-To Links you can recommend ?
[/LIST]

Any help is much appreciated.
Thanks in advance !

---

### Post by top_culprit on 2009-12-30
EXT4 is stable now , and default in ubuntu 9.10 .
It greatly increases HD performance , which can lead to better battery life .


Having a separate home partition is a good thing as it saves your configuration , when you upgrade you ubuntu next time .
You just need to format root partition and leave home as it is .
When new ubuntu is installed , all your settings are same as they were before  .





Main Advantage of EXT4 is speed . For separate home partition , you will have to reinstall anyway .
Weigh you options and decide between EXT4/EXT3 .





[clickme]("http://ubuntuforums.org/showthread.php?t=261366") to get  a list of installed software .

I will not recommend it , as sometimes it can install libraries / softwares which are no longer supported or are deprecated .
There is a risk of installing conflicting libraries.






As for most important step , you have already done it ,  by backing up all your data .

---

### Post by KarenAK on 2009-12-30
Thank you for replying !

How much space should I allocate to the /home partition ?

---

