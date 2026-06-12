---
title: "How to access Root folder from live disc?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by DanielAnnis on 2011-04-30
I'm new here, hello everyone- 
I've had Ubuntu on my laptop (HP G60) for two  years now. A month ago I updated Maverick and now my laptop will no  longer boot. I've scoured around for ways to achieve this, but I've  swallowed just doing a fresh install, but first I need to get some files  from my root menu.
 When I run the Ubuntu live disc I do not have access to my root  folder. It appears the HDD is mounted, but I just don't have the  permissions, as I'm not signed in as the admin. I need to transfer some  business files to a flash drive before I can wipe everything else. I'm  not seasoned with the Terminal and I just want to get on my way, you  know?
 So I guess I'm looking for either how to sign in as an administrator,  or how to change the permissions of the root folder or just how to  access the files altogether. It's not a matter of how I get to the  files, it's that I get to them at all.
 Help a brother out! Thanks in advance!

---

### Post by wojox on 2011-04-30
You need to use sudo and the terminal. FYI don't store stuff in your root directory. Encrypt your home folder from now on. :P

---

### Post by gregorthebigmac on 2011-05-05
A little more information on how to do this, please? I've been using ubuntu for a while, but I'm far from a power user, and while I understand what you mean by sudo and terminal, I don't know what to do after getting su.

I'm in a similar situation as OP, I upgraded to 11.04 from 10.10, and it didn't go so well, so I booted from 10.04 live CD, and am trying to backup my files, so I can just wipe and start over, but I can't access my entire music folder, due to permissions.

**Edit: I don't really understand why I can access all of my other files, but not my music files. For some reason, those are blocked due to permissions, but all of my documents folders, videos, downloads, etc, were all opened, no problem.

---

### Post by gregorthebigmac on 2011-05-05
Sorry to reply to myself, but I finally got a hold of a buddy of mine who is a linux guru, and he finally set me straight, so I'm posting what I needed to do for anyone else who might come here with the same problem.

The problem is I was trying to run chmod from the wrong directory. Say, for instance, the directory I'm trying to access is /home/music. I have read/write access to /home, but I don't even have read access to /music. to solve this, go to the parent directory /home, (or however high in the tree you have to climb until you get to a directory which you have read/write access to), then run the following from there:

```
sudo chmod 777 -R <yourdirectory>
```

this should reset the owner of the directory in question to whatever you're logged in as. Hope this helps.

---

### Post by Dondermans on 2011-05-05
For your home-directory, this gives *everyone *read and write access and allows *everyone* to execute the files. If I understand your message correctly using 006 would suffice:```
sudo chmod 006 -R <dir>
```. This only gives read and write access. For more information I kindly like to suggest you read the man page of chmod, located here:

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

If you would like access to files in your root directory, it is safer to use:

```
alt F2
```and enter:

```
gksu nautilus
```This gives you temporary access as root.

---

### Post by Wim Sturkenboom on 2011-05-05
> **gregorthebigmac said:**
> 

```
sudo chmod 777 -R <yourdirectory>
```

this should reset the owner of the directory in question to whatever you're logged in as. Hope this helps.

No, it does not ;)
It sets the permissions on files and directories so everybody can access them.

---

### Post by gregorthebigmac on 2011-05-05
Ah, my mistake. Thanks for the correction, guys :)

**Edit: Either way, given the situation I was posting about,

> **gregorthebigmac said:**
> 

I'm in a similar situation as OP, I upgraded to 11.04 from 10.10, and it didn't go so well, so I booted from 10.04 live CD, and am trying to backup my files, so I can just wipe and start over, but I can't access my entire music folder, due to permissions.



Either way would be acceptable for my situation, but they are absolutely right about the permissions being wrong. Unless you're just doing a quick backup and wipe, my method is probably not the best way to go :)

---

### Post by gregorthebigmac on 2011-05-05
> **Dondermans said:**
> For your home-directory, this gives *everyone *read and write access and allows *everyone* to execute the files. If I understand your message correctly using 006 would suffice:```
sudo chmod 006 -R <dir>
```. This only gives read and write access. For more information I kindly like to suggest you read the man page of chmod, located here:

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

Wow. This man page was more detailed than the one I read in my terminal. It gave me no number examples to modify the command with. I just got the 777 from my friend, and it worked. He didn't explain thoroughly what it did, only that it reset the owner. Thanks for the correction :)

---

