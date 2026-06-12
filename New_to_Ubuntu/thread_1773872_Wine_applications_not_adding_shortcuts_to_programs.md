---
title: "Wine applications not adding shortcuts to programs under the applications-&gt;wine-&gt;x"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by venom104 on 2011-06-02
Whenever I install a wine program it doesn't automatically add itself under the applications->wine->programname folder anymore. The problem started when I had a current version of wine, then went back and installed a version of wine that was older (I think it was 1.3.7). I got an error, it was something like plugplay.exe was not installed, so I did a rm -rf ! ~/wine. I ended up reinstalling the current version of wine, but now whenever I do the shortcuts don't appear in the context menu!

I have to reinstall all my programs and I would like them to AUTOMATICALLY make shortcuts to themselves. 

Someone please helo?

---

### Post by venom104 on 2011-06-02
I created a new user account and the problem doesn't happen on the new user account, so it's a fix...I guess. However, this problem IS NOT SOLVED, so I won't mark it as solved yet. 

I'm guessing there is some type of script that must have gotten deleted that runs whenever a WINE program is installed. I'm still clueless as to how to fix it, googling did not help at all.

---

### Post by iansane on 2011-06-02
Just to be sure, when you did the rm -rf was it with a . in front of wine? It's not in your post so need to make sure.

I just tested with a .test directory and did rm -rf ~/test and it gives no indication that the file test does not even exist and it did not delte .test

The wine directory in your home directory is hidden with a . in front of it.

So, just making sure you actually deleted it as this would be an easy mistake.

also be careful with that command. It removes recursively and forces the removal even if it's a system file.

Used to be a dirty prank to tell a computer buddy new to linux to run
sudo rm -rf / or something like that and linux would start deleting itself from the system root until it crashed.

---

### Post by venom104 on 2011-06-02
> **iansane said:**
> Just to be sure, when you did the rm -rf was it with a . in front of wine? It's not in your post so need to make sure.

I just tested with a .test directory and did rm -rf ~/test and it gives no indication that the file test does not even exist and it did not delte .test

The wine directory in your home directory is hidden with a . in front of it.

So, just making sure you actually deleted it as this would be an easy mistake.

also be careful with that command. It removes recursively and forces the removal even if it's a system file.

Used to be a dirty prank to tell a computer buddy new to linux to run
sudo rm -rf / or something like that and linux would start deleting itself from the system root until it crashed.


I meant to type rm -rf ~/.wine Any thoughts on my problem?

---

### Post by iansane on 2011-06-03
No, sorry, I was hoping it was that simple.

I know some apps don't put the shortcuts in because they aren't completely compatible with wine since they were really made for windows but it shouldn't be a case of no apps making shortcuts at all.

I know you already removed it but to give it one more try, you could go to synaptic, do a completely remove, then check the "not installed(residual files) category for anything wine just in case and remove that completely, then go and rm -rf your .wine directory again, and then do a search on the whole system for wine and manually delete anything wine, then try installing it again.

This might cause issues for the working wine in the new user profile if there are any system files not located there so to be safe I would rm-rf that one too and just start completely from scratch.

---

