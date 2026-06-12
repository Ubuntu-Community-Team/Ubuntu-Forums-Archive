---
title: "How do I &quot;manually run&quot; something?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by PeterJD on 2009-10-28
Hi,
This must be the most basic ("stupid") question ever.
 
When I recently tried to install some updates I got the message that a previous install had been interrupted and I should manually run 'dpkg --configure -a'
 
The problem is that I just don't know how to manually run something.  ( I am completely new to Ubuntu)
 
So please "in words of one syllable", how do I do it?  Starting from just the desktop exactly, in detail, what do I do?  (Don't assume I know anything except what I've learnt from years of using Windows)
 
Thanking you in advance,
 
PeterD

---

### Post by howefield on 2009-10-28
Open a terminal (Applications > Accessories > Terminal) and type

```
sudo dpkg --configure -a
```

Enter your password when prompted andpress enter.

---

### Post by philinux on 2009-10-28
Open a terminal apps>access>terminal

```
sudo dpkg --configure -a
```

Press enter

---

### Post by SunnyRabbiera on 2009-10-28
Command line is your answer, you will have to use a terminal to fix your issue.
In linux we tend to use text commands more often then Windows, but hopefully you wont have to touch it that often.
The dpkg --configure -a message is a well known issue for new users.

---

### Post by PeterJD on 2009-10-29
Thanks very much.  That fixed it.

---

### Post by Bandio on 2009-11-13
I also am a newbie.  I typed the sudo command several time before I realized that the spacing between the words made a difference because it does not recognize the command.  Something I did not know about commands. Peace to all

---

### Post by mrothgeb on 2009-11-13
> **PeterJD said:**
> Thanks very much.  That fixed it.


Welcome to Ubuntu!

---

