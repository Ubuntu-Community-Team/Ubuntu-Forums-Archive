---
title: "Ubuntu 11.04 - Wireless is only working for one user"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by joeharris5 on 2011-05-05
Hello Community, 

I'm just upgraded to Ubuntu 11.04 and something strange is happening with my wireless connection.  It is working for one user, but isn't working for another user.  I'm not sure where to start to begin debugging this issue, any help would be greatly appreciated.

Thanks, 
Joe

---

### Post by dwhite on 2011-05-05
if you set up wireless access in one account and you want all accounts to have access then you can check the "available to all users" box when you edit the connection.

go to system settings -->network connections   click on wireless tab, find connection you want to edit, click it to highlight, click edit, in the lower left hand corner of the window that opens is a check box "available to all user" check it and all users should have access.  Alternatively each user could set up in their own account but that would require they all know the wireless security key

---

### Post by joeharris5 on 2011-05-06
I've selected the option to enable wireless network for all users, but I still can't access the network with my other user.  When I open the Network Connections form from the System Settings GUI, I can see the Wireless Connection that I just checked, but it will not connect.  I don't have the wireless network icon, in the top right tray (next to the date) for my second user, and I have set the same privileges for both user's in the User and Groups administration.  

joe@joe-MM061:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
joe@joe-MM061:~$ 

Let me know if you need more data.

Thanks, 
Joe

---

### Post by joeharris5 on 2011-05-06
I went ahead and ran lsusb, lspci, and dmesg for both users.  Results are attached:

---

