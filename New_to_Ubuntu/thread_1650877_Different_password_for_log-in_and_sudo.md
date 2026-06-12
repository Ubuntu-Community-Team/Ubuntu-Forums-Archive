---
title: "Different password for log-in and sudo?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Agester on 2010-12-22
Hey all, let me start with me wanting to tell you all that you guys are an awesome community!

Onward to the thread. I was wondering if it would be possible to set up two separate passwords 1) a log-in password and 2) a sudo / synaptic etc. password.

The main purpose is that my user password is quite long to prevent brute force attacks in the event i ever lose my laptop (i do not want to make it easy for thieves!), but at the same time I find it a tad annoying to keep typing in my long password, but do not want to leave the system open / exposed in the event my little niece or curious siblings walks over to the computer and accidentally destroys or maims my lovely Ubuntu system.

Thank you :D

Edit: for typos!

---

### Post by matt_symes on 2010-12-22
Hi

Have a look at this thread. There are a couple of solutions offered.

[http://ubuntuforums.org/showthread.php?t=1647001&page=2](http://ubuntuforums.org/showthread.php?t=1647001&page=2)

> but at the same time I find it a tad annoying to keep typing in my long password,

Have you just moved from windows? Password typing is part of Ubuntus security model.

Kind regards

---

### Post by amjjawad on 2010-12-22
Welcome to Ubuntu ;)

Just wanted to add this link: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Hope this will help you to understand how Ubuntu (Linux) works :)

---

### Post by QLee on 2010-12-22
Don't forget Agester, when they have physical access of your stolen laptop, they will just boot up with a live CD and do what they please.

---

### Post by bodhi.zazen on 2010-12-22
> **QLee said:**
> Don't forget Agester, when they have physical access of your stolen laptop, they will just boot up with a live CD and do what they please.

Which is why I encrypt my data , at least /home, on portable devices.

They can have the laptop, but they do not get any sensitive data.

---

### Post by QLee on 2010-12-22
[QUOTE=bodhi.zazen]Which is why I encrypt my data , at least /home, on portable devices.

They can have the laptop, but they do not get any sensitive data.[/QUOTE]

Excellent advice for security.

---

### Post by Agester on 2010-12-22
> **bodhi.zazen said:**
> Which is why I encrypt my data , at least /home, on portable devices.

They can have the laptop, but they do not get any sensitive data.

Same here. I'm trying to be as careful as possible.

But as it seems. there isn't really a feasible way to have sudo passwords and log-in credentials to be different on the same user. I guess i'll marked this as solved (since it is in a sense!).

Thank you guys for the help and info!

---

### Post by amjjawad on 2010-12-22
My sensitive data is not on my PCs.
If someone wants to steal my PCs, they're more than welcome :D

---

### Post by QLee on 2010-12-22
[QUOTE=Agester]...
But as it seems. there isn't really a feasible way to have sudo passwords and log-in credentials to be different on the same user. I guess i'll marked this as solved (since it is in a sense!).
...[/QUOTE]

It seems that you are an experienced user, you could consider using a distro that doesn't use sudo the way Ubuntu does, for example Debian, then you'd have to su to root and that could have a complicated password.

Or, on Ubuntu, you might consider setting up another user with more limited rights and doing user switching to your secure password user when you have a specific admin task to do that you don't want the kids to have access to. [Edit] Not sure why locking the screen when you leave the machine and not sharing the password with the kids wouldn't be effective but I probably haven't thought about something specific to your situation.

---

### Post by bodhi.zazen on 2010-12-22
> **Agester said:**
> Same here. I'm trying to be as careful as possible.

But as it seems. there isn't really a feasible way to have sudo passwords and log-in credentials to be different on the same user. I guess i'll marked this as solved (since it is in a sense!).

Thank you guys for the help and info!

It is possible, it was mentioned in the link you were given.

See : [http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

Specifically see rootpw, targetpw , etc.

Yes we expect you to read the man pages with security and sudo related topics, you need to understand what you are doing.

> **amjjawad said:**
> My sensitive data is not on my PCs.
If someone wants to steal my PCs, they're more than welcome :D

Aye, it depends on what you use the device for. For personal use you may not have any sensitive data.

Of course you can always keep data on an encrypted usb device as well.

My point is, if you have sensitive data you need to encrypt it.

---

### Post by amjjawad on 2010-12-22
> **bodhi.zazen said:**
> My point is, if you have sensitive data you need to encrypt it.

Agreed :)

---

