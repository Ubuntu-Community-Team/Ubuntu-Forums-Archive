---
title: "Have Thunderbird in Ubuntu and Win7 share the same folders"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by hanzj on 2011-08-27
Hello,
I have  a laptop that has Windows 7 on one partition and Linux on the other. I have Thunderbird installed on both Windows and Linux. How can I make both of them share the same folders and messages? It would be a waste to have duplicate emails.

---

### Post by 73ckn797 on 2011-08-27
This was just asked and solved in this post: [http://ubuntuforums.org/showthread.php?t=1701190&highlight=thunderbird](http://ubuntuforums.org/showthread.php?t=1701190&highlight=thunderbird)

---

### Post by desnaike on 2011-08-27
You will have to read the entire post and decide if it's woth it .

[http://ubuntuforums.org/showthread.php?t=203524](http://ubuntuforums.org/showthread.php?t=203524)

---

### Post by hanzj on 2011-08-27
I wonder whose advice is better, the one posted by desnalike or the one by 73ckn

---

### Post by oldfred on 2011-08-27
I created a FAT32 partition in 2006 and have shared my Firefox & Thunderbird profiles ever since. I converted to NTFS about 3 years ago when I changed Ubuntu to 64bit.

I do not suggest writing directly into your Windows system partition. Much better to create a shared NTFS partition. I also copy my profiles to my portable when traveling & copy back when I return. I have upgraded and used same profiles since the begining. I have tried to update XP & Ubuntu to the same version about the same time but not always.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by 73ckn797 on 2011-08-28
I have not tried to link T-Bird across OS's since I only have Win XP in Virtualbox on my desktop and Ubuntu only on a laptop and rarely have to go into it. I saw that post and read through it out of curiosity more than for a solution. It looked like it would work but there are likely other simpler solutions.

---

### Post by Mark Phelps on 2011-08-28
Agree with oldfred ... in that, personally, I feel any "solution" that has you updating your Windows OS partition from INSIDE Ubuntu is a bad idea.

Much better to have a shared DATA partition, that way, their's no OS to get corrupted or boot loaders to get damaged.

---

