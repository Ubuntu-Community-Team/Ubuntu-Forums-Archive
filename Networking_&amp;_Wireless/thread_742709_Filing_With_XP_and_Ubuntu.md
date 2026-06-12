---
title: "Filing With XP and Ubuntu"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by JayDeePlus on 2008-04-02
i have 3 computer and a router..........i have setup router and setup 2 XP machines to file share.........that is working right..........try to do it with ubuntu machine.........it's able to see the main xp machine through network place on ubuntu machine......but when i click on the machine it gives me an error " The Folder Contents Could Not Be displayed" is there some plugin or package i need to install to be able to speak to a windows machine?

---

### Post by warp99 on 2008-04-02
You need to use Samba in order to see the files on the XP machines:

[https://help.ubuntu.com/7.10/internet/C/networking-shares.html#networking-shares-windows](https://help.ubuntu.com/7.10/internet/C/networking-shares.html#networking-shares-windows)

Please see my signature for more helpful tips.

---

### Post by superprash2003 on 2008-04-02
after installing.. to connect type smb://192.168.1.10 where 192.168.1.10 is the ip of the windows machine

---

### Post by Iowan on 2008-04-02
Try the Network Places>Connect to Server option - I've had better luck that way - although last time it didn't seem to make much difference.   I've also had my first attempt to connect fail, then the next succeed.  
Another possible problem is the Windows Firewall.

---

### Post by Eiríkr on 2008-04-03
@warp99, JayDeePlus --

You only need the full Samba package if you are sharing files *from* an Ubuntu machine.  If you're on an Ubuntu machine and want to access files that are on an XP machine, you don't need the full Samba package.  :)  All you should need are the smbclient and smbfs packages (which might come installed by default).  I've read before that XP has certain bugs related to hostname resolution via SMB that can prevent browsing via the Network -> Workgroup route in Nautilus or Konqueror, and that's probably what you've run into.  Try superprash2003's and Iowan's suggestions, and see if that works.

Cheers,

Eiríkr

---

