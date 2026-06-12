---
title: "Ubuntu 10.04 boot splash freeze when disk checking was on but power got out"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by mrblackgold on 2011-05-21
i started ubuntu 10.04 and it started checking my hard drive for disk errors it was 83% complete it was working fine but it suddenly my computer restarted because of my power cable got out of switch. i put it back then started ubuntu again but it kept freeze on the boot splash screen where four dots are. now i cant boot in to the main desktop and not even login screen. What do i do to repair this thing..

---

### Post by Gone fishing on 2011-05-21
Start it up in recovery mode and read the errors probably the automatic disk checking if failing and you will need to manually use fsck

[http://linuxpoison.blogspot.com/2009/04/how-to-checkrepair-fsck-filesystem.html](http://linuxpoison.blogspot.com/2009/04/how-to-checkrepair-fsck-filesystem.html)

[http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html)

---

### Post by mrblackgold on 2011-05-21
i cant understand a word of it. too difficult for me is there any other way to solve this thing.

---

### Post by Gone fishing on 2011-05-21
OK start in recovery mode (you might have to click escape when grub starts)

Then select file system check (fsck) and reboot (I'd do this also in recovery so you can see what happens) hopefully this will work. If not start up on a live CD and open a terminal from the terminal run 

fsck -y /dev/sda5

assuming /dev/sda5 is you root partition and unmounted

---

