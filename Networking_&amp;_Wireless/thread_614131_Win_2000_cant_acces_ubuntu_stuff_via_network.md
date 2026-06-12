---
title: "Win 2000 cant acces ubuntu stuff via network"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by dummyhead3 on 2007-11-15
Greetings!

I have a small problem... I have two computers at my house: one AMD athlon 64 dual-booting Gusty and Windows Vista; and a Celeron 3 dual-booting Windows Me and 2000; a router is connected to the athlon, and the other one is connected via wireless. Both PCs see each other (and themseleves), I can acces the win2000 from ubuntu but not vice-vers, It asks me for a password and a username that I do not know. how can I get the Windows 2000 to acces ubuntu stuff???

Thanks!

PS: Sorry if this could / should go to the beginner talk category.

---

### Post by Triptol on 2007-11-15
Should be very easy. First install Samba (if you haven't already 'aptitude install samba' will do the trick).

Now edit the /etc/samba/smb.conf file and make sure the directories you want to share are shared. Some examples are already included almost at the end of the file.

Then restart samba (/etc/init.d/samba restart).

Last but not least create a windows password for your current user:
```
sudo smbpasswd -a [your_linux_username]
```

If you now connect from windows, it will ask for a password (unless your linux username and the password you just entered match the windows username and password), which you will now have.

---

### Post by dummyhead3 on 2007-11-17
Thanks! 
I thought that samba was installed but it was not the case!

---

