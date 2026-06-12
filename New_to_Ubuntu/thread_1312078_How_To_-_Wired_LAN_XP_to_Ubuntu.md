---
title: "How To - Wired LAN XP to Ubuntu"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by bitec on 2009-11-02
Greetings

Alas I am new to UB and am unable to LAN my Ub V9.1 latop to my XPSP2 PC using a WIRED connection. Is there a step by step guide in the forums somewhere as I can't find it? All I want to do is transfer about 40GB of data from my XP PC to my Ub latop, am not worries about internet connection and want to use a ALN cable as it is quicker than wireless.    Thanks

---

### Post by Locke_99GS on 2009-11-02
In windows, I don't recall how to set up a share. In Ubuntu, right-click on the folder you wish to share, select the option "Sharing Options", and check to share the folder. It will prompt you to install samba if you don't have it already. I believe the procedure is similar on Windows.

After you set a share in Windows, in Ubuntu, from the menu do Places->Network and file the shared folder in therr -OR- enter the shared Ubuntu folder (if you set one up) from Windows, and move the data this way.

Another option could be to copy the data over SSH (putty in windows?)

---

### Post by NickJones on 2009-11-02
Go to terminal
> sudo apt-get install samba
sudo gedit /etc/samba/smb.conf
This will then pop up the config file, have a look at mine for an idea as to how to do it. Nameley the bottom bit, you can enable sharing by only changing > [SAMBAshare]
        comment = NAS_on_NickLappie
        path = /home/nick/public
        read only = No
        guest ok = Yes

Change the "path = /home/nick/public" to replace nick with whatever your username is. You must also set the permission for the public folder, go into your home folder, right click on public, go properties,  permitions, and under others set it to  "Folder Access: Create and delete" and "File Access: Read & Write"

Alternately download HFS and install it on your Windows machine, it's great for transferring a few large files, but not huge amounts of them unless you want to zip them all up. It's very simple to use if you do zip it up.

---

