---
title: "Loss of Wireless After Last Update"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by happyytilton on 2014-09-30
Lost wireless ability after an update on this past Friday.
I went through the same steps as outlined by **"Hadaka"** on the 3rd page of this post: [http://ubuntuforums.org/showthread.php?t=2225781](http://ubuntuforums.org/showthread.php?t=2225781)
It just seemed the logical procedure, but was no help.
I do have internet connectivity through the Ethernet hardline, but because we use wireless exclusively, that connection is not easily accessed.

---

### Post by happyytilton on 2014-09-30
Forgot to mention that this is the same machine and there are no changes since that posting.

---

### Post by happyytilton on 2014-10-03
After going through all the previous steps, the final resolve was actually too simple.

This problem was solved by the following steps:
  
[LIST=1]
[*]Type "**bcm**" in [Ubuntu Software Center]("https://en.wikipedia.org/wiki/Ubuntu_Software_Center"), 
[*]Install "Installer Package for firmware for the b34 driver" (firmware-b43-installer) 
[/LIST]

Credits go to [iBelieve]("http://askubuntu.com/users/109543/ibelieve") for these steps.

---

### Post by Hadaka on 2014-10-03
Hi, Let's see if we can make this as painless as possible.
First, you are correct,you didnt do anything, the rules changed
on the driver you had...linux-firmware-nonfree...so we are going
to use the regular b43 driver for your wireless. You do NOT and
should NOT be online to load this,infact please disconnect you ethernet
cable to avoid any possible conflict.
go here ->[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
and follow the yellow brick road on post #7
if you have problems,questions,post back. If there is any confusion
stop and post back.
thanks.

---

### Post by Hadaka on 2014-10-03
Great !!
Looks like you found a fix while i was posting one.
please mark your thread solved
how to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

