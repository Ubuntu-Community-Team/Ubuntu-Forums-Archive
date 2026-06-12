---
title: "Unable to Connect Via Samba After Reinstalling Ubuntu"
date: 2021-02-17
forum: Networking &amp; Wireless
---

### Post by geeky-1 on 2021-02-17
I reinstalled Ubuntu 20.04 and applied all updates on my server and shared some folders (reinstalling Samba), but now whenever I try to access a folder remotely, I log in with the password, then the connect dialog keeps popping up, but everything is grayed out except the Connect button. What is wrong here?

---

### Post by #&amp;thj^% on 2021-02-17
Did anything change "/etc/samba/smb.conf"?
Have you since the upgrade restarted samba?
```
sudo service smbd restart

```

---

### Post by him610 on 2021-02-17
This may or may not apply to your situation. It helped me though, especially #6 by Moribus.

[https://ubuntuforums.org/showthread.php?t=2452742&highlight=smb]("https://ubuntuforums.org/showthread.php?t=2452742&highlight=smb")

---

### Post by geeky-1 on 2021-03-07
> **1fallen said:**
> Did anything change "/etc/samba/smb.conf"?
Have you since the upgrade restarted samba?
```
sudo service smbd restart

```
I restarted, but same problem still exists.

---

### Post by Morbius1 on 2021-03-07
Did you remember to add the user to the samba password database:
```
sudo smbpasswd -a some-user-name
```

---

### Post by rsteinmetz70112 on 2021-03-07
Are the smbd and nmbd daemons running?
```
$sudo ps -ef|grep smbd
$sudo ps -ef|grep nmbd
```
Are smbd and nmbd enabled and running
```
$sudo systemctl status smbd status
$sudo systemctl status nmbd status
```
Run testparm and see if the /etc/smbd.conf is OK
```
$sudo testparm
```
Post output of testparm.

---

### Post by rsteinmetz70112 on 2021-03-07
Are the smbd and nmbd daemons running?
```
$sudo ps -ef|grep smbd
$sudo ps -ef|grep nmbd
```
Are smbd and nmbd enabled and starting 
```
$sudo systemctl status smbd status
$sudo systemctl status nmbd status
```
Run testparm and see if the /etc/smbd.conf is OK
```
$sudo testparm
```
Post output of testparm.

---

### Post by geeky-1 on 2021-10-14
> **Morbius1 said:**
> Did you remember to add the user to the samba password database:
```
sudo smbpasswd -a some-user-name
```

This solved the problem. Apparently they changed Samba as this was not necessary a couple of years ago. Thanks.

---

