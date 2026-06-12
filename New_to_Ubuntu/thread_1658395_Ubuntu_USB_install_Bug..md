---
title: "Ubuntu USB install Bug."
date: 2011-01-02
forum: New to Ubuntu
---

### Post by Rave Gloves on 2011-01-02
Im trying to fresh install ubuntu 10.10 after i screwed some things up. Im running the installer through my usb pen which i made on a windows machine with pendrivelinux. The installer runs till it gets just about the end then i get something like this.

"We're sorry; the installer crashed.  Please file a new bug report at
[https://blah](https://blah) (do not attach your details to any existing bug) and a
developer will attend to the problem as soon as possible.  To help the
developers understand what went wrong, include the following detail in
your bug report, and attach files /var/log/syslog and /var/log/partman:"


I checked google and people have been reporting this but ive found no fix for it. Anyone else had this ?

---

### Post by Rave Gloves on 2011-01-02
I fixed it. This is what i did.

During install when you get to the screen where it gives you the option to duel boot fully install or advanced. 

Go to Advanced then get your home folder and click on changed.

Click it to be formated, your mount point as / and set it to EXT4. 

Then click install now. This fixed it no problem for me.

---

### Post by Jugglemisterer on 2011-03-11
Rave Gloves, can you be a little more specific because i am having the same problem and when i went to advanced i didnt see a home folder. I saw three folders total, two folders that could be formatted and im a complete novice (if you couldnt tell). Im trying to install ubuntu 10.10 on a computer with no current os because windows crashed.

---

### Post by wilee-nilee on 2011-03-11
> **Jugglemisterer said:**
> Rave Gloves, can you be a little more specific because i am having the same problem and when i went to advanced i didnt see a home folder. I saw three folders total, two folders that could be formatted and im a complete novice (if you couldnt tell). Im trying to install ubuntu 10.10 on a computer with no current os because windows crashed.

Post your problem in a new thread as it may seem that the problem is the same but it is not, and look at the last date posted.

---

