---
title: "Help me network two ubuntu machines"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by derrick1985 on 2005-05-17
I need some serious help.

I have two ubuntu machines, one i did a normal install on, the other i did the server isntall (base install, it's an old machine) that i put xfce on.

I want to be able to transfer files between the two. The home folders for sure, and i also have two windows partitions on this computer that I want networked as well.

How can I do this?

Thanks.

---

### Post by ruben_b on 2005-05-17
maybe you should take a look at here:
[http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking)

---

### Post by wulf on 2005-05-17
That seems to be assuming that you install Samba on both of the machines. Is that still the case if you're working on a purely Linux based network? I though Samba was for integrating with various forms of Windows rather than to facilitate Linux <-> Linux communications.

Wulf

---

### Post by ruben_b on 2005-05-17
oh, i´ve thought i´ve seen a howto for using "nfs" with linux there, too.
so you should take a look for using "nfs" at the forum.

---

### Post by pappo on 2005-05-17
Derrick

How are the two Ubuntu machines connected ??
Are you cabled through a switch or router, or directly connecting the two with a cable ?

---

### Post by tread on 2005-05-17
Samba might still be a good way to go, it will let you add a windows machine later to the network if you have to!

---

### Post by derrick1985 on 2005-05-17
[QUOTE=pappo]Derrick

How are the two Ubuntu machines connected ??
Are you cabled through a switch or router, or directly connecting the two with a cable ?[/QUOTE]

Router sharing the same internet connection.

See, i'm stuck because i don't have any gui tools in XFCE (well, there is one, but for some reason it won't work for me.

Ex. I'm in windows (xp) and i'm on another machine running ubuntu with xfce4. I go into the servers (under internet) and it detects my windows xp machine, BUT, when I click on it, it asks for a user and pass. I put in my windows Xp user and pass, and it comes back saying incorrect.

I can't figure this out, same things happens connecting ubuntu to ubuntu.

help!

---

### Post by derrick1985 on 2005-05-17
Ok, for some reason or another, I was sucessfully able to get samba to see and mount through fstab my windows shares, finally.

Now, heres a good one for you all. How do i make shares, in XFCE4? EX: share my home folder, with windows, or share it with another linux machine?

---

### Post by fordfan753 on 2005-05-17
[QUOTE=derrick1985]Now, heres a good one for you all. How do i make shares, in XFCE4? EX: share my home folder, with windows, or share it with another linux machine?[/QUOTE]

Just edit /etc/samba/smb.conf so that it's sharing your home directory, or any others you want. For the layout and options to use just look at your other machine presuming it has files shared, although it shouldn't be neccessary to look if it's only your home directory you want to share.

---

