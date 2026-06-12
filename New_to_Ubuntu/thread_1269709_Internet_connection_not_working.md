---
title: "Internet connection not working"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Y_Guy on 2009-09-18
Well I just installed ubuntu server edition, and am now trying to install webadmin.

However, I have no idea what is wrong, but ubuntu can't connect to the internet.

Ex: if i use wget (urlhere) I get:

```
Resolving....failed: Name or service not known.
wget: unable to resolve host address `(url)
```

Link is valid as well.

Sorry for my extreme lack of knowledge, and any help would be appreciated :)

---

### Post by Groucho Marxist on 2009-09-18
> **Y_Guy said:**
> Well I just installed ubuntu server edition, and am now trying to install webadmin.

However, I have no idea what is wrong, but ubuntu can't connect to the internet.

Ex: if i use wget (urlhere) I get:

```
Resolving....failed: Name or service not known.
wget: unable to resolve host address `(url)
```Link is valid as well.

Sorry for my extreme lack of knowledge, and any help would be appreciated :)

No worries; I'll just start by asking some basic questions.

What type of Internet connection are you using?
Are you using a WiFi router? If so, is it on? (I once made that mistake :D )

---

### Post by Y_Guy on 2009-09-18
I'm using a wired connection, and it works with all the other computers I've tested it on.

Pings return no response as well.

---

### Post by seshomaru samma on 2009-09-19
what about 
```
ifconfig 
```

---

### Post by ellgor on 2009-09-19
Hi,

Check to see if your ISP (internet service provider) supports the Linux system, I found this out to my cost and I'm using Virgin Media who use Windows for connections, luckily I have a small drive with  XP on it and was able to use that to connect to my modem, mind you after much hair pulling and lengthy conversations to Virgin, hope this helps.

PS   Once the connection has been made it does not require Windows anymore.
Regards, Ellgor.

---

### Post by Y_Guy on 2009-09-21
Sorry for not replying, fixed my problem (I think I didn't install something to do with DNS originally)

---

### Post by Iowan on 2009-09-21
What's in */etc/resolv.conf*? That's where DNS servers *should* be referenced...

---

