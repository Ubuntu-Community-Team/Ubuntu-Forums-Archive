---
title: "[SOLVED] Messed up permissions"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Lage on 2009-01-04
Hi!

I'm new to Ubuntu, have tried it out a little before but never given it a real try until the past week (I finally removed XP entirely from my machine, so now I just have to learn, great!).

Anyway. Yesterday I added an account for my girlfriend in the "Users and groups" interface and had a look at the options available there. While doing this, I must have somehow disgranted myself some permissions, because now there is no "add/remove programs" symbol in the programs menu, and my password won't work when trying to do sudo things. Before, I used to have the same password for sudo as for logging in (that seems to be the way Ubuntu sets it up from the beginning), and it's the only password I've ever had on this system, but now apparently it won't work for sudo things. Obviously I can't change any users' permissions either, so I feel like I'm in a catch 22 here. I've tried logging into my girlfriend's brand new account too, but I don't seem to have set any administration privileges to her either.

Is there any way to get out of this situation? I don't remember unchecking any boxes, but I suppose I must have... and I feel so stupid. Please help.

---

### Post by bodhi.zazen on 2009-01-04
Your user needs to be in the admin group to access sudo / gksu

Boot to the recovery mode and enter this command :

adduser <username> admin

were <username> = your log in name (without the < > brackets)

---

### Post by Lage on 2009-01-04
Well, thank you very much! That did the trick!

What puzzles me, though, is that if it's that easy, what's the point in even having passwords and an admin group? Going into recovery mode as root didn't require any kind of authentication!

---

