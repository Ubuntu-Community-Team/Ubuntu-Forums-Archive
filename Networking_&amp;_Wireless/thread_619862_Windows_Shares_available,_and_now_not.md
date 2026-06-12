---
title: "Windows Shares available, and now not?"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by mikeycantoon on 2007-11-21
When I first installed Ubuntu 7.10 and got my network connections up.  I could goto network-Windows Network-and see all my 3 XP machine drive shares, connect to them, and copy files from them.  Couple days later, I can still see Windows Shares, but clicking on it, it times out.  How could I see them before but now not?  My network configuration hasn't changed at all.

-Mikey

---

### Post by mikeycantoon on 2007-11-22
Is it Samba that I need to configure in order to see my Windows shares again.  Because I didn't install Samba until after I could already access my windows shares.  I still don't understand how I could see them and access them before I installed Samba and then not after?

-Mikey

---

### Post by kevinatkins on 2007-11-22
Hi,

OK, Samba comes in two parts - the Samba client and Samba server. A default install of Ubuntu includes the Samba client, which allows you to browse and connect to Windows shares. However, if you want to share resources on your Ubuntu machine over a Windows network, then you need to install and configure Samba server. I'm guessing that you've installed the server component and now network browsing has gone haywire...

In truth, configuring Samba server can be a bit tricky.. I'm quite a seasoned Linux user and I still sometimes find it irksome! You could try uninstalling the Samba server and see if network browsing then works again...

Alternatively, one quick change you can make is to ensure that the server is configured to be part of the workgroup in which your windows machines reside. To do this, you need to edit /etc/samba/smb.conf (sudo gedit /etc/samba/smb.conf) and change the workgroup to whatever you've named your windows workgroup. Then you need to restart the samba server for the changes to take effect (sudo /etc/init.d/samba restart).

Hope this helps anyway.

Kevin.

---

### Post by mikeycantoon on 2007-11-22
Thanks Kevin, I'll try that and post back my results.  Wish me luck!

-Mikey

---

### Post by LarryJ2 on 2007-11-23
On my version of Kubuntu Gutsy 7.10 with the following  Adept Manager "smb" packages showing as being installed : libsmbclient, lineightborhood, smbclient, and smbfs

I can see my networked windows  shares available from other windows pcs on my local network by entering the following in konqueror

smb://myNetworkPC/sharedFolderName

where myNetworkPC  is the name of the windows PC and sharedFolderName is the folder on the windows pc you are sharing.  Stated another way this is the name of the folder you designated to be shared while at your networked windows PC.

If you want to see a list of the windows/linux pcs that are sharing samba (aka windows) shared folders, try  smb://myNetwork  

where myNetwork is the  Workgroup name you entered on your windows and linux pcs.  The default on windows PCs is , I recall,  MYHOME.  This name seems to be case sensitive.  MYHOME is different than myhome.

Note that I do not use logins and passwords for my windows/samba shared folders. I'm behind a NAT router and my WAF (wife acceptance factor) doesn't allow that.

Also theres a package  smb4k that you can install using Adept Manager that seems to work in kubtuntu.   It's an smb/samba share network browser somewhat similar to windows network neighborhood.

You would think that to restart  samba/smb, in KDE Kubuntu Gutsy you could go:
Kmenu->SystemSettings->Advanced->SystemServices  click Administrator Mode  then find the smb daemon and click restart but it doesn't seem to be there!   I don't know what debian/ubuntu calls this service.   Maybe someone else can help.  

Hope this helps someone.

---

