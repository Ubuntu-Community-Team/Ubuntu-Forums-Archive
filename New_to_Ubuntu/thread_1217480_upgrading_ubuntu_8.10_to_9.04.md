---
title: "upgrading ubuntu 8.10 to 9.04"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by thvdbroek on 2009-07-19
I just upgraded fom 8.10  to ubuntu 9.04
During the upgrade process no probems occurred.
I have chosen to keep the existing configuration file.
 
When restarting the computer i see the ubuntu logo and the time bar. It looks quite normally. 
After a few seconds I see horizontal bars black and white (just a zebra)
At the top of the screen I see some small ubuntu logos in green and purple.
The computer is hanging. Nothing happens further.
 
I have a HP Compaq PC DC5000/MT with a compaq screen 7500. No flat or TFT screen.
 
I also started in the recovery mode. However it does not help.
 
I hope someone can help me.

---

### Post by ByteJuggler on 2009-07-19
If you (try to) boot up (up to the "zebra" display), can you get a text mode login prompt by pressing ctrl-alt-f1?

---

### Post by TeoBigusGeekus on 2009-07-19
Do I smell ATI?

---

### Post by CaptainMark on 2009-07-19
Sounds like it. What graphics card have you got, if its an ati your gonna want to start asking your friends if they have a spare you can borrow to sort it out.

---

### Post by thvdbroek on 2009-07-19
> **ByteJuggler said:**
> If you (try to) boot up (up to the "zebra" display), can you get a text mode login prompt by pressing ctrl-alt-f1?
 
Thank you for your reaction.
The answer at your question is no.
Even ctrl-alt-del does not work

---

### Post by hyperdude111 on 2009-07-19
Not ctrl-alt-del thats a windows command. 

Try alt-ctrl-F1 it opens a virtual terminal.

---

### Post by ByteJuggler on 2009-07-19
> **thvdbroek said:**
> Thank you for your reaction.
The answer at your question is no.
Even ctrl-alt-del does not work

Do you have a 9.04 LiveCD, and if so does it startup OK?  (I presume you do not have one as you probably upgraded online, but its worth asking.)

---

### Post by thvdbroek on 2009-07-22
> **ByteJuggler said:**
> If you (try to) boot up (up to the "zebra" display), can you get a text mode login prompt by pressing ctrl-alt-f1?

First i thank you for your reply.
Pressing ctrl alt del does not work. the computer is hanging. Nothing works.
Even ctrl alt del does not work.

---

### Post by Durden on 2009-07-22
> **thvdbroek said:**
> first i thank you for your reply.
Pressing ctrl alt del does not work. The computer is hanging. Nothing works.
Even ctrl alt del does not work.

ctrl + alt + f1

not

ctrl + alt + del

---

### Post by thvdbroek on 2009-07-22
> **hyperdude111 said:**
> Not ctrl-alt-del thats a windows command. 

Try alt-ctrl-F1 it opens a virtual terminal.

Thank you for your reply.

pressing alt ctrl f1 does not work.
the computer is hanging.

---

### Post by thvdbroek on 2009-07-22
I do not have a liveCD.
When ubuntu offers a possibility to upgrade why not.
I think it is better to create a liveCD.
Installing the 8.10 from a live CD gave no problems.

---

### Post by CaptainMark on 2009-07-23
Try this, download ubuntu 9.04 iso from this link [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
burn this image to disk, and boot from the live cd. Make sure you burn an image disk not a data disk (sorry if this sounds patronising but not sure what level your at)
Just post back here with the results if you can use the 9.04 live cd. 
Reason we need to know is 9.04 and 8.10 use a different system for visual processing if you cant use the live cd its probaly a driver problem

---

### Post by LewRockwell on 2009-07-23
> **thvdbroek said:**
> I do not have a liveCD.
When ubuntu offers a possibility to upgrade why not.
I think it is better to create a liveCD.
Installing the 8.10 from a live CD gave no problems.

yes, save all your valuable files and then use a new 9.04 LiveCD to reinstall

I do not recommend upgrading for examples such as this

Testing with the newer LiveCD and then reinstalling is much better

.

---

