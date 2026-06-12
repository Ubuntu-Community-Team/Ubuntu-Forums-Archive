---
title: "Password for Samba sharing with Vista"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by zachthejones on 2008-04-20
I've checked a couple of threads, but I kind of got lost when things went completely terminal...

I want to share files from my Ubuntu (7.10) laptop (wireless) with my wife's Vista laptop (also wireless).  I have an Ubuntu desktop (7.10) and haven't had any problem using Samba to share with it.

In opening up the network, I can "see" my wife's laptop from mine, and I can see mine from hers, but I always get prompted for a username and password.

I found on a post to run this to change/set the samba password:
```
sudo smbpasswd -L -a COMPUTER_NAME
```

but after running that and entering a password, it said that it failed to change the password. But what is confusing me is that nowhere have I found how to set up a username...

Is the issue with Samba and needing a password/username to access and use with Vista? Or is it some sort of security thing separate on each laptop?

---

### Post by fsmithred on 2008-04-20
For someone to log into the shares on the linux box, they'd need to use the username and password of the owner of those files. If your wife has her own account on the linux box, she can log in to her share with her linux username and password, after you do:

sudo smbpasswd -a her_linux_user_name

and you'll be prompted for her password.

If you need to make an account for her, go into System --> Admin --> Users and Groups, or you could use the adduser command.


For someone to log into her windows machine, I guess they'd need to use an account that exists on that computer, but I don't know enough about windows to tell you any more than that.

---

### Post by jonandrews on 2008-04-20
Take a look at my guide to Ubuntu / Windows networking

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)


It was written around XP, but a number of forum members have told me it works fine with Vista.

---

