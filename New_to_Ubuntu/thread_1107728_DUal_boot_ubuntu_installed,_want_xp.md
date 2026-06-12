---
title: "DUal boot ubuntu installed, want xp"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by spiepie on 2009-03-27
Hi
I have installed Ubuntu and loving it but ......I need to have XP for work:(

Trying to create a partition for XP -about 10GB but cant find the option to create a new partition in Gparted.
Any ideas please
thanks for your time
si

---

### Post by overdrank on 2009-03-27
> **spiepie said:**
> Hi
I have installed Ubuntu and loving it but ......I need to have XP for work:(

Trying to create a partition for XP -about 10GB but cant find the option to create a new partition in Gparted.
Any ideas please
thanks for your time
si

Hi and welcome, if you are using gparted from the live cd of Ubuntu then you will have to select and edit ubuntu partition to resize it for the space needed for xp. You may also have a look [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Paqman on 2009-03-27
One thing you might not be aware of: you cannot make any changes to a partition that is in use (ie: it is "mounted")

So you can't change your main Ubuntu partition while running Ubuntu. To get around this, just boot up your LiveCD and use Gparted from there. Since you're running off the LiveCD your disk partitions aren't mounted (except for your swap partition, just right click and choose "swapoff" to unmount that if you need to)

---

