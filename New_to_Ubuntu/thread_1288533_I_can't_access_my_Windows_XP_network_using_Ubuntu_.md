---
title: "I can't access my Windows XP network using Ubuntu 9.04"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by davew78 on 2009-10-11
I just installed Ubuntu 9.04 and I can't access my Windows Network from the computer with Ubuntu on it. This computer only has Ubuntu on it.   I can access my shared folder on the Ubuntu computer from my Windows XP computer, as well as the other computers on my network. I was able to set up my network printer with no problem. Can someone please help?

---

### Post by benmoran on 2009-10-11
Perhaps Samba isn't installed. 

From a terminal:  sudo apt-get install samba
Or search for samba in Synaptic.

---

### Post by davew78 on 2009-10-11
Samba is installed.

---

### Post by houstonbofh on 2009-10-11
Long but very detailed post at [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) that may help.

---

### Post by tkelito on 2009-10-11
So after Samba is installed you can do this:

In terminal:

This create a backup of your fstab:
```
sudo cp /etc/fstab /etc/fstab.bak
```

This creates the place to mount your share:
```
sudo mkdir /home/USERNAME/Shares/NameOfShare
```

This opens your fstab to edit:
```
sudo gedit /etc/fstab
```

This is the line to add so your share gets mounted:
```
\\xxx.xxx.xxx.xxx\NameOfShare	/home/USERNAME/Shares/NameOfShare	cifs	username=defaults;password=defaults 0 0
```

This mounts your shares without a restart:
```
sudo mount -a
```

On Vista/XP you will have to either add the username of you Ubuntu install with the correct security permissions or you can add the user 'everyone'.  Though adding 'everyone' is not nearly as secure it is fine for a home network where you control the access.

---

### Post by davew78 on 2009-10-11
Thank you, it worked perfectly!!!

---

### Post by tkelito on 2009-10-11
> **davew78 said:**
> Thank you, it worked perfectly!!!

Wonderful, glad we could help this morning.

---

