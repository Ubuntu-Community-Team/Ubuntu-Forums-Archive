---
title: "[SOLVED] Connecting to other computers on the network - WinXP and Vista"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by foolios on 2007-11-09
I have read a few posts that mention Samba(sp.).
Can someone point me to a tutorial that will help me share files between my xp/vista machines and this ubuntu machine, please?

Thanks so much in advance.

---

### Post by froy02 on 2007-11-09
Here's a thread that I used to setup my shares with vista, xp and other ubuntu machines:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) 

I might add that it worked perfectly.

---

### Post by vinnn on 2007-11-09
[System ] > [Administration] > [Shared Folders]
Simple as that.

---

### Post by foolios on 2007-11-09
> **vinnn said:**
> [System ] > [Administration] > [Shared Folders]
Simple as that.

I tried this first since it seemed the easiest. I can see the networked computers after doing this and rebooting.

I can access the Vista computer shares, no problem, surprisingly. =)
But when I try to access a file on this Ubuntu system from Vista, I have to log in. Since the login keeps giving me the vistauser/loginname kind of thing, it won't let me connect, I am guessing because that user needs to be on the Ubuntu system in some way.

How do I set up access to the Ubuntu shares? Do I need to add a user and log in as that user, or do I set up some kind of permission on the shared folder itself.

I'll look at the other link about setting up Samba and see if that would be the better alternative.

Thanks

---

### Post by bigken on 2007-11-09
in a terminal type 

sudo smbpasswd -e yourname
sudo smbpasswd -a yourname

---

### Post by foolios on 2007-11-09
> **bigken said:**
> in a terminal type 

sudo smbpasswd -e yourname
sudo smbpasswd -a yourname

I tried the first line with a user of foo and it now allows me access to the Ubuntu shared folder via the Vista pc.
I tried to copy a file to the Ubuntu share but it says I need permission to do so.
I then tried the second line with foo as the username and it seems to allow it.

But I still can't copy a file to the Ubuntu share from the Vista pc.

Thanks so much for your help in advance.

---

### Post by bigken on 2007-11-09
i think you need to allow read write permissions in ubuntu shared folders

---

### Post by foolios on 2007-12-16
YOu were exactly right. That solved it.
Thanks so much.

---

