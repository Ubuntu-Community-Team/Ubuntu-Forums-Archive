---
title: "Partition Help"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by mrshmizzie on 2009-02-06
OK, so I decided to try my hand in Kubuntu after becoming familiar with ubuntu. I decided that I prefer Ubuntu and decided to reinstall it. I know am left with 3 partitions...1 with ubuntu, 1 with kubuntu, and 1 with windows vista. I want to split the 20 something gb from kubuntu between the ubuntu and vista partitions. I'm still fairly new with partitioning and I have used gparted. I just am not sure exactly how to split the space between the other two. Can anyone point me in the right direction?

---

### Post by crowhill on 2009-02-06
hey there

i once tried to play with a windows partition in gparted. i destroyed it so that i lost windows (well, honestly, i didn't care so much :)). so if your windows operating system is important to you i recommend that you don't play with the partition it is on, at least not with the help of gparted. 

if i were you i would give all of the 20g to ubuntu:)

---

### Post by cjv8888 on 2009-02-06
> **mrshmizzie said:**
> OK, so I decided to try my hand in Kubuntu after becoming familiar with ubuntu. I decided that I prefer Ubuntu and decided to reinstall it. I know am left with 3 partitions...1 with ubuntu, 1 with kubuntu, and 1 with windows vista. I want to split the 20 something gb from kubuntu between the ubuntu and vista partitions. I'm still fairly new with partitioning and I have used gparted. I just am not sure exactly how to split the space between the other two. Can anyone point me in the right direction?
Are any OS installed at the moment in the system and how are they positioned?

---

### Post by mpl34 on 2009-02-06
Scenario 1: If the kubuntu partition is in the middle of the drive map then it is an easy process with gparted. Just delete the kubuntu partition and resize the vista and ubuntu partition to gather the empty space adjacent them. 

Scenario 2: However if ubuntu is in the middle of your drive map it could be a difficult process as you will only be able to extend the ubuntu partition onto the 20gb of free space left over from deleting kubuntu. You'll then have to resize the ubuntu partition again reducing it by 10gb (make sure this 10gb is next to your vista partition). Then resize your vista partition to take on this 10gb.

I hope that make sense.

(In Scenario 2 the second resize of the ubuntu partition may take awhile as it will have to copy and move important system and user files in the process).

I hope this explanation is correct i'm no guru

---

### Post by mrshmizzie on 2009-02-07
The Kubuntu should be the second one on the drive. I just know gparted is a program not to be messed with unless you know what you're doing. Also another question...if I format and do end up being able to move the space between the two...do I just end up removing it (kubuntu) from the menu.lst? 

@MPL is there a program that you recommend? Thanks for all your help.

---

### Post by mpl34 on 2009-02-07
I wouldn't say that "gparted is a program not to be messed with" it's very basic and unless you are shrinking the vista partition or deleting swap partition its extremely unlikely you'll do any damage to your system.

If you drive map is
   Vista --> Ubuntu --> KUbuntu

It will be a very simple process to delete the kubuntu partition and expand the ubuntu partition (no formatting will be required).

---

