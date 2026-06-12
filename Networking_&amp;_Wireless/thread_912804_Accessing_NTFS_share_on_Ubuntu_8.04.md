---
title: "Accessing NTFS share on Ubuntu 8.04"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by lsaplai on 2008-09-07
Hello all,

I have a small home network with 1 machine running Windows XP and the other Ubuntu 8.04 (a laptop and a desktop).

The Desktop Ubuntu is actually dual boot with XP and the XP partition is NTFS. I always run this machine with Ubuntu. I haven't booted XP for months.

I have no problem accessing the XP shared partition from the XP machine. However, I can't access it from the laptop (Ubuntu 8.04). I can see it under Places | Network and when I click on it I'm prompted for a username and password but whatever I enter, I can't open the share. (If I user my desktop username and password, it keeps asking again and again, as if the password was wrong; If I use the Windows admin username and password, I get a "Failed to mount windows share" error)

Question: given that the NTFS share runs on an Ubuntu 8.04 machine, how do I access it from another Ubuntu 8.04 machine?

Thanks in advance for your help!

---

### Post by superprash2003 on 2008-09-07
an easy way out is to setup samba and share the partition, you should see it under /media/(ntfs partition name).it would be in the form of a folder, just share it [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by lsaplai on 2008-09-12
Thanks a lot Prash.

I've been kept away from that laptop for a few days so I wasn't able to follow up earlier.

I have to take a more detailled look at your tutorial and my desktop machine, but the NTFS partition shoud be shared already: I can see it on the laptop, just can't open it. I can aslo access it (browse content, read and write files) from a Win XP desktop on my network.

I would expect, as I'm using the same username and password on all the computers, to be able to access it without problem.

I'll keep investigating. Advises are still welcome!

---

