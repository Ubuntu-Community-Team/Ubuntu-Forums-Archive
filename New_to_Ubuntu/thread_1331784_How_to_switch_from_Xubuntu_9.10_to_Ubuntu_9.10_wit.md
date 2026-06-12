---
title: "How to switch from Xubuntu 9.10 to Ubuntu 9.10 with all data intact."
date: 2009-11-19
forum: New to Ubuntu
---

### Post by velvund5 on 2009-11-19
I remember doing this with Jaunty.  It was successful.

I have Xubuntu 9.10 on my computer. (Dell mini 10 - yeah, that horrible one)  Anyway, I am wondering what would be the code to disolve Xubuntu 9.10 along with its applications and Xfce and replace it with Ubuntu 9.10 and Gnome?  I've looked at a few previous codes; however, it never completed the job.  Any ideas?

---

### Post by scorp123 on 2009-11-19
```
sudo apt-get install ubuntu-desktop
```

No idea what "codes" you are talking about. If you have error messages: **Post them!** So we can see them. Just talking about them without telling us what ***exactly*** went wrong makes it impossible for us to help you.

---

### Post by mlentink on 2009-11-19
scorp123 speaks truth

As an addition, there isn't really a reason to remove the xfce components and libraries after you've installed the gnome-desktop, unless you're extremely squeezed for disk-space

---

### Post by aysiu on 2009-11-19
You're probably talking about this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

It's been updated for 9.10.

---

### Post by velvund5 on 2009-11-19
Sorry, I meant command line.  I'm bad with the lingo.  Nothing is wrong yet, except a lack of sound, but I'll try this out.

---

### Post by velvund5 on 2009-11-19
Thank you [[COLOR=#D40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941"), that is exactly what I was looking for.  Now I have Ubuntu and it converted well.

---

### Post by NoonienSoong97 on 2009-11-19
I was wondering can you then update from ubuntu 8.04 to ubuntu 9.10 using this method?

---

