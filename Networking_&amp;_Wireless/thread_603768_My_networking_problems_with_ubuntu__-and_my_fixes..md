---
title: "My networking problems with ubuntu  -and my fixes."
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Mcavity on 2007-11-05
Ok.
This is going to be my diary of fixes for my networking issues.

Transferring a 800 meg file from a samba share from XP to the Linux box takes 2 hours.

I think the problem is relates to IPv6. 
Solution . Disable IPv6. 
Google finds this. 

gksudo gedit /etc/modprobe.d/aliases

Change
alias net-pf-10 ipv6
to
alias net-pf-10 off

Now the same transfer is down to 24min.  Big improvement. 
However Linux to XP takes 5 min. So there's still something not right. 

Anyone have any ideas?

---

### Post by Mcavity on 2007-11-08
network speed is still on the slow side.
however I did find the fix for my XP boxes asking for username and password when trying to get to the linux shared files. 
I had to make a user with the same name/ password as my xp login name. 

SMB share fix 
make smb account with password same as windows login username
example
 
mike@mike-ubuntu:~$ sudo smbpasswd -a [windows login]
--sudo password--
New SMB password:[windows login password]
Retype new SMB password:

---

### Post by Mcavity on 2007-11-17
update. 
I gave up on the realtek nic. traded out for a Dlink and this seems to have stablised the speeds both up and down. however Im still not going very fast. 

update. It seems that the shares are not mounting via CIFS. 
when I mount a share via CIFS I do get much better speeds. 
I need to figure out why this is not the default.

---

