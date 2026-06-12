---
title: "Network several computers..."
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2007-12-14
I'm still in the process of converting 5 machines to EEft, same version on 4 so far - WITH SAME NAME, SAME USERNAME, AND SAME PASSWORD.

Will this make for problems in sharing? Make for easier sharing?

Internal security, and wireless security aren't concerns, if this makes any difference...

---

### Post by jonallport on 2007-12-14
Yes, this will cause problems.  Machine names need to be unique; u/name and p/word doesn't matter except from a security standpoint.

---

### Post by buccaneere on 2007-12-14
> **jonallport said:**
> Yes, this will cause problems.  Machine names need to be unique; u/name and p/word doesn't matter except from a security standpoint.

Great - thanks...

How do you change the name of your machine? Bios? Login?

---

### Post by jonallport on 2007-12-14
# hostname {new_host_name}

or

vi /etc/myname

---

### Post by mellowd on 2007-12-14
You could keep it simple like PC1, PC2 and so on

---

### Post by buccaneere on 2007-12-14
> **mellowd said:**
> You could keep it simple like PC1, PC2 and so on
 Good simple idea there, mellow(for my simple mind:lolflag:).

usernametagmachinename? @ machinename?

Any more, and I'll have to start takin' off a shoe to count 'em.

---

### Post by buccaneere on 2007-12-26
> **jonallport said:**
> Yes, this will cause problems.  Machine names need to be unique; u/name and p/word doesn't matter except from a security standpoint.

I just found this there, jona...

[QUOTE=stormbringer]Add your useraccount to samba (the smbpasswd thing) and Samba should grant your Windows box access automatically!

Just to stress it once again - this'll only work if both useraccounts on both computers and both OS's have [COLOR="Red"]the very same username/password combo[/COLOR]. If this isn't the case then it won't work out automatically.[/QUOTE]

...from his samba tutorial.

What gives? I need a little help here...

---

### Post by buccaneere on 2007-12-28
> **buccaneere said:**
> I just found this there, jona...



Just to stress it once again - this'll only work if both useraccounts on both computers and both OS's have the very [COLOR="Red"]same username/password combo[/COLOR]. If this isn't the case then it won't work out automatically.

...from his samba tutorial.

What gives? I need a little help here...

 [HTML]Originally Posted by stormbringer
Add your useraccount to samba (the smbpasswd thing) and Samba should grant your Windows box access automatically![/HTML]

---

