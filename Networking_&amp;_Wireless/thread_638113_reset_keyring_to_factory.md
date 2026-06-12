---
title: "reset keyring to factory"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by coloured on 2007-12-11
Keyring has become retarded and no longer works as it should. I get prompted to unlock the keyring, which I do successfully (even after I have ticked the box to say unlock this keyring upon logging in). I get prompted for every VPN connection I establish, and even though I have checked the box to save the credentials in keyring.

How can I reset keyring - so that I can start fresh, and maybe then the check boxes will work.
I have reinstalled certain components, but because it embeds itself in many components I cant reinstall everything, for example it wants to reinstall compiz and gimp etc.

running gutsy all up to date. using nm for the vpn's (pptp plugin)

Please help me, this is very very annoying.
Jurgen

---

### Post by Prometheum on 2007-12-11
Have you tried deleting your keyring files?

They're located in ~/.gnome2/keyrings .

I presume deleting the keyrings would also reset the setting associated with them. Good luck.

---

### Post by coloured on 2007-12-11
thanks, I actually had to delete these and go into keyring manager and delete the entries from within there. 
for some reason there were multiple entries for the same object - i guess this is why it was confused.

thanks for the help.
Jurgen

---

### Post by 99bluefoxx on 2007-12-12
on the issue of the keyring; how do i reset my passcode?
i set to something secure in the spirit of security, and promptly forgot what it was, now when it comes up, i cant use it
i dont weant to re-install my os, but thats the only thing i could think of

---

