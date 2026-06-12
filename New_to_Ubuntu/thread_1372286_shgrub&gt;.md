---
title: "sh:grub&gt;"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by battleshipterry on 2010-01-04
I have the below error on 2 pcs now happens right after I select ubuntu in duel boot selection menu(seconds after pc comes on).as this is the first part of booting up I have limited commands.it sees partitions when I type ls.not sure how to get to the right one and boot from grub on it.grub may be corrupt.I think it has something to do with beta grub version as I had just reloaded Wubi in windows and was doing first updates to Ubuntu 9.10 and had just rebooted.but I have a laptop that has very same errorand it has had 9.10 on it for a month or 2.Any help would be great thanks.



GMU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists
possible command completions. Anywhere else TAB lists possible
device/file completions. ]

sh:grub>

---

### Post by tom.swartz07 on 2010-01-04
> **battleshipterry said:**
> I have the below error on 2 pcs now happens right after I select ubuntu in duel boot selection menu(seconds after pc comes on).as this is the first part of booting up I have limited commands.it sees partitions when I type ls.not sure how to get to the right one and boot from grub on it.grub may be corrupt.I think it has something to do with beta grub version as I had just reloaded Wubi in windows and was doing first updates to Ubuntu 9.10 and had just rebooted.but I have a laptop that has very same errorand it has had 9.10 on it for a month or 2.Any help would be great thanks.



GMU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists
possible command completions. Anywhere else TAB lists possible
device/file completions. ]

sh:grub>

99.9% of the errors that ive seen from dual booting with WUBI is because Windows fragments the files and things get lost. Its very unlikely that its GRUB itself that has the error. Even though its still in beta, it has the stable structure of the previous version underneath the hood that makes it very robust.

I would suggest that if you are seriously considering using Ubuntu on your computer, re-install using the cd, rather than WUBI. WUBI is mainly used for people who want to test out Ubuntu (or any flavor of Linux) on their computer without any strings, and then remove it just like a program. 

Unfortunately, there isnt one concise way to restore grub to a busted wubi installation. Perhaps you could boot to windows and run Defragmentation several times to clear up as much space as possible, but beyond that- I dont think theres much hope.


If you need assistance with the Dual Boot installation procedure, I would be more than happy to help you!

---

### Post by drs305 on 2010-01-04
So you are having the problem both in wubi and on another machine with a normal install? For Ubuntu, the Grub 2 beta version is the standard one for now (beta4).

Here is a guide to booting from the recovery prompt in Grub 2:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

Please note the special format of the "linux" command for wubi installs.

As tom.swartz07 offered, if you have questions, ask here and someone will try to answer them.

---

### Post by battleshipterry on 2010-01-05
Thanks for the help I just reloaded it in windows,it was easy that way.I have not did any thing with the acer laptop yet, it is also duel boot and has the sh: grub> error.but I did reload the older HP laptop that had the same problem.I must be doing something that causes this.I have seen this same problem 4 times on 3 different pcs it must be some thing I am doing.as an example: I know that trying to get my ATI TV Wonder card to work on desktop pc, changes the menu.lst file and now grub 2 does not use menu.lst but this is just a example. so this may be a type of a cause. but does not explain the laptops.I only load software from synaptic have not messed with the boot folder.At first I thought it was something in windows.
say Microsoft did a auto update that within windows deleted the grub file.this is a little of a conspiracy theory I guess but could happen if the evil empire don't like us duel booting Ubuntu in there OS.
I would love to be free of windows but I am a old gamer and my tv card will not record in ubuntu.The new WIFI Kodak printer has no Linux drivers(low priced ink and very good quality) And some other software will not work.I started using Linux with Mandrake 8.2 was over $60 at Circuit City years ago since then Linux has made great improvement (Thanks to Canonical and the Ubuntu community) so I am sticking with Linux it will win in the end I know. 
I could buy a tv card to work in Linux and I run wine and cross over but cant give up that wonderful printer :) and corel photo software.Anyway thanks both of you for replying I do appreciate it.

---

### Post by drs305 on 2010-01-05
Use the system that best suits your needs. Using Linux when you can and providing feedback will help in it's development.

If you are done with this thread, would you please mark it SOLVED via the Thread Tools link at the top right of the first post.

---

