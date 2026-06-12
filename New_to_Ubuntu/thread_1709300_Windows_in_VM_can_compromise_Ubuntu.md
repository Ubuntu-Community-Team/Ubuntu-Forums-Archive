---
title: "Windows in VM can compromise Ubuntu?"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by dojopo on 2011-03-18
Hi, I recently installed ubuntu but there is some software with which I have to work(accounting) and was develop only for windows and will not run with wine. So I installed virtual box and got windows 7 enterprise running. My question is, is it possible to get ubuntu infected while running windows 7 in virtual box? Even though I don't have wine installed now on Ubuntu. Also, if let's say I do a dualboot, windows 7 and ubuntu, if I get my windows infected, what will happen to my ubuntu?


Cheers!

---

### Post by Darkness Des on 2011-03-18
Some Viri (that you can't even find if you're looking for) can notice that they are in a virtual machine, but as soon as they climb out get extremely confused by Linux. And unless you run VirtualBox as root (which if you're going through the menu, you're not) it can't do anything even if it can work with Linux, which I guarantee it can't. With Wine, Viri (when they work) can only affect a fake C: drive, meaning it gets the Wine Notepad installation and that's about it.

Summary:
You are perfectly safe and there is no need to worry whatsoever.

---

### Post by darolu on 2011-03-18
Nothing would happen in both cases. Virtual Box is a virtual machine, it creates a virtual hard drive where everything is stored, including Windows itself, all of its programs and documents. It's completely safe. In a dual-booting installation, something similar happens, except that it is no longer a virtual environment but an actual separated hard drive or hard drive partition. Although in both cases you can access Windows files from Ubuntu and vice versa, Windows malware are useless in a Linux environment, in Richard Stallman's words it would be like trying to rob a bank by pointing at the cashier with your finger tip.

---

### Post by dojopo on 2011-03-18
Thank for being so fast and helpful. I have just one more question which I forgot to put it in my post. I'm also concerned about my router. It's a linksys and runs a custom firmware(dd wrt). Is it possible in some way that the router can be affected?(the firmware to be more exactly).


Cheers, dojopo!

---

