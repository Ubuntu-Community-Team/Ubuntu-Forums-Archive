---
title: "Cannot create partition on HD - tried 3 OS's"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by Tohya2042 on 2010-08-17
So...

My sister's computer was riddled with viruses and she was having problems getting windows vista to work.  Here is what I've tried so far:

Using vista recovery disk to reformat HD - failed "unable to create partition"

Wipe computer clean using "Dban" - failed 
Wipe computer clean using "Killdisk" - success

Reinstall vista from blank state - failed "unable to create partition"

Install windows xp from blank state - failed "unable to format partition"

Install Ubuntu from livecd - failed both auto partition and custom partition 
-- tried ext4 and ext3 systems

Run Ubuntu from livecd and run GParted
--create ntfs partition on /dev/sda - failed

[I]"Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy."
"Warning: partition(s) 5 on /dev/sda could not be modified, probably because it/they is/are in use."[/I]

I have no idea why it won't partition the drive.  She has a Dell Inspiron 1318 with the A06 bios. (standard inspiron, no changes from base package dell offers)  I was hoping to use Ubuntu to force it to format as ntfs so windows might have a chance at actually working.  Anyone have any idea what could be wrong?  I'm really hoping I can figure something out short of just replacing the drive.

Thanks in advance.

---

### Post by earthpigg on 2010-08-17
possible bad news: [http://www.tomshardware.com/news/bios-virus-rootkit-security-backdoor,7400.html](http://www.tomshardware.com/news/bios-virus-rootkit-security-backdoor,7400.html)

possible good news: [http://www.ehow.com/how-does_4809843_removing-bios-virus.html](http://www.ehow.com/how-does_4809843_removing-bios-virus.html)

i've never encountered a bios-level virus myself, nor attempted the solution above, so i cannot state for certain either link is relevant to your problem based on any actual personal experience.

---

