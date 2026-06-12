---
title: "Joining an Ubuntu client to Samba domain"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by beaker15 on 2008-04-02
Hi, 
I have an ubuntu server working as a samba domain controller and about 10 XP clients. Users log in with username and password and have their profiles stored on the server and also can access shares on the server (assuming they have permission to).

Now I want to add an Ubuntu client to the network so it works in the same way, ie user logs in and it loads the user profile from the server and accesses the samba shares with correct samba permissions. Any tips on doing this? 

I take i just use the 'net join' command to join the pc and create local users on the ubuntu client that match up with the samba users?

---

### Post by beaker15 on 2008-04-08
ok i'll re-word it. Obviously on Linux i don't get a splash screen at startup with a choice of whether the user logs in locally or to the domain so is it just a case of Joining the PC to the domain? Then if I do this, how can i sync local linux users with the Samba users on the server? can it be done at all?

Surely someone must have a Samba domain controller serving a Linux client, how is it set up?

thanks for any replies

---

