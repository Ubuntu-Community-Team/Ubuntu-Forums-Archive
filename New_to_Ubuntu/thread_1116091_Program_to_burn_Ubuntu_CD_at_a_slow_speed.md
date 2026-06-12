---
title: "Program to burn Ubuntu CD at a slow speed"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by drdjnicholls on 2009-04-04
[B]
Can anyone help?
As on a previous occasion (which was resolved) with an earlier version of Ubuntu, my PC now seems to only accept a CD which is burned slowly. However, the slowest speed on the CD burning programs I have is 10, which repeatedly creates CDs that produce read errors when trying to boot up Ubuntu (the latest version)

My question is: can anyone direct me to a freeware CD burning program that gives the option for slow burning?

Thanks

David
[/B]

---

### Post by anjilslaire on 2009-04-04
K3B, in the repo's, is my preferred disc burning app.

---

### Post by clive littlewood on 2009-04-04
Hi

Try Brasero in the repos.

It will burn at 4x Speed.

Works for me           :p

Clive

---

### Post by Old_Grey_Wolf on 2009-04-04
drdjnicholls,

Did K3b or Brasero work for you?

Neither of them let me burn at less than 10X even on old computers that I used to burn at 2X a year ago. So, it's not my hardware. 

After 8.10 included the "Make a USB startup disk" under System > Administration, I've been using USB sticks rather than CDs. 

---------

However, if someone on the forum can answer, I would like to know why I can not now burning CDs (CD-R) at less than 10X. There just is no option to select anything less than 10X.

This is not a problem normally; however, I'm trying to get a laptop working that can not boot from a USB stick.

---------

drdjnicholls,

Sorry if I am hijacking your thread.

---

### Post by batharoy on 2009-04-04
This is a limitation of the media (disk) itself.
Any program wether it be Brasero, K3b etc.. will only burn as slow as the media will allow.

---

### Post by Old_Grey_Wolf on 2009-04-04
> **batharoy said:**
> This is a limitation of the media (disk) itself.
Any program wether it be Brasero, K3b etc.. will only burn as slow as the media will allow.

What-ever-you-say; however, I have a Windows XP computer with an older version of imgburn that can burn at 4X on the same CDs that won't burn at less than 10X with new CD burning software. 

But, like I said above, I am using USB sticks now so it's not a problem most of the time.

---

### Post by Old_Grey_Wolf on 2009-04-05
drdjnicholls,

I was able to get a good iso burn using the **cdrecord** command.

Your command will vary but mine was ```
cdrecord -overburn -driveropts=forcespeed -v -eject speed=4 dev=3,0,0 ubuntu-8.10-desktop-i386.iso

```

I had to use the command ```
cdrecord -scanbus
``` to determine what dev=X,X,X should be.

---

