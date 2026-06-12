---
title: "Samba Messed Up"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2008-08-30
[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

I followed the directions there and messed up my Samba.

When my Ubuntu PC is accessed it shows only the share sandbox (even when it doesn't exist) and doesn't show any others. I cannot even access the sandbox share.

How can I make my samba work again?

---

### Post by RealG187 on 2008-09-01
Please help, I tried restarting the samba service, reinstalling samba and using a different smb.conf file....

---

### Post by bodhi.zazen on 2008-09-03
In general , samba works out of the box.

In general, you can do all the configuration from the gui

[https://help.ubuntu.com/community/SettingUpSamba#Graphical%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Graphical%20Configuration)

The how-to you are following had you create a new user, "sandbox"

So :
[LIST=1]
[*]First, on the server, any shared directories/files must be owned by sandbox.
```
sudo chown -R sandbox /shared_directory
```
[*]Second, you almost certainly need to log out of X and back in (no need to re-boot).
[*]Mount the share from windows, use the user name sandbox and the password you assigned to sandbox.
[/LIST]
If all that fails, please provide additional information.

Is the connection fire walled ?
What kind of connection are you using for vmware ? Bridged ? TAP ? Private ?
Can you ping between ubuntu and windows ?
what error message are you getting when you try to mount the samba share ?
Is the samba share marked read only ?

Post the relevant section on the smb.conf file.

---

### Post by RealG187 on 2008-09-03
I dont want to use the username sandbox, I want it use the default so I can access it from all OSes (mainly windows 98 since it asks for just the password, not a username, so I assume Windows 98 just sends the default username, either my Win98 userame, or my Ubuntu one)

---

### Post by bodhi.zazen on 2008-09-03
Windows 98 ??? LOL

[http://www.windowsnetworking.com/articles_tutorials/w98samba.html?printversion](http://www.windowsnetworking.com/articles_tutorials/w98samba.html?printversion))

I would assume windows 98 is sending your windows user name to samba 

```
sudo  smbpasswd -a user_name
```

where "username" is your windows 98 user.

Add ```
browseable = yes[FONT=monospace]
[/FONT]read only = no
guest ok = yes
``` to your smb.conf under the section for your share

---

### Post by RealG187 on 2008-09-03
It still doesnt work, is there a way to remove the password altogehter? My network was a WEP key and I can make the folders read only if I want (I have one that's read only and one that's not for each computer)

---

### Post by bodhi.zazen on 2008-09-03
Wireless, lol

Try it on a wired network connection first ... wireless just adds a whole layer of complexity ...

---

### Post by RealG187 on 2008-09-03
Well my laptop is on wireless and VM.

I cant put it on wired. I am sure there is something wrong with my samba, before I folowed the directions there everything worked fine.

---

### Post by bodhi.zazen on 2008-09-03
oic, lol

you could purge samba, delete smb.conf, and re-install it

```
sudo apt-get remove --purge samba && sudo apt-get -y install samba
```

You should also check what type of connection you are using with vmware.

---

### Post by RealG187 on 2008-09-03
I purged samba twice and I think I am at default samba setting.

The non-existant share sandbox no longer appears and when I right click a folder, it shares it again.

The username is my own login and password.

Windows 98 still says it's incorrect however. My Ubuntu and Windows username are the same.

But I was reading and it could be that Ubuntu encrypts the password and Windows 98 doesn't understand.

If that is the case I want no password and it just to goto the share automatically.

---

