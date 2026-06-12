---
title: "Security article response"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by zer010 on 2009-08-29
I was wondering what ya'll think of this article:  [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)   .  Does it make any good points?  How much, if any, should be done to an updated "Jaunty" install?   Thanks for any tips or opinions!

---

### Post by Liolikas on 2009-08-29
Those advices will not hurt but they are not important too unless you have some government secrets on your pc.
---
Also if you do not use sshd and you have it on by default so really better to turn it off at all.

---

### Post by oldos2er on 2009-08-29
I stopped reading when the author said Firestarter is a firewall. This is better info: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by inobe on 2009-08-29
just my opinion' the desktop user need not worry, just have fun and enjoy learning what you love.

now if your the head of IT department or have servers and your protecting critical information' then of course you would want to harden your linux.

---

### Post by woedend on 2009-08-29
> **oldos2er said:**
> I stopped reading when the author said Firestarter is a firewall. This is better info: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Interesting perspective, but it is fair to call Firestarter a firewall.  Many people say "Firestarter isn't a firewall its a GUI frontend"  You can get into the debate by saying "iptables is the firewall!"..but that isn't really right either.  Iptables is more of a filtering engine/framework.  But it needs to be told what to do by configuring rules, be it manually or with a GUI.  So, while it is true that firestarter without iptables is useless(read: won't work)...firestarter does set iptable rules to create what can be called a "firewall".  But it's not necessarily fair to call it a "gui frontend"...as it doesn't need to be run as GUI... I used to run it as a daemon only when I needed ics configured.  That said, firestarter as I understand it doesn't get worked on much anymore other than the dozens of patches that have been applied to fix memory leaks...but it still does its job and I liked it better than gufw.

---

### Post by str8outtacpt on 2009-08-29
> **woedend said:**
> Interesting perspective, but it is fair to call Firestarter a firewall.  Many people say "Firestarter isn't a firewall its a GUI frontend"  You can get into the debate by saying "iptables is the firewall!"..but that isn't really right either.  Iptables is more of a filtering engine/framework.  But it needs to be told what to do by configuring rules, be it manually or with a GUI.  So, while it is true that firestarter without iptables is useless(read: won't work)...firestarter does set iptable rules to create what can be called a "firewall".  But it's not necessarily fair to call it a "gui frontend"...as it doesn't need to be run as GUI... I used to run it as a daemon only when I needed ics configured.  That said, firestarter as I understand it doesn't get worked on much anymore other than the dozens of patches that have been applied to fix memory leaks...but it still does its job and I liked it better than gufw.

this has nothing to do with the post but im in desperate need. i think i did something very bad. i put linux on my computer and i accident went to partition editer and made my hard allocated instead of ntfs but i never commited the change but i cant back to windows and i do not have anything to back it up with so is there anyway i can get windows back without losing all my data?

---

### Post by woedend on 2009-08-29
> **str8outtacpt said:**
> this has nothing to do with the post but im in desperate need. i think i did something very bad. i put linux on my computer and i accident went to partition editer and made my hard allocated instead of ntfs but i never commited the change but i cant back to windows and i do not have anything to back it up with so is there anyway i can get windows back without losing all my data?

You should really make a new thread with this so that you can get proper help but need to include more information....a step by step of what exactly you did and where you did it at..etc.  In any event, data recovery is usually possible...how hard it is depends on what happened...but please make yourself a new thread.

---

