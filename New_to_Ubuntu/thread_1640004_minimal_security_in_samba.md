---
title: "minimal security in samba"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by ilantal on 2010-12-07
By /etc/samba/smb.conf I can get no security, so the next step is to get some minimal security. I have taken [print$] as my test case. It comes up with user name, domain and password. The user name is correct with my login name, the domain is WORKGROUP which is also correct. When I put in my password it refuses to connect.

The relevant part in smb.conf is:
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
;   security = share
;   force user = nobody
;   force group = nogroup
   guest ok = no

As you can see I've tried some experiments with security and force user and group. Nothing works. On the other hand if I change guest ok = yes, up it comes, but with no password.

If nothing else works, I'll use it with no security, but I think there must be a better way.

Thanks,
Ilan

---

### Post by cariboo on 2010-12-07
The samba3 by example guide may be helpful you can see it here:

[http://www.samba.org/samba/docs/man/Samba-Guide/](http://www.samba.org/samba/docs/man/Samba-Guide/)

---

### Post by 3rdalbum on 2010-12-07
The semicolon before "security" - is that commenting out that line?

Also have you tried a frontend like system-config-samba, or shares-admin?

---

### Post by inobe on 2010-12-07
what procedure did you use to install samba and the steps you used to configure it, also did you backup your untouched smb.conf ?

---

### Post by bodhi.zazen on 2010-12-07
See also :

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html)

In general, I firewall my samba server + security = user.

If you need more then that, take a look at kerberos, although that is almost certainly overkill for more people.

---

### Post by CharlesA on 2010-12-07
My Samba server is firewalled.

Only difference is that I have security = user commented out, however, I've got mine set up with each directory locked down to their respective user using both linux file permissions and share permissions (valid/invalid users)

---

### Post by inobe on 2010-12-07
i don't think the op created a user name and password for the share.

```
sudo smbpasswd -a username
```


please post the steps you used to configure samba.

---

### Post by ilantal on 2010-12-08
As usual, the simple answer is the correct one....
I didn't do anything special to configure Samba, and that was the problem.
The code
sudo smbpasswd -a username
solved my problem. I didn't know that Samba had its own password. I was reading in great detail on smb.conf but I missed the big picture.

What is really very nice is that people like you take the time to help when I was missing something really stupid.

Thanks,
Ilan

---

### Post by inobe on 2010-12-08
> **ilantal said:**
> As usual, the simple answer is the correct one....
I didn't do anything special to configure Samba, and that was the problem.
The code
sudo smbpasswd -a username
solved my problem. I didn't know that Samba had its own password. I was reading in great detail on smb.conf but I missed the big picture.

What is really very nice is that people like you take the time to help when I was missing something really stupid.

Thanks,
Ilan

you are very welcome, if you need anything even if you wish to start over and do it rite' feel free to create a thread and contact me, i really don't mind helping.

---

### Post by CharlesA on 2010-12-08
That's what we are here for. :)

Don't forget to mark the thread as solved from thread tools.

---

