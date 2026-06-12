---
title: "Help with remote access over LAN, and making ubuntu into a file server"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by quickshot89 on 2007-10-22
as the title says basically


ive build a very cheap pc (under £50) for a file server for me and the rest of the family can use on our LAN

ive installed what ubuntu asks for, but when i try to open up the folder on xp/vista it asks for username + password, which i dont want, i want an open folder that anyone on the network can view, so howdo i change it?

second, because its a file server, id like it to be out of the way, but id still like control at time, without having to move to the machine, so what things do i need to remote desktop it over my lan, im running vista x86 if that helps at all

---

### Post by ihcnet on 2007-10-22
Check [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29")  out in order to configure the file sharing. Since you're running Windows on your main machine, [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_using_VNC") will probably work best. Cheers.

---

### Post by quickshot89 on 2007-10-22
cheers those methods worked a charm, one last question, how do i disable the user name + password on start up?

---

### Post by ihcnet on 2007-10-22
Go to System>Administration>Login Window go to the Security tab and check the Enable Automatic Login box and choose the user in the drop down menu you want to login automatically. Best wishes!

---

