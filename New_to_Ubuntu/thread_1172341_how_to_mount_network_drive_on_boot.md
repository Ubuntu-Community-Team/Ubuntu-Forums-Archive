---
title: "how to mount network drive on boot"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by corkscrew on 2009-05-28
I have moved from win xp to linux so far really happy except for network drives.

I have a network with laptop and 2 x desktops and 2 LAN drives (fat32).
Running Hardy 64 on 2 machines and xp on the other, all can see each other etc.

I can access the drives through nautilus ok, but i want these drives to mount automatically on boot so i can run automated backups to them. The drives also power down for energy saving.

I cant find a simple how to to do this just a bewildering amount of threads pertaining to sbmf and cif 

At least in windows the drives mount automatically I hate to think windows is superior in this field but to me it like the case at the moment.

---

### Post by Celauran on 2009-05-28
From [help.ubuntu.com](https://help.ubuntu.com/community/SettingUpSamba):

In order to have a share mounted automatically every time you reboot, you need to do the following:

With any editor, create a file containing your Windows/Samba user account details:

```
gksu gedit /etc/samba/user
```

KDE users must use kdesu rather than gksu and instead of Gedit they can use Kwrite as editor.

... it should contain two lines as follows:

```
username=samba_user
password=samba_user_password
```

Note: "samba_user" = the user name on the samba server (may be different from your log-in name on the client). "samba_user_password" is the password you assigned to the samba_user on the samba server.

Save the file and exit gedit.

Change the permissions on the file for security:

```
sudo chmod 0400 /etc/samba/user # permissions of 0400 = read only
```

Now create a directory where you want to mount your share (e.g. /media/samba_share):

```
sudo mkdir /media/samba_share
```

Now, using any editor, and add a line to /etc/fstab for your SMB share as follows:

```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```

Add a line for your SMB share:

```
//myserver_ip_address/myshare  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0
```

The share will mount automatically when you boot. The "noexec" option prevents executable scripts running from the SMB share.

---

### Post by corkscrew on 2009-05-28
> **Celauran said:**
> From [help.ubuntu.com](https://help.ubuntu.com/community/SettingUpSamba):

In order to have a share mounted automatically every time you reboot, you need to do the following:

With any editor, create a file containing your Windows/Samba user account details:

```
gksu gedit /etc/samba/user
```

KDE users must use kdesu rather than gksu and instead of Gedit they can use Kwrite as editor.

... it should contain two lines as follows:

```
username=samba_user
password=samba_user_password
```

Note: "samba_user" = the user name on the samba server (may be different from your log-in name on the client). "samba_user_password" is the password you assigned to the samba_user on the samba server.

Save the file and exit gedit.

Change the permissions on the file for security:

```
sudo chmod 0400 /etc/samba/user # permissions of 0400 = read only
```

Now create a directory where you want to mount your share (e.g. /media/samba_share):

```
sudo mkdir /media/samba_share
```

Now, using any editor, and add a line to /etc/fstab for your SMB share as follows:

```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```

Add a line for your SMB share:

```
//myserver_ip_address/myshare  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0
```

The share will mount automatically when you boot. The "noexec" option prevents executable scripts running from the SMB share.

hi thanks in advance, fell at the first hurdle though
```
cm@m3n78:~$ gksu edit /etc/samba/user
Warning: unknown mime-type for "/etc/samba/user" -- using "application/*"Error: no "edit" mailcap rules found for type "application/*"
lication/*"cm@m3n78:~$ 

```

---

### Post by Boondoklife on 2009-05-28
Im gonna go out on a limb but it maybe cause you typed gksu edit and not gksu gedit? ;)

---

### Post by corkscrew on 2009-05-29
> **maletek said:**
> Im gonna go out on a limb but it maybe cause you typed gksu edit and not gksu gedit? ;)

oops yes well spotted, ok got all done but the drive still wont mount here's the line i added to my fstab
```
//198.168.25.45/LAN-DISK1 /media/storage  cifs  credentials=/etc/samba/user,noexec  0 0
```

the actual folder i want to access is /lan-disk1/store1 should i put that in fstab

---

### Post by Boondoklife on 2009-05-29
try this```
//server/public /media/public cifs auto,user,credentials=/root/.credentials,iocharset=utf8,dir_mode=0666,file_mode=0777 0 0
```

---

### Post by woohhaa on 2009-05-29
I'm very new to ubuntu and this helped a ton. But when I followed the directions it didn't work. I found that I needed to install smbfs in order for this to work. 

Code:
sudo aptitude install smbfs

After that it worked just right. Thanks for the great advice!

---

### Post by Boondoklife on 2009-05-29
out of curiosity what version of ubuntu you runnin? I installed jaunty and dont remember having to install it, guess it came installed?

---

### Post by woohhaa on 2009-05-29
I am using jaunty 9.04. I went through the steps to the best of my ability then restarted with no automatic mount. I then spoke with a friend about this issue and he pointed me to the page below. After reading through it I tried the command I mentioned earlier and restarted again. This time it worked like a charm. Go figure.  

[https://help.ubuntu.com/community/SettingUpSamba#Client](https://help.ubuntu.com/community/SettingUpSamba#Client)

---

### Post by ericsp on 2009-07-12
got it all running with the help of this thread. however, when I open the drive, all folders are inaccessible. When type "smb://192.168.10.1/media/" in nautilus, I see all folders as folders. when i access the mounted drive via "/media/networkdrive/media" I see a sort of textfile icon with an orange block marked with a white cross (inaccessible). Any suggestion?

---

