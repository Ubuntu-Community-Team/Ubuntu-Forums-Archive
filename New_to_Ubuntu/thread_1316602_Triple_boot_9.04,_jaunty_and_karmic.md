---
title: "Triple boot 9.04, jaunty and karmic"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by Rodemire on 2009-11-06
Good morning,
I received my copy of Karmic today and i will install it as soon as i get home.
I just need some confirmation that i am on the right track. I dual boot Jaunty and XP at the moment, both of which are on the same harddrive. Since i read about some problems with the Karmic install i decided to test it before removing Jaunty. I have a second harddrive and am planning on installing Karmic on it. 
Do i need to watch out for anything for this installation? That is, any hints and tips i need to know of?
Secondly,if the installation goes well,how can i safely remove Jaunty without messing up?
Note: I have read about Grub 2 and how to update it with changes and i have backed up all my Jaunty data.
Thanking you all in advance for all your help.

---

### Post by louieb on 2009-11-06
Should install and set up booting XP and Jaunty just fine. 
> how can i safely remove Jaunty without messing up?

What do you want to do with the space? You could  wait 6 months and install v10.4 in it..

---

### Post by mikechant on 2009-11-06
> Secondly,if the installation goes well,how can i safely remove Jaunty without messing up?

Assuming that you've extracted any data you need from the Jaunty partition/s, and that you are booting via grub with its config files in the relevant Karmic partition, you can just delete/reformat/reuse the Jaunty partitions with no ill-effects.
But as per above if you are intending to upgrade to Lucid (10.4) next year then you might as well keep the Jaunty partition/s until then and install 10.4 over them at that time.

Personally I have 3 root partitions - 1 & 2 used for current/previous or current/next versions of Ubuntu, and the third one for experimneting with other distros (currently running Ubuntu Studio)

---

### Post by aktiwers on 2009-11-06
Why  not test it in Virtualbox? 
I would always go for virtual machines if you are doing more than dualboot.

---

### Post by Rodemire on 2009-11-06
I actually hadnt thought about it but that makes a lot of sense. I will put another distro on that partition. Thanks a lot guys.
I hope the install goes smoothly.

---

### Post by oldfred on 2009-11-06
I would make your new harddrive as the first drive so grub2 installs on the new harddrive. Then if you have issues with Karmic you can switch drives back and still boot with out having to reinstall old grub. 

I like to have an operating system on each drive and its boot in its harddrive. Only the first drive has the current boot and also the chainboot to the other drives.

---

