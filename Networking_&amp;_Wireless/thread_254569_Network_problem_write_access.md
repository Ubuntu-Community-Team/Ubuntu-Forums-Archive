---
title: "Network problem: write access"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by Amorphous_Snake on 2006-09-10
I have a network between 2 PCs. One running Ubuntu 6.06 and the other running Windows XP. I made my whole "home" folder to be shared using SMB. I can see it from my other PC while on Windows but I can't access it, because I am asked for a password and username (I enter my Ubuntu password and username but nothing happens. I am the admin of both PCs, by the way). When using Knoppix on the Windows PC, I can see and access the shared home folder (without being asked for a password or anything) but without being able to write in it, although I have the "Read only" option unmarked in Shared Folders Settings in Ubuntu.

I think I might have problems on my Windows PC so I am trying to format and reinstall Windows, but I need to copy the important data to the Ubuntu PC.

Please help, I need a very quick answer...

---

### Post by 0be1 on 2006-09-10
Amorphous_Snake;

Have you by chance created an non-root user account on your ubuntu box as well as give that account permissions to you home folder? Just a thought.

Ubuntu is very good on security, sometimes too good in fact, but I feel better safe than sorry.

Please post back any finds you may have so others can learn from it as well.

regards...

0be1

---

### Post by Amorphous_Snake on 2006-09-10
> **0be1 said:**
> 
Have you by chance created an non-root user account on your ubuntu box as well as give that account permissions to you home folder? Just a thought.


The user account I am using is the one that the installation process asks when you are installing Ubuntu. It's not root, but I think it's the highest possible level?

---

### Post by 0be1 on 2006-09-10
Amorphous_Snake;

That was somewhat my point. Ubuntu does not have an account built in by default for you to interact with windows systems. That is why I asked if you has created one or more accounts with the proper access rights to view, read, and write to your shared folder.

So again, my question is have you created additional accounts with the appropriate rights?

regards...

0be1

---

### Post by Amorphous_Snake on 2006-09-11
I guess not. How do you do it anyway?

---

### Post by 0be1 on 2006-09-11
If you have a windows manager of sort sort installed it may very. Under Gnome, go under system - administration - users and groups and add your user. If you don't have a manager you can do adduser --help for your choices or man adduser for the really meaty stuff. Don't forget to set you permissions as well, and if you want two way access (windows and Linux) setup a user on your windows box with the exact same spelling of the username and password.

Hope this helps...

0be1

---

### Post by Amorphous_Snake on 2006-09-11
I have GNOME. I tried making another user and I added it to the group "$User". I hope that's right.

I am a complete Linux newbie and I hardly understand how this thing works. I once tried to make a user and then I deleted it, but I couldn't even delete the home directory of that user from my user because "I don't have permission". What is this?!!! I created that user. Can't I delete its home folder. I had to delete it using "gksudo nautilus" when I press Alt-F2 (A trick that I learnt here!). So, I know that this isn't the place to ask such question, can you beside helping me with the network problem, remove the confusion I am having with access, read and write rights in Ubuntu?

---

