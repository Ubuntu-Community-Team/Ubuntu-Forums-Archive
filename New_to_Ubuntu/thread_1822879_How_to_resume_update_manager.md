---
title: "How to resume update manager"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by aneshdas on 2011-08-11
hello friends,

I was trying to upgrade my ubuntu 9.1 to ubuntu10.04.3 LTS. 

I was using upgrade manager to do the same. 

but when the donload was almost 75%, the light went off.. 

can any one tell me how I can resume the updation?

 I took almost 13 hours before the powercut.

---

### Post by aneshdas on 2011-08-11
hello friends,

I was trying to upgrade my ubuntu 9.1 to ubuntu10.04.3 LTS. 

I was using upgrade manager to do the same. 

but when the donload was almost 75%, the light went off.. 

can any one tell me how I can resume the updation?

 I took almost 13 hours before the powercut.

---

### Post by westie457 on 2011-08-11
> **aneshdas said:**
> hello friends,

I was trying to upgrade my ubuntu 9.1 to ubuntu10.04.3 LTS. 

I was using upgrade manager to do the same. 

but when the donload was almost 75%, the light went off.. 

can any one tell me how I can resume the updation?

 I took almost 13 hours before the powercut.

The easiest way really is to download the 10.04.3 ISO and burn to a CD and then install over the top after you have moved all your personal files to a safe place. Upgrading through the Udate Manager is never a good idea as it can and sometimes fail for bizarre reasons.

---

### Post by aneshdas on 2011-08-11
But because I spent this much time(13 hours)........

and my cdrom is also not detecting any cd's? when i load a cd it is just blinking but I cannot open the drive..

---

### Post by Bart92 on 2011-08-11
> **aneshdas said:**
> hello friends,

I was trying to upgrade my ubuntu 9.1 to ubuntu10.04.3 LTS. 

I was using upgrade manager to do the same. 

but when the donload was almost 75%, the light went off.. 

can any one tell me how I can resume the updation?

 I took almost 13 hours before the powercut.

First try to run Ubuntu in recovery mode and check for broken packages
Then sudo update-manager

---

### Post by amjjawad on 2011-08-11
Best approach to upgrade is to do Fresh New Installation.

From terminal, please post the output of:

```
sudo fdisk -l

```Please wrap up the output with "CODE" tags OR highlight the output and click "#".
You just need to copy the above command and paste it into Termianl and yes, that's small "L" at the end.


If your CD Drive has some issues, you can go for LiveUSB.
[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There is no need to spend all that time, 13 hours? totally a waste.

Please, make sure to BACKUP your important files before doing anything.

If you have separate /home partition, you just need to format the root (/) partition during installing 10.04.3 but if you don't have then the installer will format the root (/) partition.
The above command will show if you have separate /home or not.

If you still want to spend XX Hours to upgrade, then it's your call :)

---

### Post by grahammechanical on 2011-08-11
Have you tried to start the upgrade again? You might find that much of what was downloaded is sitting in a temporary file and the upgrade will resume and only download the missing packages.

I do not say that this will happen for sure but I have noticed that with every update and upgrade all the necessary packages are downloaded and then the updates are applied. Packages are unzipped, old packages deleted, new packages put in they places, then everything is somehow hooked together.

Regards.

---

### Post by uRock on 2011-08-11
Duplicate threads merged. Third threads was closed. Please do not create multiple threads with the same content.

Regards,
uRock

---

