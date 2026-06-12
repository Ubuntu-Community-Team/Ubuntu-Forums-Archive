---
title: "Help! any changes in the permissions tab undo immediately"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by bestron on 2010-11-16
Please help, I wanted to change the property "allow executing file as a program" for some shell script program to make it execute

the problem is when I try to change anything in the permissions tab it returns back immediately by itself,
that when I check the checkbox besides my desired property -to make the file executable- it unchecks immediately without any warnings

any solutions? :confused:

[Edit] This happens even when I'm root

---

### Post by mcduck on 2010-11-16
sounds like your files are on FAT or NTFS filesystem, or on optical media like DC or DVD.

None of the above supports ownerships and permissions as Linux uses them. Instead the permissions are set for the whole filesystem at the time it's mounted.

You can either move your file to some Linux filesystem, or try changing the mount options to add execute permissions to all files on the current fs.

---

### Post by Drenriza on 2010-11-16
What exactly is it your trying to change permissions for?
How do you try and change these premissions?
What should the permissions be? just execute?

---

### Post by bestron on 2010-11-16
Thank you [/B][mcduck]("http://ubuntuforums.org/member.php?u=17309")**, you are right my files were on an NTFS** **filesystem, I moved them to the Linux filesystem and** **it DID work**, [B]Permissions changed and the file executed.

And yes, just wanted to execute this file (it's a game) 

by: Right Click-->Properties-->permissions.

---

