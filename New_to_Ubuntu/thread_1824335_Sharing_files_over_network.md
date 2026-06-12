---
title: "Sharing files over network"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by bigao on 2011-08-13
I'm  new to this all I have used is windows.  I have ubuntu 11.04 on a notebook I connect wireless to my desktop with windows XP, with a cable modem and a router that is wireless.  I installed SMBK4 on the notebook and the desktop shows up but if I click on a folder it gives me error           p, li { white-space: pre-wrap; }  

mount.cifs: permission denied: no match for /home/tony/smb4k/BIGAO-199B2MBA3/My Pictures found in /etc/fstab


The desktop is set to share files over the network, also I can print with no problem to the printer on the desktop.  Any help will help.


Thanks:p

---

### Post by Morbius1 on 2011-08-13
Smb4K is a KDE appliction so I'm not sure if you are running Kubuntu or Ubuntu with a KDE application.

If you are running Ubuntu then what happens when you run:
```
nautilus  smb://"BIGAO-199B2MBA3/My Pictures"
```

---

### Post by bigao on 2011-08-13
I run the code then I can access the desktop pictures.

---

### Post by cogier on 2011-08-13
Which desktop is set to share files over the network - Windows or Ubuntu?

---

### Post by bigao on 2011-08-13
windows

---

### Post by Morbius1 on 2011-08-13
Then don't run Smb4K.

Open up Nautilus ( your Home folder ) > Select "Network" > "Windows Network" > "BIGAO-199B2MBA3" > My Pictures.

If you want you can then select Boolmarks > Add Bookmark. Then it will show up on the left side panel of Nautilus sort of like a "mapped drive" does on WinXP.

---

### Post by bigao on 2011-08-13
Thanks I'll do that

---

### Post by cogier on 2011-08-13
What you need to do is select the folder in Ubuntu that you want to "Share" and Right Click on it and select "Sharing Options".

You will be presented with various options. Select your requirements - You will then be told that you need to download the necessary software.

Allow this to happen, reboot the computer, go back and AGAIN select the folder you want to share and this time the options will work.

---

### Post by bigao on 2011-08-13
I did that it comes up with this

Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist

---

### Post by Morbius1 on 2011-08-13
Just to be clear, the instructions cogier gave you is for sharing a folder on your Linux box for others ( i.e., WinXP ) to access. It has nothing to do with accessing someone else's shares from Linux.

Anyway, it looks like samba is either not installed or not running. Start it:
```
sudo service smbd start
```When you use the nautilus method to share a folder for the first time in Ubuntu it tells you need to reboot ( or maybe it's logoff and logon again ), did you do that?

---

