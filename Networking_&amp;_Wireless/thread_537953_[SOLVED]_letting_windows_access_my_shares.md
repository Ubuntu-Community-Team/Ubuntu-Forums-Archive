---
title: "[SOLVED] letting windows access my shares"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by kubilaycan on 2007-08-29
hi

i use feisty, the dude upstairs has xp. i can access his shares with no problem. but when he goes (in windows) to network computers and double clicks on mine, it asks for user name and password.

i dont get it. i shared my folders using the system>>administration>>shared folders. domain workgroup is called workgroup and currently i have the WINS server setting ticked. it was unticked before and still didnt work.

i repeat once again, i can access his shared folders through the network perfectly! i can transfer files over to my computer. but whenever he tries to access mine it asks for user name and password.

so whatsup?

thx

---

### Post by kubilaycan on 2007-09-16
solved: 

just followed this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)

tip: look out for the semicolon before "security = share" in smb.conf. you have to remove it.

---

