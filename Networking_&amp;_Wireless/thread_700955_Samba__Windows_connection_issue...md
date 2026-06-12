---
title: "Samba / Windows connection issue.."
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by tiger.woods on 2008-02-18
I had Samba working with Gutsy and my Windows XP at one time but now when I try to enter my username and password to access the share from Windows I get "incorrect password or username".

So, I went to reset the password on buntu 'smbpasswd -a myuser' and get the following error:

host@host02:/home/mythtv$ sudo smbpasswd -a myuser
New SMB password:
Retype new SMB password:
Failed to modify password entry for user

I also can't remove the user:

host@host02:/home/mythtv$ sudo smbpasswd -x myuser
Failed to modify password entry for user myuser
host@host02:/home/mythtv$ 

Can someone point me in the correct direction?

Thanks,

---

### Post by jhetrick62 on 2008-02-19
Did you try these commands from the server itself or remotely from your windows machine while logged into this server?

Jeff

---

### Post by tiger.woods on 2008-02-19
> **jhetrick62 said:**
> Did you try these commands from the server itself or remotely from your windows machine while logged into this server?

Jeff

On the server.

---

### Post by lnx4me on 2008-02-19
Well thats an odd problem. Restart samba first and then try to reconnect.

---

### Post by tiger.woods on 2008-02-20
Tried that with no success...

---

### Post by lnx4me on 2008-02-21
post your config file.

---

### Post by Iowan on 2008-02-21
Although it seems to me like that shoulda worked, you could first
```
sudo su -
``` 
then try the commands again.
**exit** to return to normal user.

---

