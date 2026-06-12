---
title: "Broadcom wireless no driver in repo 15.10 no network detect problem"
date: 2015-11-10
forum: Networking &amp; Wireless
---

### Post by andrew211 on 2015-11-10
Previously, I installed the bcmwl package to get my Dell Latitude 2100 to use wifi. 

I clean installed 15.10 on account of update issues relating to cloning an install to the SSD that is the drive for this netbook (grub or bios and ID of the drive not identifiable or clearly indicated?).  

I tried the find additional drivers option and there was no apparent need for any despite having a Broadcom wireless card, which is fairly infamous for being difficult to work with in Linux compared to others.  I also checked Synaptic and apt-cache search for bcmwl to no avail. 

Technically, I'm installing 15.10 Lubuntu.  To my knowledge, the differences between this and Ubuntu 15.10 are or would be negligible.  

I tried the keyboard shortcut for making sure wifi was not shut off via hardware switch.  However, doing this did not cause the light to indicate it being on regardless of how many times I used it.  Of course, 

I used ethernet to do all this. 

 I tried sudo rfkill unblock wifi and I believe sudo rfkill unblock all and rebooted and that also did not solve the problem.  To top it off, the same error message that states there is a problem (unspecified by error message) and asks if I would like to report it still appears when I first boot up (just like it did when I was using a cloned OS install which was an update manager -d type upgrade to the most recent version on the old drive). 

 I did try to grab bcmwl from Launchpad using debi package install, but it could not resolve dependency issues.  Also, I looked for bfwcutter, thinking that perhaps it had been updated and better so as to do away with the need for bcmwl (I had problems getting this to work as effectively in the past).  

I need wifi for work, not only for personal use at home, but also business use away from home, but I do not know how to resolve this issue.

Thank you in advance for any help you can offer!

AB

---

### Post by ajgreeny on 2015-11-10
To help us to help you please use paragraphs in your post.

Many forum users are, unfortunately, you may think, very good at dismissing a "wall of text" like yours, and don't bother trying to help because it is much harder to read and see your problem.

---

