---
title: "Samba no longer works!"
date: 2004-12-07
forum: Networking &amp; Wireless
---

### Post by WorLord on 2004-12-07
Hello, all.

I have several samba shares mounted via /etc/fstab.  These drives are simple: /[servername]/[sharename] /mnt/[sharefolder].  They all currently work exactly as they should... unless I use Nautilus.

At some point, I lost the ability to graphically see the contents of any /mnt/[sharefolder]s.  The throbber animation goes to town, indefinitely, but no contents show up.  Nautilus does not, however, freeze-up or crash - I can change folders at any time, and its as responsive as ever.  I can open a terminal and cd into /mnt/[sharefolder] and see everything just fine, also.

Nautilus used to have no problems with this whatsoever.

Also, I didn't notice that there was a problem for a while, because I have /mnt/[sharefolder]/folder symlinked to my home directory.  I can see and manipulate the contents of this subfolder - just not with the main mount folder itself.

It's pretty strange, and is a niggling pain in the butt.  

Has one of the security updates borked this?  Or is it something I'm doing?

(Using Warty 4.10, system with no other noticeable problems)

---

### Post by WorLord on 2004-12-07
Okay, strangeness abounds, but everything is still more or less functional now.

The /mnt/[sharefolder]'s in question that were tripping Nautilus up were all C$ shares.  (I found this out when I browsed to one that wasn't a C$ share, and it pulled right up).

Mounting *actual* Samba shares (not C$) with fstab, and browsing them in Nautilus, works just fine.  Even with domain username/password protection.

Thanks for reading, and hopefully, this helps someone else out.

---

