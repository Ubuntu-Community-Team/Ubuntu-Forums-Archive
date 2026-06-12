---
title: "NTFS mounted... Can't find &quot;My Documents&quot;"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by stoneface22 on 2009-08-27
Hi all --
     I've successfully (?) mounted my sda1 NTFS drive using the GUI that I installed via synaptics... 
     My problem now is that I can't find "My Documents" or "My Music" to import them to rhythmbox.  Where am I going wrong? Thanks,
 -- Keith

---

### Post by sp0tz on 2009-08-27
If I remember right, the "my documents" folder is stored here:

C:\documents and settings\YOUR USER NAME\my documents

so then you would want to open the ntfs drive, and then open documents and settings, etc etc.

---

### Post by Cheezespread on 2009-08-28
As far as I remember i never could read the contents of Documents and settings from Vista in Ubuntu. Though other folders worked fine. When you install Ubuntu for the first time , you get a prompt on the way to import the contents of your user from Windows. 


Bug info : [https://answers.launchpad.net/ubuntu/+question/10585](https://answers.launchpad.net/ubuntu/+question/10585)

---

### Post by oboedad55 on 2009-08-28
> **Cheezespread said:**
> As far as I remember i never could read the contents of Documents and settings from Vista in Ubuntu. Though other folders worked fine. When you install Ubuntu for the first time , you get a prompt on the way to import the contents of your user from Windows. 


Bug info : [https://answers.launchpad.net/ubuntu/+question/10585](https://answers.launchpad.net/ubuntu/+question/10585)

I just checked on this in XP. I can read the contents. The above directory is correct.

--Jon

---

### Post by freak42 on 2009-08-28
in vista you usually can find such folders under
c:\users\<your username>\....

---

### Post by Mark Phelps on 2009-08-28
> **oboedad55 said:**
> I just checked on this in XP. I can read the contents. The above directory is correct.

--Jon
Vista changed these locations.  In XP, they were actual folders; in Vista, they're called "junctions" (what we know as soft links).

Thus, in Vista, you can't open these folders; instead, you have to open the real folders.

---

### Post by LewRockwell on 2009-08-28
> **stoneface22 said:**
> Hi all --
     I've successfully (?) mounted my sda1 NTFS drive using the GUI that I installed via synaptics... 
     My problem now is that I can't find "My Documents" or "My Music" to import them to rhythmbox.  Where am I going wrong? Thanks,
 -- Keith

WHERE....does anyone see OP trouble-call reporting that they are using "Vista"?

and...given the above...why, Why, WHY, hasn't anyone asked that question?

anywho...

to OP, we have previously experienced the inability to access and manipulate data using Ubuntu. This includes running full "privileges"

so we just pop in another *nix distro(confession...usually Puppy) and wheeeeee, oh how nice!

and, as always...backup, Backup, BACKUP...everything you're not willing to lose permanently

.

---

### Post by stoneface22 on 2009-08-28
Actually, I was on vista before I switched to Ubuntu -- trying several things now; starting with backing things up.

---

