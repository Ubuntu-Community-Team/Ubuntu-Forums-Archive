---
title: "samba issues gutsy / xp / vista"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by n00rt on 2008-02-04
Hi - i have a network at home with ubuntu gutsy an XP laptop and a vista machine - i can access the ubuntu shared folders from the XP laptop  but cannot get onto any workgroup from ubuntu and vista is not seeing the ubuntu machine either? 

I need to be able to have access to the vista pc from ubuntu  - and possble mount it at startup if possible

any suggestions on how to get this working smoothly?

thanks!

---

### Post by OffAxis on 2008-02-04
This is what you're looking for:
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

For a quick connection (just to test) you can use the command line
```
smbclient -W [workgroup] -L [servername]
```
and it'll show what's available.
[servername] is it's windows netbios name


from there you can connect with
```
smbclient //servername/foldername
```

---

### Post by n00rt on 2008-02-05
hey thanks! all seems to be networked fine now - much easier than getting vista to appear  in an all xp network!

---

