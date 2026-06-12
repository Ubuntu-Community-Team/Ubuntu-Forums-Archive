---
title: "Ubuntu 10.04 Random Lockups Intel 82855"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by slamsteel on 2011-03-25
Hello There.
Im new here.
I just want to know why my ubuntu 10.04 locks randomly.
When i load maybe two or more tabs it locks.
Also when i watch youtube.Ubuntu will lock.
When it locks,Keyboard is not working.Only mouse is working.
But the audio is still going on (on youtube)
I'll have to hard shutdown it.
My drivers are from X-Updates
Thanks.

---

### Post by 123456789123456789123456 on 2011-03-25
> **slamsteel said:**
> Hello There.
Im new here.
I just want to know why my ubuntu 10.04 locks randomly.
When i load maybe two or more tabs it locks.
Also when i watch youtube.Ubuntu will lock.
When it locks,Keyboard is not working.Only mouse is working.
But the audio is still going on (on youtube)
I'll have to hard shutdown it.
My drivers are from X-Updates
Thanks.

What are the system specs?
does not sound like a ram issue, possibly a kernal issue.  are you running the latest kernal?  if so, try the previous kernal.  you may also consider upgrading to 10.10.
you can do that by changing the update profile, in symantic package program for all normal releases, there is also a section in update manager that will allow you to change the release from long term to normal releases.

---

### Post by slamsteel on 2011-03-26
HP Ze4900
1024mb of ram (992mb left)
Intel 82855 (32mb)
1.5ghz Intel Pentium/Celeron M.(I forgot because i removed the stickers)

_____________________
I don't like upgrading to 10.10
It seems like 10.10 doesn't want my graphics card.
Because when i install x-updates
then edit the xorg.conf
Change it to intel
Then after restart.
The drivers will work.
But the animations will be like destroyed.
The animations has distorted effects.
But the drivers work.
Compiz is enabled.
But the effects are unstable.
_____________________________
Edit:
I haven't upgraded the kernel.
I will upgrade it know.
I'll let you know if the problems still shows.

---

### Post by mikewhatever on 2011-03-26
Most likely, [this is the cause]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes"). Those 8xx chipsets are no longer supported by Intel, which has resulted in major problems when running the latest versions of xserver.

---

### Post by slamsteel on 2011-03-26
Thanks for the replies.
I already updated the kernel
I'm now on 2.6.34.
The problem is not currently showing.
I hope this fixes my problem.
By the way.
I'll keep this thread updated, if the problem occurs again.
I'm doing the things i'm doing when the problem occured.
But the problem did not occur.
Thanks

Edit:
The problem occured while downloading multiple .torrent files.
The kernel update didn't actually solve the problem :)
If i can't fix this problem.
I'll just go back to XP :D

---

### Post by slamsteel on 2011-03-27
The kernel update didn't fix the problem.
I experienced it again.
What will i do?
My head will burst.:(

---

### Post by slamsteel on 2011-03-27
Oh.Nevermind.
I've given up on Ubuntu.
I already uninstalled it.
Thank you for helping.
Bye ubuntu :)

---

