---
title: "Samba continues to fight me at every turn"
date: 2020-10-19
forum: Networking &amp; Wireless
---

### Post by inotamira2 on 2020-10-19
I JUST had this working the day prior on an Odroid HC2 using Ubuntu Minimal. The print$ directory shows up, and nothing else no matter what I do to the Samba file. Preferably, I'd like the NAS folder, which is actually the NAS drive itself, to be listed as the only share, before I had to work around this by having the homes folder shared and using that because Samba suddenly stopped sharing when using a path, now nothing is working.

Edit: Why are there two smb.conf locations? Edit /etc/samba/smb.conf not /user/share/samba/smb.conf. OP is retarded.

---

### Post by TheFu on 2020-10-19
```
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic  
# errors. 
```
Did you do that?

Did you set the samba password using smbpasswd?

Firewall?

Anything in the logs?

---

### Post by rsteinmetz70112 on 2020-10-19
Did you restart smbd and nmbd?

---

### Post by inotamira2 on 2020-10-19
Yes, and it claims everything is fine, but during the dump, it only shows global, printers, and print$. Yes I've set the password. No firewall. Samba logs say everything is fine. It seems like the changes I make, it doesn't pick up, and I don't know why, and to the other person who respondeds question, I restart nmdb and smdb every time I make a change, and yes, I've also tried rebooting the device.

Edit: So, I've been editing the smb.conf at /usr/share/samba/smb.conf which apparently isn't where Samba reads from, but is where I've been told to edit the conf multiple times. I've been needing to edit the one at /etc/samba/smb.conf . Either I'm an idiot and somehow missed the fact this is where everyone else is editing it (probably) or this should really be noted better in the documentation. To make it more clear, it's working now.

---

### Post by rsteinmetz70112 on 2020-10-19
Try editing 
```
/etc/samba/smb.conf
```
That's where mine is, but they may have moved it. I don't even have an /etc/share on my system.

---

### Post by inotamira2 on 2020-10-19
> **rsteinmetz70112 said:**
> Try editing 
```
/etc/samba/smb.conf
```
That's where mine is, but they may have moved it. I don't even have an /etc/share on my system.

Your timing is beautiful my guy, I just figured this out AS you posted this.

Edit: I'm doubly stupid, because I added share to the directory out of habit...

---

