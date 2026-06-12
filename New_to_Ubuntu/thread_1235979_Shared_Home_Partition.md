---
title: "Shared Home Partition"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by AlistairH on 2009-08-09
I'm currently running Ubuntu 7.10 with a separate home partition. If I was to install Ubuntu 9.10 in a dual boot arrangement, can 9.10 use the same home partition, or would there be conflicts or file permission issues?

---

### Post by cwsnyder on 2009-08-09
The main conflicts would be the settings for applications (which are stored in /home) might be for two different releases of the applications.

A separate /home partition saves application settings when you do a distribution upgrade, but that same saving of application settings will set up conflict when you attempt to share the /home between two different distributions/releases.

---

### Post by AlistairH on 2009-08-10
Thanks cwsnyder, I'll keep them separate then.

---

### Post by louieb on 2009-08-10
Heres a tip. If you use the same user names and add them in the same order. Then the user will be able to access data  in there home on the other install. You could add a symbolic link

User name is obvious. Why the same order? Each user also has a number  1st user is 1000,  2nd - 1001 and so on. Some programs use name other number when checking permissions.  User number (id) can also be found on the advanced tab in Users and Groups.

---

### Post by AlistairH on 2009-08-12
Good point louieb, thanks.

---

### Post by Paqman on 2009-08-12
There's no reason why multiple distros can't share one home partition, just make sure you have separate user accounts for each distro. I've had my machine set up this way for years. Multiple separate home partitions would waste a lot of space.

---

### Post by AlistairH on 2009-09-24
I installed an extra hard disk and used that for Ubuntu 9.04 for testing purposes with louieb's suggestion regarding usernames and order of creation to allow me access to the Ubuntu 7.10 home directories.

Now that I've test the specialist software I needed runs properly under 9.04, I'd like to wipe the 7.10 installation, install a new copy of 9.04 on that partition with it picking up the original home partition in the process.

Assuming I point the home directory to the original home partition during installation, and do not format it of course, I assume the 9.04 installation will pick everything up ok. Will there be any issues regarding software versions settings, i.e. OpenOffice 2.0 v OpenOffice 3.0?

Would it be better simply to restore my data from backup into a fresh 9.04 version of the home directories?

---

### Post by Marflus on 2009-09-24
I can't say whether there'd be issues or not for sure, but it seems likely there would be some odd behaviour or something. Fixable, for sure, but probably a little extra work. In your position I'd opt for a total reinstall, to avoid any possible problems, though I can see the advantages of not going that way.

---

### Post by scorp123 on 2009-09-24
> **Paqman said:**
> There's no reason why multiple distros can't share one home partition, just make sure you have separate user accounts for each distro. +1 on that one.

Same /home partition ... but different users. So the settings of e.g. OpenSUSE don't mess with my setting for Ubuntu, and so on. Actual files (movies, music, text documents, and what not) is stored on a separate partition /data anyway. I simply place symbolic links from the /data place into the relevant /home/someuser directory and voila, I can access the same files from all the distros without wasting more extra space than really needed.

---

