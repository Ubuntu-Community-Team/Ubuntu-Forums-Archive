---
title: "My Computer Just Died"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by MFisher81 on 2011-05-31
Hello, 
I have been using Ubuntu 10.10 for a few weeks now on an Acer Aspire 5520. I have been enjoying it so far, but today (just when a major project is coming due) I get the following error at startup:

[        15.817327]  ath5k phy0: can't register ieee80211 hw

So I can't start up the computer or access any of my documents. Also, I am an absolute beginner here.

Two things happened before I got this error: 

1. I installed a recommended security update (sorry, I don't remember exactly which one).
2. I was having trouble getting a usb flash drive to mount...

---

### Post by BlouBlou on 2011-05-31
Is X (graphics) working fine?
Can you login as your user and use PC as usually or it only starts as recovery-mode?

If you can't start x, try "startx".
If it's a HDD error, use "fsck".

Tell me if you need further help.

---

### Post by shad0w_walker on 2011-05-31
Ok, the 802.11 and the ath5k bits are pointing to this being something either to do with the wifi card or whatever is loading straight after the wifi card.

When you turn on the computer, you should get a menu popup with a few options on what to boot (Generally will have a list of kernels and what not, along with recovery mode)

If you can, try to boot from one of those recovery options. See if that makes any difference. If you have a switch to turn your wireless on/off, try turning it off and seeing if that helps.

---

### Post by MFisher81 on 2011-05-31
I tried to start up in recovery mode, but I got the same error. It doesn't allow me to input anything. I am trying to start up with a live cd right now.

---

### Post by jtarin on 2011-05-31
If you can boot with the Live CD use it to CHROOT into your installed enviroment then remove the module ath5k to keep it from loading at boot.This should allow you to then boot into an environment you can work in but with no wireless at present until the driver problem is sorted out.

---

### Post by MFisher81 on 2011-05-31
I backed up my files and reinstalled the OS. Everything is working fine now. Running updates to see if the problem happens again.

---

### Post by dFlyer on 2011-05-31
> **MFisher81 said:**
> I backed up my files and reinstalled the OS. Everything is working fine now. Running updates to see if the problem happens again.

That was one way of fixing the problem, but nothing was learned.

---

