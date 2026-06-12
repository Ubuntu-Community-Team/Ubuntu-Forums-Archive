---
title: "Where is samba in ubuntu??"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by visualfox on 2006-09-16
i want to connect a winxp pc with ubuntu pc in a network.
how i can connect these pcs?where is samba and what i must to do?
Thanks!

---

### Post by meng on 2006-09-16
Here's a starting point.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by JayTee on 2006-09-16
I'm still a newbie at this but I'll give it a shot. As I understand it Samba installs by default with Ubuntu 6.06 to access SMB/CIFS resources like Windows XP shares. If you want to share your Ubuntu volumes with Windows you'll need to go into Add/Remove from the applications menu and click on Advanced. In the left pane of the window click Networking (you may see Networking (Universe) as well depending on your sources options but don't use that) and scroll down in the list on the right. You'll see two choices samba-common and samba. samba common should have a green box to the left of the name indicating it's already installed and samba will not. If you want to share your linux system with a windows system check the samba box and apply the change.
To access Windows shares from Ubuntu go to the Places menu and choose Network Servers. The Network file browser will find your Windows network and show an icon in the right pane. Double click to drill down in it till you find your Windos XP computer and double click that. It should show any available shared folders you've setup. NOTE: If you can read the share but not write to it you will need to modify your share permissions in Windows to allow Everyone Write access. Windows XP shares are set to Everyone Read by default. If you want to mount a Windows XP share or volume there are several good how-tos on this forum. Best of luck!

---

