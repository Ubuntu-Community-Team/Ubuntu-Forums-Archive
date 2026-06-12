---
title: "almost have the network/samba configured, but linux wants password?"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by skelooth on 2005-11-30
My network is set up as follows

my linux box (l337-machine)
and my windows box via wireless (Betsy)
plugged into a netgear wireless g router
in the workgroup mshome

I can access the windows box from linux no problem, both computers can see eachother no problem, pinging works no problem, blah blah blah

but if i try to access linux from the windows machine, it says "enter password for l337-machine/$IPC" or some such nonsense

Not really sure how to stop/change/fix that? I tried adding Betsy as a user on my linux box but that did not help.

---

### Post by ebrowne on 2005-11-30
try smbpasswd for the user your trying to allow to access the smb mount.

---

### Post by skelooth on 2005-11-30
Thank you very much ebrowne. I solved the issue by running

sudo smbpasswd -n Betsy

then opening smb.conf with

sudo nano /etc/samba/smb.conf

and adding the line

null passwords = yes

once again, thank you very much. This is my first time networking on anything other than windows so it's the same "but different". Out of curiousity, what was the 'default password' for Betsy? Why would samba give a password and not 'tell' anyone?

---

