---
title: "Lack Privilege?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by GaryPG2 on 2009-03-15
I am just getting started with Ububtu. A few days ago I ran ntfs-config to gain access to my Windows Vista partition. It worked perfectly. Today I tried it again, but double clicking the Hard Drive icon in the file browser gave me the message:

"You are not privileged to mount the volume 'Hard Drive'."

I tried logging in again as root using the only password I have, but it would not accept it. I am the only user on my system.

Can somebody tell me what I am doing wrong?

---

### Post by taurus on 2009-03-15
Did you shut down your vista cleanly the last time you used it?  Boot back into vista and shut it down cleanly and it should mount automatically when you boot back into Ubuntu since you have an entry to mount it in /etc/fstab.

p.s.  Even if you are the only user on your machine, you are not root.  You are just a user who happens to have root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dhysk on 2009-03-15
normaly you would have to be root to mount a drive.  In Ubuntu when you log into as an 'administrator' you arn't actually running as root.  mount something alot of times you have to use a comand like 

sudo mnt /dev/'yourdrivesname' /media/'yourdrivesname'

---

### Post by GaryPG2 on 2009-03-15
Thanks. You are correct. I did not shut down Vista correctly. It was taking forever to shut down so I pressed reset. After going back and shutting down properly, all is well.

---

