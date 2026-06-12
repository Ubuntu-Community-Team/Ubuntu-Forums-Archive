---
title: "&quot;Failed to add entry for user&quot; when switching users"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by linkmaster03 on 2009-03-16
Using su like so:

```
su - john
```

logs me in properly but shows an error like so:

```
tim@laptop:~$ su - john
Password:
Failed to add entry for user john.

john@laptop:~$
```

What does that mean, and how do I get rid of it?

---

### Post by lzap on 2009-03-17
Hello, same here. What to do???

---

### Post by darthpenguin on 2009-04-19
same here. I think it has something to do with samba in my case. help.

---

### Post by lzap on 2009-04-19
Do you have fresh install or did you upgraded from the previous release?

I have upgraded. I have U8.10...

---

### Post by vergenzt on 2009-04-19
I have the same problem, but it only started after I used "usermod" to change the name of my login, and it does it in the form of a dialog box when I login from Ubuntu's GUI.

---

### Post by andrew19881123 on 2009-04-22
i have the same problem in ubuntu 8.10 server after the usermod command.. how can i solve this problem? does it compromize some user functionality?
thx.

---

### Post by Captain_Glen on 2009-12-13
I had the same problem. But the solution is easy.

Just open up System -> Administration -> Users and Groups.

Then click unlock and enter your password.

Then Find the group that is your username and click on it. Mine was "glen".

Then click properties. Then make sure you put a tick in the box next to your username.

---

### Post by Captain_Glen on 2009-12-18
Ok my bad.  That didn't fix it.

But this really does (well it did for me anyway):

Open up Synaptic.

search for samba
select completely remove samba and system-config-samba
Hit apply

Log out
Log in.  It should say user added for your username.

Now install samba for the ubuntu software centre.

Your good to go.  

I should point out that I encountered this problem when I removed myself for the list of samba users (I was listed twice so I thought I'd "clean up" by removing one - bad idea!).  If you didn't encounter this problem by messing up samba this fix may not work for you.

---

