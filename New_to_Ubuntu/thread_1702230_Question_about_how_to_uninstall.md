---
title: "Question about how to uninstall***"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Amber2011 on 2011-03-07
Hi,

I need to uninstall Ubuntu 10.10 from Xp. I have tried all weekend to log on Ubuntu and I can't. I have read on other forums many other people are having the same problem. I am done trying, at least if I get rid of it, I can reinstall. I really was enjoying Ubuntu but it is useless to me, if I can't get on.

Anyway I read different ways of doing it, from this forum and Google. I am hearing to download this and that and unzip and put in C drive and type in command prompt. I am looking for the easiest way. I do not want to chance losing XP. Would it work if I just done a regular reformat with my XP recovery CD's? At least I know how to do that. I am new to this so I need baby talk....please! Thank you

---

### Post by Rex Bouwense on 2011-03-07
We need a little more information.  First, did you install Ubuntu inside of Windows using WUBI or did you install it along side of it?

---

### Post by Amber2011 on 2011-03-07
Oh yea, I forgot that information. I used a10.04 live CD upgraded to 10.10. I have a duel boot side by side.

---

### Post by Rex Bouwense on 2011-03-07
Can you boot into Windows with the current set-up?  
The Windows master boot has been replaced by GRUB, so if you remove Ubuntu you will have to replace that and there are many how tos on this forum for that operation.
It sounds like you got a bad upgrade.  Do you by chance have a Ubuntu 10.10 CD?  You could do a fresh install.  Upgrades are sometimes chancy and it sounds like yours went south.

---

### Post by Amber2011 on 2011-03-07
> **Rex Bouwense said:**
> Can you boot into Windows with the current set-up?  
The Windows master boot has been replaced by GRUB, so if you remove Ubuntu you will have to replace that and there are many how tos on this forum for that operation.
It sounds like you got a bad upgrade.  Do you by chance have a Ubuntu 10.10 CD?  You could do a fresh install.  Upgrades are sometimes chancy and it sounds like yours went south.


Yes I can boot to windows, I am on there now. I did reading on this prior to posting and understand how to uninstall, for the most part, but am a bit confused with other parts.

Since the master boot has been replaced by Grub...does that mean that the XP recovery CD's will not work? If that is true then I guess I just need to go over the "how to's" a little more. I was looking for an easy way out, one that I was familiar with.

I upgraded from the Ubuntu software.

---

### Post by Rex Bouwense on 2011-03-07
The XP Recovery Disk will work and will probably re-install the Master Boot whatchamacallit that Windows uses.  You will lose Ubuntu if you use the Disk so back up anything that you cannot stand to do without (like your grandmother's recipe for sugar cookies).

---

### Post by Amber2011 on 2011-03-07
I have only had Ubunu about a week or so. I wanted to make sure everything worked before I put my music and everything on it....so I have nothing to back up.

So just to be clear....just do a normal XP recover and I am good to go? Thank you very much, I appreciate your help.

---

### Post by Amber2011 on 2011-03-07
I am not against Ubuntu and I would like to try again. Just wanted to let you know.

---

### Post by Rex Bouwense on 2011-03-07
Linux is not for everyone and there are probably in excess of 350 varieties out there to try.  Ubuntu is a very popular one and has excellent community support.  I grew up with Windows and then found Ubuntu.  Sorry it didn't work out for you.  Perhaps some other time in the future.

---

### Post by Amber2011 on 2011-03-07
Most likely not far in the future. I am tired of windows, constant worries and slow downs....well you know the deal with them.

I just wonder why the instructions to uninstall does not list a XP recovery choice? Don't get me wrong this forum is great.

---

### Post by bcbc on 2011-03-07
You just need to run "fixmbr" from the XP recovery command prompt. Then, make sure it boots direct to XP when you restart the computer. 
Then, remove/reformat the partitions you created for Ubuntu. (Do not do this before you are booting straight to XP or you'll get stuck at a grub rescue prompt).

I don't believe you can 'merge' the partitions back with XP, but you could probably do it using Gparted on a live CD. If it was me, I'd just keep them separate.

---

### Post by Amber2011 on 2011-03-07
Ok that is very helpful. Keeping the partitions separate is fine with me.This computer is getting old and I will be getting a new one soon and use this one just for my experiments. One of them will be Ubuntu so I will talk to you all later. Thanks you have been great. Take care see you down the road.

---

### Post by Rex Bouwense on 2011-03-07
Amber2011 sorry I didn't get back to you, my battery was running out of juice and I didn't have my AC charger so I had to back off but it looks like you got what you needed.  Enjoy.

---

