---
title: "[SOLVED] Do I need anti-virus/spyware software?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by jalehtor on 2008-12-15
I'm new to Ubuntu, and have it installed on a completely stripped machine--no windows on it. Will I need to install a program like Avast to keep Ubuntu safe from viruses? I've heard that Ubuntu does not get viruses, but I wanted to double check--I'm an xp/Vista survivor, so anti-virus/spyware programs seem like absolute necessities to me.

---

### Post by oilchangeguy on 2008-12-15
> **jalehtor said:**
> I'm new to Ubuntu, and have it installed on a completely stripped machine--no windows on it. Will I need to install a program like Avast to keep Ubuntu safe from viruses? I've heard that Ubuntu does not get viruses, but I wanted to double check--I'm an xp/Vista survivor, so anti-virus/spyware programs seem like absolute necessities to me.

read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by nhasian on 2008-12-15
you dont need it, but if you have to have an anti virus program you can install clamav.

```
sudo apt-get install clamav
```

and if you want a graphical from end for clamav:

```
sudo apt-get install clamtk
```

---

### Post by Achetar on 2008-12-15
It is a good idea to have antivirus software if only to keep yourself from passing email viri on to friends.

---

### Post by Michael.Godawski on 2008-12-15
hi, humbly adding my article:
[http://godawski.oxyhost.com/viruslinux.html](http://godawski.oxyhost.com/viruslinux.html)

---

### Post by NewJack on 2008-12-15
Here is a post you should have a look at in addition to the Psychocats site to give yourself a clearer picture of security in Ubuntu.  It was made by bodhizazen:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by PocketDog on 2008-12-15
The chances of you unintentionally sending someone a virus *and them being infected by it* is so close to zero it would make a mathematician's eyes water. No, you don't need an anti-virus.

---

### Post by Nepherte on 2008-12-15
> **Achetar said:**
> It is a good idea to have antivirus software if only to keep yourself from passing email viri on to friends.
I honestly don't think this can be considered a good idea. You really can't be held responsible for someone else's computer security.

In general, you don't need a virus scanner. Every os has its own security measures, just make sure you use the right one (and a virus scanner is not among those measures for linux).

---

### Post by JoshuaRL on 2008-12-15
> **Achetar said:**
> It is a good idea to have antivirus software if only to keep yourself from passing email viri on to friends.

I completely disagree.  In my humble opinion, the only people that NEED an antivirus application are those that run an email server, or some other production server that has file sharing access to Windows computers.  But even the second one is a little iffy.

> **Michael.Godawski said:**
> hi, humbly adding my article:
[http://godawski.oxyhost.com/viruslinux.html](http://godawski.oxyhost.com/viruslinux.html)

Nice article man, well written and precise.  And you stayed away from the "security by obscurity" arguement.  Which (and I know you know this) is completely false.

> **Nepherte said:**
> I honestly don't think this can be considered a good idea. You really can't be held responsible for someone else's computer security.

In general, you don't need a virus scanner. Every os has its own security measures, just make sure you use the right one (and a virus scanner is not among those measures for linux).

Completely agreed.  There are much better antivirus programs for Windows than there are for Linux.  And part of running a Windows OS is learning how to protect yourself and your data.  Putting that off on someone else, especially someone else who has a secure system already, is wrong and is asking for trouble.  You don't ask your neighbor down the street with a nice alarm system and two dogs to make sure no one breaks into your house.  That would be your own responsibility.

---

### Post by NewJack on 2008-12-17
> **JoshuaRL said:**
>  You don't ask your neighbor down the street with a nice alarm system and two dogs to make sure no one breaks into your house.  That would be your own responsibility.

No one is asking you or anyone to install an A/V program.  Some people who receive and share files with Windows users may want to install an A/V to make sure that they are not passing something off to their Win counterparts.

---

### Post by JoshuaRL on 2008-12-17
> **NewJack said:**
> No one is asking you or anyone to install an A/V program.  Some people who receive and share files with Windows users may want to install an A/V to make sure that they are not passing something off to their Win counterparts.

I know no one is.  But there's a difference between having the ability to do something and having a legitimate need to do so.  And while it is everyone's choice, I think the OP would be better served not worrying about it.

---

### Post by billgoldberg on 2008-12-17
> **Nepherte said:**
> I honestly don't think this can be considered a good idea. You really can't be held responsible for someone else's computer security.

In general, you don't need a virus scanner. Every os has its own security measures, just make sure you use the right one (and a virus scanner is not among those measures for linux).

I completely agree with your position on the matter (for desktop users).

---

