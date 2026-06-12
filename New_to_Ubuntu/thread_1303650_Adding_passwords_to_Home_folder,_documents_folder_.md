---
title: "Adding passwords to Home folder, documents folder ect."
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-10-28
My laptop is being sent away to samsung tommorow and i want to put passwords on my folders so the cant look about my personal files. help?

Also do you think that the they would need to access drivers and such?

---

### Post by ikt on 2009-10-28
Would it be better to create a 'dummy' user that has no password and logs on automatically that way they have no access to your folders, then just remove that user when you get your laptop back?

Would need to make sure your home folder has permissions set so 'others' can't access it.

Although I think it's a little paranoid, I imagine if they're booting into your operating system as apart of their checks, they haven't got very good tools.

---

### Post by WestCity on 2009-10-28
I don't know how many files you have, but maybe you can just burn a dvd or two and erase files from laptop. ;)

---

### Post by mr_steve on 2009-10-28
Unless you encrypt your files, nothing you do will keep them from accessing your files if they want to. They shouldn't need to, since presumably you're sending it in for some kind of hardware problem.

I usually go one of two routes if I have to send a laptop in for service:
1) Backup the drive, and wipe it with the factory restore tool. This is especially helpful for companies that refuse to support computers with Linux installed, even if the problem is obviously hardware.

2) Talk to them ahead of time and tell them you'd prefer to send the machine in without the hard drive. Not everyone will allow this, even if you're sending it in for something like a broken screen hinge or similar. But in one of my last jobs, it was pretty common for us to send computers to Dell's service center with the hard drive removed.

---

### Post by Rave Gloves on 2009-10-28
Cheers for the replys guys, i like the idea of a dummy account, i will leave a not on the laptop saying for them to log onto it. 

Any back up software you recomend?

---

### Post by Rave Gloves on 2009-10-28
bummpp

---

### Post by theozzlives on 2009-10-28
+1 for taking out the HD out. That's what I did when I sent my laptop in. If you don't, you may wind up with Windows and NO data.

---

### Post by mikewhatever on 2009-10-28
Protecting folders with passwords would not stop anyone with physical access to the computer from looking into these folders. It's a very simple 'protection' that used to be available for Windows XP, it's none existent in Ubuntu simply because it doesn't protect anything. The options you have, if taking out the hdd isn't an option, are, encrypt, or backup and safe delete.

---

### Post by Rave Gloves on 2009-10-28
> **mikewhatever said:**
> Protecting folders with passwords would not stop anyone with physical access to the computer from looking into these folders. It's a very simple 'protection' that used to be available for Windows XP, it's none existent in Ubuntu simply because it doesn't protect anything. The options you have, if taking out the hdd isn't an option, are, encrypt, or backup and safe delete.

Are there any back up software??

---

### Post by theozzlives on 2009-10-28
> **Rave Gloves said:**
> Are there any back up software??

Just take out the HD and include a note saying you have sensitive data on there. They can't make you compromise yourself by giving them your data.

---

### Post by mikewhatever on 2009-10-28
> **Rave Gloves said:**
> Are there any back up software??

Here you go. [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

You may also want to look at imaging, which is a way of backing up all of your system. I don't know why you are sending the laptop to Samsung, but if it had Windows preinstalled, the vendor might find it necessary to reinstall it and wipe all your data in the process.
[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)

---

