---
title: "Unable to access the network in gnome."
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by t94xr on 2007-04-09
Im unable to access the network at all, I can setup samba shares and stuff but I'm completely unable to access WORKGROUP. I can enter into it but Im unable to see any computers. Another being a Ubuntu Linux 6.10 Server which I can access quite perfectly on my Windows XP system.

Anyone have any ideas? I've also attempted to manually mount them using smbclient, but no luck.

:(:confused:

---

### Post by meomike2000 on 2007-04-09
have u enabled users for the samba server?
was a problem i had when i first set up a network share on a linux box with windows xp clients.
 
not real sure of the exact problem u are having, need to give more details.
mike

---

### Post by t94xr on 2007-04-10
I can access my laptop remotely with the shares i've setup...
I cant access the network from within linux here...

I try and access WORKGROUP within GNOME and it comes up with an error saying it cant find any workgroup computers.

?

---

### Post by skip27 on 2007-04-10
Can you ping the other computers in your network?

---

### Post by meomike2000 on 2007-04-10
do the other computers have a share set up. do they have a firewall that could be blocking the linux box.
 
is ur linux box in the same workgroup as the other computers?

how are u trying to access "workgroup" and is ur linux box in the same "workgroup" as the others?

---

