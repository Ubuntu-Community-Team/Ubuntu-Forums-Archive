---
title: "Hot-swap?"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by DBrocks on 2009-09-05
Hey guys. Well, I was just wondering if Ubuntu supported hot-swap of SATA II devices natively. I have an ICH7 chip set. Will it work automatically or do I need a script/program to detect a new drive? Thanks!

---

### Post by Paqman on 2009-09-05
Yep, all SATA devices should be hot-swappable on all OSes. It's part of the SATA specification.

---

### Post by DBrocks on 2009-09-05
Regardless of chip-set? I thought you needed the correct chip-set for it to work.

---

### Post by Paqman on 2009-09-05
You might be right. Just because the spec says they're supposed to be hot-swappable, doesn't mean every manufacturer is going to follow the spec to the letter. Linux has a lot of trouble with ACPI on some boards because OEMs don't implement it properly.

Only one way to find out I guess ;)

---

### Post by DBrocks on 2009-09-05
I would probably write a script to unmount all file systems, then use hdparm to stop the drive. Then I could just pull it out. The problem arises when trying to re-register the drive. Not sure how to go about doing that. Ideas?

---

