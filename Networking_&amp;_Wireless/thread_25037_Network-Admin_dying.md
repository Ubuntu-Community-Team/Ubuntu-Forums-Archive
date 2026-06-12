---
title: "Network-Admin dying"
date: 2005-04-09
forum: Networking &amp; Wireless
---

### Post by BrianRVT on 2005-04-09
Im am having problems in Hoary that I didn't encounter in Warty.  First off, the IPW2200 isn't working out of the box.  No problem I thought, Ill just fire up the network admin.  So I go through the menus and run it, but when I put in the root password, it tells me its the wrong one (yes im putting in the root's password).  I tried it again, and now it says "failed with child status -1" or something like that.  I was finally able to get into it, by su'ing to root, then running it manually with /usr/bin/network-admin.  It spits some error out on the console saying authenification failed, but starts up ok.  So I go in and configure the 2200 and try to activate it (the card is working fine because it sees my SSID).  Activating it takes several minutes and doesn't work properly.  

Any ideas??!?!?

Thanks in advance.

---

### Post by jdong on 2005-04-09
When prompted, you're supposed to enter your **own password**.

---

### Post by BrianRVT on 2005-04-09
Yea I tried that too.  When entering my password nothing happens.  I let it set for a minute or two and nothing still.

After messing around I think there is some problem with passwords.  I was trying to so a "sudo reboot" and I put in the root password, it rejected it.  But if I do "su root" then put in the password it works ok (and of course I can do "reboot" then).

I installed Hoary just like it suggested.  I made one normal user.  Any ideas?  Is this related or just another problem.

---

### Post by jdong on 2005-04-09
Can you try a "sudo network-admin" from the terminal, and see if you get a more detailed error?

---

### Post by BrianRVT on 2005-04-09
When I do "sudo network-admin" it prompts for password.  I put in the root password, and it says its the wrong one.  This happens 3 types and it exits.  This is a just a trial install and I just have the root password as "root".   So it isn't a hard one to type :)  Im udderly confused.  I setup Warty the same way and this didn't happen.

Thanks for your help!

---

### Post by jdong on 2005-04-09
When you use sudo, you must type in **your own password**. When you use su, you type in the root password.

---

### Post by BrianRVT on 2005-04-09
Using my password, it said my user account isn't in the sudoers file.  So I went in there and added it like root.  And it will start network admin now.  This is different than the way Warty ran correct?

So back to the original problem.  I configure and activate the wireless card, but commands like ping say that there is no network present.  Whats a good way to see if the network is active, similar to ipconfig in NT/XP?

---

