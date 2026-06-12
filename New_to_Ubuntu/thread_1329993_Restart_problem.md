---
title: "Restart problem"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by proaditya on 2009-11-17
Hi

I am having problem shutting down my ubuntu system. I am dual booting Windows 7 and Ubuntu -9.10. THe problem is when i restart from ubuntu. It goes to black screen and hangs(does not poweroff). But if i give shutdown from ubuntu, it shuts down perfectly!!! What is to be done?
Aditya

---

### Post by Procuro on 2009-11-18
I had a similar problem a few Ubuntu versions ago and I fixed it permanently by updating the bios. Are you using the latest version available for your computer?

---

### Post by proaditya on 2009-11-18
How do i update bios? Also this problem was not happening with 9.04. Only with 9.10

---

### Post by Procuro on 2009-11-18
To update the bios, go to your manufacturers website (like HP or Dell) and find your computer under their customer support. You usually can install it within windows with semi-newer computers (otherwise you have to put in on a floppy disk). It never hurts to have the latest bios version.

But if it wasn't present in 9.04, that might not be the issue at all. Did you do an upgrade or a fresh install? Something could have gone wrong with the upgrade that contributed to it. If that's the case, there might not be an easy solution to the problem without doing a fresh install.

---

### Post by aaricia on 2009-11-18
Hello,

I have exactly the same problem that ProAditya mentions and it happended when I upgraded from 9.04 to 9.1. I have a dual booting with Windows Vista and Ubuntu. I cannot restart or shut down the laptop from Ubuntu. It shuts down the different applications, and then there is a line on screen saying "Deactivating swap" and gets frosen there. 

I decreased the value of swap in the configuration file, but there is no difference.

Is it a problem of the bios or of the upgrade?

Thank you very much for your help.

Regards

---

### Post by Procuro on 2009-11-19
Aarcia, the deactivating swap thing was a pretty large bug that has been affecting a large amount of users, especially those upgrading from a Wubi installation. A patch was released YESTURDAY it looks like, check it out:

[https://bugs.launchpad.net/wubi/+bug/468589](https://bugs.launchpad.net/wubi/+bug/468589)

Get the latest updates for your ubuntu installation, the patch for this issue should be out now or coming very very soon. Hopefully proaditya is experiences the same issue and this will fix it for both of you.

---

### Post by proaditya on 2009-11-22
hi all
thanks for the reply
i don't know what i did but now there is no restart problem. (no idea what happened). Guess i updated a few packages. But was some libmono something. Don't know if it is related to the problem

---

