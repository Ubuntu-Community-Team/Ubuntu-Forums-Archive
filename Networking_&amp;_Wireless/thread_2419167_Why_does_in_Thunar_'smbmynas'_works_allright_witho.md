---
title: "Why does in Thunar 'smb://mynas' works allright without having samba installed?"
date: 2019-05-17
forum: Networking &amp; Wireless
---

### Post by r.vanderspank on 2019-05-17
Hello, I just reinstalled Xubuntu 18.04. I was surprised to see that typing 'smb://mynass' in Thunar works without having samba installed. After enabling ufw, it didn't work anymore. Since Samba is not installed, I cannot use 'sudo ufw enable Samba.' Do you understand what is going on? Thank you.

---

### Post by TheFu on 2019-05-17
Samba is a sharing server, not the client.

Your system is acting like an SMB/CIFS client. The GUI tools, like Thunar are probably using GVFS and might have the GVFS-SMB client library included by default.

Have you checked the log files?  That's where issues should be logged.

---

### Post by Morbius1 on 2019-05-18
> I was surprised to see that typing 'smb://mynass' in Thunar works without having samba installed.
But libsmbclient is installed and that is all you need to connect to a SMB server.

And as far as ufw see if this helps you: [https://askubuntu.com/questions/875845/kernel-4-8-ufw-and-smb-not-working-together](https://askubuntu.com/questions/875845/kernel-4-8-ufw-and-smb-not-working-together)

I don't run Linux on anything mobile so I don't use ufw. I'm assuming the above works since I've seen it before in other places.

[COLOR=#0000cd]**EDIT**[/COLOR]: THis whole thing looks like a problem specific to netbios. When you run **thunar smb://mynas** you are accessing it by it's netbios name. I betcha if you were to connect to it by it's ip address or mDNS host name ( if it had one ) the problem would not be there.

---

