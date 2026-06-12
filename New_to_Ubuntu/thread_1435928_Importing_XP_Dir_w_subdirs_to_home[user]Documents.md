---
title: "Importing XP Dir w/ subdirs to /home/[user]/Documents"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by FredVanH on 2010-03-22
Hi.  I want to copy my personal data files from an old XP machine where they are all in 119 subdirectories of C:\MyFiles\.

I have copied that structure to a portable USB Flash Drive to facilitate the copy.

I want to copy that structure with its files to my new Ubuntu 9.10 machine's /home/[user]/Documents (I'll take care of any necessary conversions afterwards).

After I insert the flash drive, can I just drag the structure into /home/[user]/Documents, or will the fact that it came from XP screw it up - making it necessary instead to make each subdirectory all over again in the Ubuntu file browser before I drag the files in?

Thanks for any advice,
Fred

---

### Post by dearingj on 2010-03-22
You should be able to just drag it into /home/user/Documents.

---

### Post by Kakers on 2010-03-22
From what I can gather in your post... You copied the folder MyFiles from the C drive on your windows machine to your USB/External Hard Drive and now wish to move these from your portable device to the Documents folder in your home?

The fact that they came from a windows xp machine should not make a bit of difference, they should just go straight on there, the very most I see you make have to do is change the permissions with chown or chmod but I doubt you will have to even do that... :D

---

### Post by FredVanH on 2010-03-22
Thanks, dearingj & Kakers, for your super-timely responses! I have now tried it and it works perfectly.

---

