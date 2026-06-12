---
title: "Linux and Windows combined network, help with Samba"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by Nir Friedman on 2008-08-16
I run Linux, and the rest of my family is running Windows. I wanted to be able to have it set up on a network so that we could see and modify each other's files (at least in some directories). This is already set up amongst my family members computers which all run Windows. We have a wireless router at home which connects all the computers to the internet as well as to each other (my computer is already using the wireless router for internet, so its connected). So I did some searching around, found out about Samba and started messing around with the Samba config file. I didn't make too many changes, all I really did was change workgroup = FRIEDMAN (the correct name of the workgroup). Then I started playing with the shares section, uncommenting lines mostly. I have the following lines under share definitions uncommented (i.e. no semi colon in front).

[homes]
browseable = yes
read only = yes
create mask = 0700
directory mask = 0700

and that's it. I don't want to have any user restrictions or passwords or anything like that for people on the windows end, so I didn't deal with user accounts or passwords and such. After doing this, I (to my glee) was able to see my whole family (all their computers, that is) and have proper access through konqueror and typing smb:/friedman. However they still can't see me at all. I don't know if this is at my end, or their end (Windows network neighbourhood is black magic after all). Any suggestions?

Also on a related note: I tried to go to the sharing tabs on a random directory (when I right click and go to properties) and it tells me that I need to have SMB and NFS servers installed to do this. Which packages do these correspond to? Will they make my life easier? I would much prefer to share specific folders simply by right clicking and indicating share then by editing the config file a zillion times (yes, I'm a recently converted Windows user who likes his GUI...) so if this allows me to do it, by all means. I basically would like to get integrated with Windows networks through the path of least resistance, regardless of whether its GUI or config file. Many thanks for anyone who takes the time.

PS I am running Kubuntu as the prefix indicates but I'm not sure what system information beyond that is relevant; to be honest if its something detailed I'm not sure that I know it. However given that I can see other computers already on the network, I feel like the connection is there I just have to change more settings to enable, so hopefully the details of the router or my hardware aren't relevant.

---

### Post by Iowan on 2008-08-16
Although you have a **smb.conf** file, you may not have the Samba-server suite installed - required to share files TO Windows systems.  The (pre-installed) Samba-client appears to be working well.  [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/search.php?searchid=46430999]("http://ubuntuforums.org/search.php?searchid=46430999")
[http://ubuntuforums.org/search.php?searchid=46430999]("http://ubuntuforums.org/search.php?searchid=46430999")

A few links to check.

---

