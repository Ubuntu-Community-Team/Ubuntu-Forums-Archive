---
title: "Connecting Windows to Samba"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by dsbw on 2008-04-16
All the threads I see are about connecting *to* Windows from Ubuntu, I want to do the reverse.

I have a machine "DOE" and a user "JOHN". 

Windows sees the machine and offers a dialog captioned "doe.mydomain.com" with a user name and password slot. If I put in john@doe (w/password), it doesn't work. (It just blinks and comes back.)

I can connect through PuTTY, and it says:

login as: john
john@192.168.2.1's password

And I'm in. 

I've tried variations, but Windows doesn't accept john@192.168.2.1 as valid. It does take "192.168.2.8\andy" but that doesn't work.

There are SAMBA guides on the web, but they're rather involved--I think they're about using SMB as a general share. But John is set up as a user, he has a password, he's the only user I want--is there some way I can that logon?

---

### Post by SpaceTeddy on 2008-04-16
samba uses it's own username password file... i've never quite got around to understanding when a user is IN the database, and when not... but my first guess would be that your username does not show in the smpasswd....

try to add yourself to it with this command
```
sudo smbpasswd -a john
```

then try to log in again. The other solution is to create a public share where anyone can write/read from... 

hope it helps...

---

### Post by Iowan on 2008-04-16
I'm probably misreading something - but "john" should be sufficient for a username. "john@doe" is correct for SSH, but doesn't seem right for Samba login.

---

### Post by dsbw on 2008-04-17
> **Iowan said:**
> I'm probably misreading something - but "john" should be sufficient for a username. "john@doe" is correct for SSH, but doesn't seem right for Samba login.

Windows puts the local machine name there if you don't put something else. Or it seems to, I'm going to try the aforementioned technique and see how that goes.

---

### Post by dsbw on 2008-04-17
> **SpaceTeddy said:**
> samba uses it's own username password file... i've never quite got around to understanding when a user is IN the database, and when not... but my first guess would be that your username does not show in the smpasswd....

try to add yourself to it with this command
```
sudo smbpasswd -a john
```

then try to log in again. The other solution is to create a public share where anyone can write/read from... 

hope it helps...

That works. In the sense that I'm in. I'm not seeing John's home directory or anything. That's okay, though, I can work it out from here, I think.

---

### Post by jonandrews on 2008-04-19
I've put together a guide to networking Ubuntu & Windows PC's on a website:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by svaens on 2008-07-09
hi, 

I had the same problem on the machine that I 'upgraded' to Hardy from Gutsy. I followed your instruction to add a username and password manually using the smbpasswd command, 
and it worked! Thanks. 

However, this is a bit silly, and strange. 
does anyone know when this is needed and why? It makes more sense that a user can use his own original 'Ubuntu' username and password to connect, why should we have to maintain an extra set of username passwords!!!

Additionally, At home on my other machine, I installed Hardy FRESH. 
I didn't have this problem. 
I was able to simply create the share using nautilus gui options, 
I think maybe I had to reboot, but after that, I was able to log in. 
Then, to give my partner access, all I had to do was give her an UBUNTU login, and then she could get in. I never had to do a smbpasswd command. 

Is this a bug in upgrading perhaps? Was functionality (or default configuration) fixed in hardy, but  in an 'upgrade' is forgotten?

---

