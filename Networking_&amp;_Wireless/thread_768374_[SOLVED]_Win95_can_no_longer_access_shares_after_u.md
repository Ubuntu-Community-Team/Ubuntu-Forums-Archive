---
title: "[SOLVED] Win95 can no longer access shares after upgrade"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by jjj_uk on 2008-04-26
Hi there,

I've just upgraded to Hardy from Gutsy and found than an old Win95 box can no longer access the Ubuntu shares. It now asks for the password.

I've kept the same smb.conf file during the upgrade and have also re-added the same username and password to the list of Samba users.

Ubuntu can see and access the Win95 shares and the Win95 box can see and access other WinXP boxes on the network. The XP boxes can access the Ubuntu shares with no problems as before. 

I can ping the Ubuntu machine from Win95, but no joy otherwise.

Anyone found a solution to this?

ta,

j

---

### Post by jjj_uk on 2008-05-06
Just a quick update on this.

The issue seems to be that since the upgrade, Win 95 is no longer granted access to IPC$ shares on the Linux box since Samba security was improved meaning the password is not accepted.

A workaround seems to be to set the smb.conf file to 'security = share' rather than 'security = user'. This gives a password dialog box directly to the Public folder and the password is now accepted.

I would still prefer to use User though in the interests of security if anyone has any further suggestions.

ta,

j

---

### Post by jjj_uk on 2008-05-10
It seems the fix for this is as follows:

1) In smb.conf set security = user
2) Then add and set lanman auth = yes and client lanman auth = yes.
3) Use the terminal and smbpasswd -a <username> and smbpasswd -e <username> to re-add and enable the username and password of the Win9x machine which should be the same as the Ubuntu username and password.
4) Restart Samba and away you go.

I hope this helps someone with the same problem.

j

---

### Post by Iowan on 2008-05-11
Had you not mentioned keeping the same smb.conf file, I'd ask about the **encrypt passwords =** option.  Win95 did not, most other OS's since then do.

---

