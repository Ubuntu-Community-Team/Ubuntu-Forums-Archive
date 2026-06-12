---
title: "Network wants a password?"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by edzell on 2010-06-24
Ubuntu 64-bit 10.04 on laptop

I'm trying to access shared files on desktop PC from new laptop via wired router. Network dialog box asks for a password but my admin PW isn't accepted (Dialog box just reopens.)

I have 2 older desktops plus a new laptop, all wired through a router. One desktop is Win 98, one is Ubuntu 10.04. They shared a network (WORKGROUP ;)) before the laptop arrived. Ubuntu could read the Windows files but not vice-versa.

Now I have connected the laptop. When I try to network it sees the shared folders on the other machines but won't open them without a password which I don't have or don't know.

The laptop is an HP-G60 I was given and had pre-installed Windows 7. After much tribulation trying to dual-boot I've cleaned it off and installed 64-bit Lucid.

I've been playing around with Ubuntu for some time but am still really a newbie.

All (polite) help appreciated

---

### Post by tarps87 on 2010-06-24
I am assuming you are trying to access the files on one of the windows boxes, if so do you use a password to log into that machine? If this is the case you need to use this password. If not try using the username of the user on the windows machine and a blank password. If neither work you will need to check the share settings on the windows box, right click on the folder and then access the share tab (or at least this is the case for 98SE to XP)
Let use know if you have any problems

---

### Post by edzell on 2010-06-24
> **tarps87 said:**
> I am assuming you are trying to access the files on one of the windows boxes, if so do you use a password to log into that machine?

Can't open files on either desktop via the laptop. The Windows one is win98 - no username or password involved. The Ubuntu desktop opens files on the Windows one just fine but the laptop wants a damn password for either of them.

Folders on both desktops are already set to "sharing." The laptop sees them but won't open them without that password. It shouldn't need one for Win98, and for the Ubuntu machine the admin PW doesn't help - laptop networking  just repeats the request for password ad nauseam.

---

### Post by pxr on 2010-06-24
For the shared folders on the Desktop, did you check the box for 'Guest Account' ?

---

### Post by tarps87 on 2010-06-24
All the machines will have a username even if you don't need to enter it to connect even is the username is just admin.
Right so to check:
Ubuntu desktop: Connects to Win98 Desktop but not to the laptop
Ubuntu laptop: Does not connect to Win98 or Ubuntu desktop
Win98 desktop: Doesn't see or connect to either Ubuntu machines
Is this correct?
Have you tried the anonymous login option on the laptop, should be on the same dialogue box as the password entry?

---

### Post by edzell on 2010-06-24
The laptop has developed bigger problems: It's locked up on me several times now, especially when filling forms (like this one, now coming from the desktop) and when running Evolution, which used to run OK but now won't download mail and hangs. (Reinstalled it to no avail.)

But to answer your questions:

> **tarps87 said:**
> All the machines will have a username even if you don't need to enter it to connect even is the username is just admin.

Maybe we've got some ambiguity here regarding names - computer name vs username? All the machines have names but only the Ubuntus are employing a username. Actually the same  (sole) username & admin password on both.

> Right so to check:
Ubuntu desktop: Connects to Win98 Desktop but not to the laptopUbuntu desktop networks fully with Win98. Sees name of laptop and name of its shared folder but won't open it without a password.

> Ubuntu laptop: Does not connect to Win98 or Ubuntu desktopUbuntu laptop sees both desktop names and names of shared folders but won't open them without......

> Win98 desktop: Doesn't see or connect to either Ubuntu machinesWin98 sees names of both Ubuntus. Sees names of shared folders but can't open them; Incompatible filesystems.

> Have you tried the anonymous login option on the laptop, should be on the same dialogue box as the password entry?Not certain what this means. I log in as admin (sole user) without providing my password

---

### Post by edzell on 2010-06-24
> **pxr said:**
> For the shared folders on the Desktop, did you check the box for 'Guest Account' ?

No I didn't. Now I have and it helps a LOT :p. How simple. Thanks, pxr.

---

### Post by tarps87 on 2010-06-24
> **edzell said:**
> Maybe we've got some ambiguity here regarding names - computer name vs username? All the machines have names but only the Ubuntus are employing a username. Actually the same  (sole) username & admin password on both.


Nope we are on about the same thing, the 98 machine will be using a username just not so obvious or easy to identify and not in the same sense as Ubuntu or even xp ;)

> **edzell said:**
> 
Not certain what this means. I log in as admin (sole user) without providing my password

I was referring to when it requested the login password for the share, this however would have returned the same error, as I missed the simple solution. I just wasn't sharing #-o
Glad it's solved

---

