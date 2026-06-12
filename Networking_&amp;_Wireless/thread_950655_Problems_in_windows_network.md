---
title: "Problems in windows network"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by jefersonpreti on 2008-10-17
Hi. I dont't have much experience with networks and much less ubuntu, and I have a problem with ubuntu access in a Windows Network. I install and configure samba. In Nautilus, I see the network and computers, but I not see the shared files, printers etc. In access to one of this computers (I call it "server", but is a simple pc with windows XP OS), is necessary a login and password for access, and, I don't know how I enter this login in ubuntu. Detail: other computers with windows XP OS see the shared files in this computer with ubuntu OS. I'm brazilian user, sorry for the bad english. Thanks!

---

### Post by Liv3dN8as on 2008-10-17
Try ```
smb://ip address
``` in nautilus.

If you have a password and username configured maybe try ```
smb://username:password@ip address
```
or something to the likes of that.

---

### Post by slimx3m on 2008-10-17
sometimes you want to make sure that the server and the client computer are on the same workgroup.  that is something that you would have to update in the samba settings to join a workgroup or domain. that depends how you have your network setup.

---

### Post by jefersonpreti on 2008-10-17
Well, thank you for attention. I put the command "smb://192.168.15.104" to execute in nautilus. Apparently works, did appears the dirs with the hd units from "server", but, when I try enter in one of this dirs, a window ask "username", "domain" and "password" is showed, and it is don't like the login and password that we put in windows XP PCs, where the ask is "server", "username", "password". Our network don't have a domain. But, certainly, is a progress, thanks.

---

### Post by jefersonpreti on 2008-10-17
Curios... To enter in a shared dir in my owner computer although the networks, the window ask username, domain, password is showed too. Isdifferent in windows XP and is a new for me. Really  I'm much to learn in ubuntu... Please give-me a tip to solve this. Thanks...

---

### Post by Liv3dN8as on 2008-10-17
Sorry for the long wait. Did you try without putting anything in for the domain? Otherwise on your XP machine go to control panel -> sytem; there might be something there that will tell you your domain.

---

### Post by jefersonpreti on 2008-10-22
Hi, don't worry and thank you. The actual situation follow:
- In XP systems, there is no domain, only workgroup;
- In SAMBA conf, I don't see nothing about domain name config, I put in workgroup the same name used in XP systems;
- In Network view, in Nautilus, I see all computers of the network. In access of the shared files of this machine (Ubuntu) although the network, and inserting the login and password writed in samba conf, the access is available;
- The access to shared files of ubuntu machine from the XP machines is available too, by the insert of login and password;
- In Nautilus, if I click in some computer of the network, after a time of processing, nothing appears. Only if I insert IP address I can "access" the files of the computers (in truth, I can see the files, but I can't to access then, because the login window is showed). The computers of the Network operates in automatic IP obtaining. So, I have difficult to know what IP is one determined machine.

Thanks very much for help (and one more time, sorry for the bad english!)

---

### Post by jefersonpreti on 2008-10-22
I think that my problem is pure ignorance mine in ubuntu and network! It is a idiot error, how enter with correct username and password in ubuntu to access another pcs, something like this. But in searchs, I don't see nothing like my problem. I see cases in that ubuntu not see the network XP, or XP not see ubuntu, etc... But's ok. Help please..

---

