---
title: "mini keyboard help"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by djyoung4 on 2010-11-06
So I just got a new mini keyboard ([http://www.smklink.com/index.php?id=Nzc5]("http://www.smklink.com/index.php?id=Nzc5")) made by smk-link.  Its perfect for what I need but I have only gotten the mouse portion and the top buttons working.  Has anybody used one of these or know of any possible tutorials on how to get the actual keyboard part working.  any help is greatly appreciated

---

### Post by djyoung4 on 2010-11-09
bump

---

### Post by djyoung4 on 2010-11-10
bump

---

### Post by djyoung4 on 2010-11-19
bump

---

### Post by djyoung4 on 2010-12-28
bump

---

### Post by ThunderSaid on 2011-01-27
I'm seeing this same problem. I've got a little extra information. I'm using Ubuntu 10.04 LTS. The mouse and all of the special media-center-type buttons along the top work as expected; not all of them do anything because I haven't assigned them to any functions, but using 'xinput -test <idnumber of the mouse>' I can see that each button press is received by the computer as a press event and a release event.
 
The keyboard appears to have no working buttons, but a little digging shows that to be wrong. Again using the 'xinput -test <idnumber for the keyboard>' method, I can see that certain keys are sending events to the computer. The "working" keys seem to be the shift keys, the alt keys and the ctrl keys. I put that in quotes because I have no idea if they're sending the right key events or not, but they're at least sending something.
 
As an extra piece of information, both the keyboard and mouse get detected as "ORTEK W/L KEYBOARD AND MOUSE." One is listed as a mouse, and one is listed as a keyboard.
 
Sorry I don't have any help (I'm a total newbie), but I figured that more information might help any altruistic users that might know what's going on.

---

### Post by Scarborough on 2011-03-13
Hey djyoung4,

I also just got the same hand-held SMK-Link mini wireless keyboard/"mouse" combo (VP6360) ([http://www.smklink.com/index.php?id=Nzc5](http://www.smklink.com/index.php?id=Nzc5)) and its "mouse" functions work, but not the keyboard. 

As ThunderSaid noted, mine also registers as having an Ortek board (ID 05a4:1700 Ortek Technology, Inc.) according to lsusb. I found this post that solved the same issue for another device (the Ortek PBK-1700) with the same chip:

[http://ubuntuforums.org/showthread.php?t=1594007](http://ubuntuforums.org/showthread.php?t=1594007)

I'ven't taken time to try out the work-around yet, but it seems to have worked for a few others. Hope this helps.

          -- Scarborough

---

