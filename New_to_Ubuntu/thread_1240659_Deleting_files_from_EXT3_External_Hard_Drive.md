---
title: "Deleting files from EXT3 External Hard Drive"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by wattage on 2009-08-14
Hello. This question is going to sound silly, but here goes.

I have a 500GB external hard drive that I formatted as a single EXT3 partition. I've been using it for a while and need to clear off some space to make room for some big video files. So I clicked a few files and pressed delete on the keyboard. The files instantly disappeared, with no confirmation.

I don't need the files back. But the space they were taking up has not freed-up yet. How do I "empty the recycle bin"? Or how would I get the files back if I wanted them?

Originally, 300 of the 500GB were used. I need to load 400GB of videos. So after clearing away 250+GB, I thought I would be all set. But the only way I was able to 'clear' the space was to reformat the external drive. This worked of course, but it's less than ideal.

Please help. What am I doing wrong? What (obvious) step am I missing? I've used NTFS-formatted external drives with no difficulty in the past. This is my first time using EXT3 (which seems to handle big files much more efficiently).

Thank you!

---

### Post by LinuxRules1 on 2009-08-14
When you delete a file on a USB device linux puts it in a hidden file named .Trash-1000(or some other number). when you unmount the drive it should ask you if you want to empty the trash. if not, just delete the .trash-1000 file(it won't stay on the disk when you delete it).

---

### Post by aysiu on 2009-08-14
Press Control-H, look for the hidden .Trash or .Trash-1000 folders, and hard-delete them (press Shift-Delete and not just Delete).

---

### Post by bodhi.zazen on 2009-08-14
The trash is indeed hidden  It is located in ~/.local/share/Trash

---

### Post by wattage on 2009-08-15
\\:D/

That did the trick! Thanks for the quick and spot-on answers. Hidden files. I would not have thought to look there.

---

