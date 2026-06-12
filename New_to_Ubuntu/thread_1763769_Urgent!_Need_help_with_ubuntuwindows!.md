---
title: "Urgent! Need help with ubuntu/windows!?"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by isebastian on 2011-05-20
ok so im a windows xp professional user but I needed some software that only ran on linux so i downloaded the cuurrent live cd version ( natty ). I've used ubuntu in the past without problem, until now. I rebooted my computer with the live cd in, selected installation alongside with windows. Everything looked perfect until the installation finished and I rebooted my computer. Instead of the normal OS selection menu. I get a message : "Grub error: no such device and a whole bunch of numbers". After playing with it for a little i got the boot menu to show up but only windows worked. Whenever i selected ubuntu it just crashed. I've tried about everything right now both of my disks have been wiped out...Reinstalled a fresh copy of windows...reinstalled ubuntu about 10 times and now im stuck again with the first error...How can i fix this? I need to get both OS running together....I don't know if it helps but this is my computer ( really suckish ): 
Dell Dimesion 2400
Pentium 4 2.3 ghz
Ram 768 mb
2 40 gb ATA hard drives... totalling 80gb
on-board 64 mb graphics processor


I am a total Linux noob please help me!I know I can fix everything by just reinstalling windows and deleting everything else but I need ubuntu.

---

### Post by duke.tim on 2011-05-20
Sounds like Grub has a problem...
Generally you need to install Windows before Ubuntu. Windows tends to be picky about where it is installed (what partition).
You could always install ubuntu on a virtual machine like [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
or install it under windows xp with wubi.

This looks like very similar to your case I would suggest looking at them :)

[http://www.linux.com/community/forums?func=view&catid=3&id=6094](http://www.linux.com/community/forums?func=view&catid=3&id=6094)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408)

---

### Post by wolfen69 on 2011-05-20
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Go to the section on repairing grub.

---

### Post by duke.tim on 2011-05-20
Natty uses Grub2! But the repair process looks like it could work.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Immolatus on 2011-05-20
When in doubt go with the "razor". the common component here is the disk you are installing from. You may have a bad file if you burned it @ over 8x. I burn all mine @ 8x or 4x to avoid burn errors and then archive them. Any time I have ever had this issue it was because I burned the disk too fast.
You might also try installing in windows with wubi if it will work with xp.

---

