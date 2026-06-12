---
title: "can't access ubuntu from windows PC's"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by giltheissen on 2009-01-23
brand new to ubuntu (5 days). Everything's gone smoothly, except for one thing. On my home network, none of my Windows Pcs can access the ubuntu PC. I can see and access all the Windows shares from ubuntu, but when I look for the ubuntu PC from either Vista or XP PC's, I can see it, but it asks for my user name and password, but never accepts the ubuntu username or password I've picked (none of my Windows PC's have any passwords and the single username for all PC's, including ubuntu is the same). No other problems with the network than that. Don't know whether this is a windows problem or an ubuntu problem, but any suggestions would be appreciated.
   Thanks - Gil Theissen

---

### Post by mjheagle8 on 2009-01-23
[http://librenix.com/?inode=10453](http://librenix.com/?inode=10453)
this link should help.

---

### Post by giltheissen on 2009-01-23
Thanks for the link. Samba is already installed, but when I try the next step, i.e.type in the next command:  /ect/samba/smb.conf  I get "permission denied". 
  Also tried the alternate method suggested in the article using the GUi with:  sudo apt-get install swat netkit-inetd tcpd and got "couldn't find package netkit-inetd"
   So I'm stuck again.

          Gil Theissen

---

### Post by mjheagle8 on 2009-01-23
use sudo when the permission is denied.
try searching in synaptic for the package.

---

### Post by giltheissen on 2009-01-23
netkit in synaptic only returned netkit-ping ( a transitional ping utility)  which doesn't look like what the author is referring to. And sudo in front of /ect/samba/smb.conf simply gives me "command not found".
    Gil Theissen

---

### Post by achase79 on 2009-01-23
netkit-inetd is in the inetutils-inetd package.
you need to edit your samba.conf file in a file editor.
```
sudo gedit /ect/samba/smb.conf
```

---

### Post by achase79 on 2009-01-23
you may also want to get gsambad.  It allows you to edit your samba.conf file graphically.
```
sudo apt-get install gsambad
```

or in Intrepid there is the gadmin-samba package
```
sudo apt-get install gadmin-samba
```

---

### Post by mjheagle8 on 2009-01-23
you all realize its /etc not /ect right?

---

