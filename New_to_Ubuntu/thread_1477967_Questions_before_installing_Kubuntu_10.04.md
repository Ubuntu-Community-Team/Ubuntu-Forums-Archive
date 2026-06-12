---
title: "Questions before installing Kubuntu 10.04"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-09
I want to install Kubuntu 10.04 replacing Ubuntu 10.04. Other existing OS is windows 7 which i want to keep intact.

My questions are:
1. Is Kubuntu's manual partitioning same as Ubuntu 10.04
2. What will happen to Grub Loader after Kubuntu is installed?
3. If in case installation fails before finishing (as it failed 3 times while installing ubuntu 10.04). Will it affect Grub loader?
4. Will I be able to log on to windows 7 if Kubuntu's installation failed?

---

### Post by rasmus91 on 2010-05-09
> I want to install Kubuntu 10.04 replacing Ubuntu 10.04. Other existing OS is windows 7 which i want to keep intact.


go to

System->Administration->synaptic package manager

Search for Kubuntu. Install Kubuntu from here.

Reboot. Choose Log in in KDE

Go to Synaptic and remove Ubuntu if you don't want it.

---

### Post by SKhan on 2010-05-09
> **rasmus91 said:**
> go to

System->Administration->synaptic package manager

Search for Kubuntu. Install Kubuntu from here.

Reboot. Choose Log in in KDE

Go to Synaptic and remove Ubuntu if you don't want it.
ok but i already knew what you told me. now tell me will it be any different from installing Kubuntu from live CD? and please also answer my question above, if possible.

One reason i don't want to install kubuntu from synaptic package manager is because i live in a place where electric load shedding is very frequent now a days. So i am sure downloading will be discontinued in the middle.

---

### Post by rasmus91 on 2010-05-09
> 1. Is Kubuntu's manual partitioning same as Ubuntu 10.04
2. What will happen to Grub Loader after Kubuntu is installed?
3. If in case installation fails before finishing (as it failed 3 times while installing ubuntu 10.04). Will it affect Grub loader?
4. Will I be able to log on to windows 7 if Kubuntu's installation failed?

1. Yes, i think so.

2. if you install from synaptic = no change. If you install from live = reinstalled

3. me no knows.

4. perhaps. you will if you install from synaptic.

> ok but i already knew what you told me. now tell me will it be any different from installing Kubuntu from live CD? and please also answer my question above, if possible.

One reason i don't want to install kubuntu from synaptic package manager is because i live in a place where electric load shedding is very frequent now a days. So i am sure downloading will be discontinued in the middle. 

But that doesn't really matter if you install from synaptic, cos then you can just log in to Ubuntu (gnome) again, and start synaptic, and try again.

> now tell me will it be any different from installing Kubuntu from live CD?

It's really that easy, and you will have no problem if you get interrupted. Installing from Synaptic is best IMO because you will already have the core files, and you wont be messing with GRUB. (Ubuntu And Kubuntu have the same Core files, just runs a little different when it comes to the Desktop.)

hope it helped.

---

### Post by SKhan on 2010-05-09
> **rasmus91 said:**
> 1. Yes, i think so.

2. if you install from synaptic = no change. If you install from live = reinstalled

3. me no knows.

4. perhaps. you will if you install from synaptic.



But that doesn't really matter if you install from synaptic, cos then you can just log in to Ubuntu (gnome) again, and start synaptic, and try again.



It's really that easy, and you will have no problem if you get interrupted. Installing from Synaptic is best IMO because you will already have the core files, and you wont be messing with GRUB. (Ubuntu And Kubuntu have the same Core files, just runs a little different when it comes to the Desktop.)

hope it helped.


Ok let me try it from synaptic package manager

---

### Post by SKhan on 2010-05-09
thanks rasmus91 Kubuntu successfully installed from synaptic package manager.
but i will still delete it after sometime, and reinstall it again. because actually i want to delete this partition in order to merge it with 10GB unallocated space.

---

### Post by kio_http on 2010-05-09
> **SKhan said:**
> thanks rasmus91 Kubun successfully installed from synaptic package manager.
but i will still delete it after sometime, and reinstall it again. because actually i want to delete this partition in order to merge it with 10GB unallocated space.

The difference from fresh install, is that GNOME and other Ubuntu software remains.

---

### Post by SKhan on 2010-05-09
> **kio_http said:**
> The difference from fresh install, is that GNOME and other Ubuntu software remains.
true, that's understood. Well i was too excited to get a fresh kubuntu install and get my lost 10gb space that i have just installed kubuntu from live CD. Today's my first day on Kubuntu, and not more than 15th day on linux, i am facing some problems in kubuntu which i will post in another thread.

---

### Post by rasmus91 on 2010-05-10
> thanks rasmus91 Kubuntu successfully installed from synaptic package manager.
but i will still delete it after sometime, and reinstall it again. because actually i want to delete this partition in order to merge it with 10GB unallocated space.

Oh, yeah, i guessed you might have something like that. isn't there a way to do that without formatting? :s

> The difference from fresh install, is that GNOME and other Ubuntu software remains. 

Well if you don't want that software either you can just go to synaptic :D

> true, that's understood. Well i was too excited to get a fresh kubuntu install and get my lost 10gb space that i have just installed kubuntu from live CD. Today's my first day on Kubuntu, and not more than 15th day on linux, i am facing some problems in kubuntu which i will post in another thread. 

Good luck! :)

---

### Post by SKhan on 2010-05-10
> **rasmus91 said:**
> Oh, yeah, i guessed you might have something like that. isn't there a way to do that without formatting? :s
well i don't have more than average partitioning experience. Another choice might have been extending neighbor partition thus merging it with unallocated space. but i am very new to linux so i don't know how to do it from linux. but it was impossible from windows7  because hard disk already had the maximum number of partitions allowed. and the partition next to unallocated space was a ext4 partition which windows7 doesn't understand.

---

