---
title: "Transfer File WinXP to Ubuntu 6.06 Server"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by textguru on 2006-10-02
I have two computers, one Windows XP Prof and one Ubuntu Server 6.06. My primary desktop is Windows. There are times that I need to copy some files to the Ubuntu Server. Is there a way that I can copy files from Windows to Ubuntu without using ftp? I have tried installing ftp but my proftpd doesn't work. Hope you could help me on this.

---

### Post by billir on 2006-10-02
If you have Gnome running on the "server" then go to Places => network servers => Windows Network (right hand pane)
Pick your xp computer from the list. Pick the share folder with the files you have previously put there.

If you do not have a gui you can setup Samba (download it using yum) on the ubuntu box and set it up having a SMB or windows share.

---

### Post by enetic on 2007-08-15
thank you. this is just what I needed billir!

---

### Post by ryry0666 on 2007-08-15
First, on your Windows machine, create a shared folder, or share the folder that contains the files you need shared.  NOTE: You will not be able to share a folder within your "Documents and Settings" folder if EFS is enable.d

On your Ubuntu machine, you will need to install Samba which can be done with the following code:
```
sudo apt-get install samba
sudo apt-get install smbfs
```

The shares may then be mounted with the following command.  It will be mounted in a folder called share in your home directory.

```
mkdir ~/share
mount -t smbfs -o username"Username on Windows Machine" //ip.of.windows/sharename ~/share
```

---

