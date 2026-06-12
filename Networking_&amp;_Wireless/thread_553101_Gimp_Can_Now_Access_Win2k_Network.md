---
title: "Gimp Can Now Access Win2k Network"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by measekite on 2007-09-17
Gimp, Scribus and other programs that do not use gnome-vfs to access network drives can be made to do this by mounting those drives in /media.

My system is Feisty as a client and Win2K Advanced server formatted for NTFS.

The answer, as given to me by others on this forum is in the Unofficial Guide to Ubuntu 7.04 and I thank you for it.  Here is the link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking)

Follow the instructions in the HowTo:

[COLOR=Red]**  How to mount network folders on boot-up, and allow all users to read/write**[/COLOR]

    * Read #General Notes
    * Read #How to install Samba Server for files/folders sharing service 

    * In this example: 

    Network computer's IP: 192.168.0.2 
    Network computer's Username: myusername 
    Network computer's Password: mypassword 
    Shared folder's name: linux 
    Local mount folder: /media/sharename 

[B] sudo mkdir /media/sharename
gksudo gedit /root/.smbcredentials  

[COLOR=Red]notice the period after /root/[/COLOR]
[/B] 
    * Insert the following lines into the new file: 

username=myusername
password=mypassword

    * Change the rpivileges of the .smbcredentials file: 
[B]
sudo chmod 700 /root/.smbcredentials[/B]

    * Make a backup copy and then edit the fstab file (which has the mounting options): 

[B] sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab[/B]

    * Append the following line at the end of file: 

** //192.168.0.2/linux    /media/sharename smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0**

Now either reboot or do a

**sudo mount -a**

You may have one problem if you used spaces in the share names on your Window Server when you originally shared the folder or drives.  If so you need to log on to your server and change the share name to something without spaces.

In my case I had Public Vol 1 and the above instructions did not work until I changed that to public_vol1.  Using quotes around it helped with the mount command but not when inside the fstab file.

It is unfortunate that one has to do such low level and obscure things when compared to the more sophisticated Windows but the OS engine of Linux (Ubuntu) appears far superior and that once Ubuntu matures and gets good device support from the hardware mfg then Windows is going to have to make big changes if they do not want to loose market share.

---

