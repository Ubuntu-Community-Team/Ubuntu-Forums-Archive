---
title: "Understanding sudo/root"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by theprintingplace on 2011-04-02
Hello everyone. I thought I had the whole sudo/root account thing understood but now I am not so sure. I have no problems using sudo from a command line when I need to but I see to have a hard time elevating on the GUI side of things.

Example: I plugged in my external hard drive to do a backup using *fwbackups*. The drive was automatically mounted and displayed on my Desktop. I setup my backup set and wanted to use the external drive as the destination but I did not have permission to write to it since it was owned by root.

So, my temp fix was to open a terminal. I could not figure out where drives are when they are mounted automatically (ex: not in /mnt) so I unmounted on my desktop and remounted in a terminal to /mnt/backup. I then created a folder on my drive called "fullbackup" and used *chown* to change ownership to me, *nick*. I was then able to proceed with my backup.

There has to be an easier way! I couldn't even figure out how to login as *root* with XFCE. I know this is not supposed to be a good solution but how else do you solve this problem. I am all for converting users to Linux but we have to make it easy for them! LOL

Any help would be greatly appreciated. Thank you.

---

### Post by uRock on 2011-04-02
Hi! This may be helpful. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by fela on 2011-04-02
NEVER login to a GUI as root.
Never.

Never.

NEVER.

Did you hear me, I said NEVER.

OK, the 'proper' way to do it is like this:

plug in your drive
cd /media/your_disk
sudo chown user:user . -R

---

### Post by lisati on 2011-04-02
> **fela said:**
> NEVER login to a GUI as root.
Never.

Never.

NEVER.

Did you hear me, I said NEVER.

OK, the 'proper' way to do it is like this:

plug in your drive
cd /media/your_disk
sudo chown user:user . -R

Agreed. Although this is probably more intuitive for a system in a corporate setting where a department might want to limit access to their files by someone from a different department, a large part of the permissions system is based around the idea that different users have different responsibilities.

---

### Post by theprintingplace on 2011-04-02
OK. I won't login to the GUI as root. I won't ever do it! LOL I guess so many things in Ubuntu seem intuitive that I am surprised we ask users to open a terminal and chown, just to add files to a flash drive or USB hard drive.

I understand the security benefits and the concept of administrators setting up specific folders for users to read/write too but for the average desktop user, this is overkill.

No setting to have Ubuntu mount drives as a user instead of root automatically?

---

### Post by fela on 2011-04-02
> **theprintingplace said:**
> No setting to have Ubuntu mount drives as a user instead of root automatically?

It normally does do this, I'm pretty sure.

---

