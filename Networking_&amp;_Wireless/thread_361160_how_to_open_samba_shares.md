---
title: "how to open samba shares"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by jeisma on 2007-02-14
hi!

from xubuntu 6.10, i need to open a samba share from another pc.

how to do that?

Thunar File Manager i tried to go to the location smb://192.168.0.10 but it won't allow it.

any ideas?


thanks!

joey

---

### Post by scxtt on 2007-02-14
can't remember exactly how thunar handles "smb://", but at the very least you'll need to specify the name of the samba share, so:

smb://192.168.0.10/**<name of share>**
ex.: smb://192.168.0.10/jeisma_home

would have a better chance ...

a good way to test it out would be via a terminal:

smbget smb://192.168.0.10/jeisma_home/<some file>

and see if you can get the file that way ... note, you'll need to have created smbpasswd for a user ...

---

### Post by jeisma on 2007-02-14
hello!

thanks for the response, but i already did that.

i can open the samba share from a windows. however, i don't know how to do it from a linux desktop.


thanks!

joey

---

### Post by scxtt on 2007-02-14
just cause it works in windows doesn't really mean anything - and you'll get more "browsability" in windows, so something like **smb://192.168.0.10** is more likely to work ...

did you do the smbget test?  do you know the name of the samba share in windows (more than just the ip address)?

i was able to get a file called "test.txt" from a windows 2003 server samba share from my own desktop:

shared **c:\document and settings\scxtt\desktop** as *scxtt_server_desktop* {had to use admin. account to do this}

**<linux prompt>#:** smbget smb://192.168.1.103/scxtt_server_desktop/test.txt
* asks for a username *
* asks for a password *
* tells me what workgroup is being used *
** gets the file **

also had to make sure the windows firewall would allow this ...

---

### Post by g8m on 2007-02-14
In a terminal i use the smbmount/smbumount commands to mount the shares.
You might have to install the smbfs package (sudo apt-get install smbfs).

To be able to do that as a normal user the smbmnt command must be installed suid root.
   sudo chmod +s /usr/bin/smbmnt

Then create a mountpoint.

  smbmount //servers/share mountpoint

If everything is normal it will popup a password.

With a different user
  smbmount //server/share mountpoint -o user=user

To be able to use the smb:// location, maybe you must add the user to the 
samba password file with sudo smbpasswd -a <user>

---

### Post by greyspoke on 2007-02-14
Have you got smbclient installed jeisma?  It doesn't get installed when you install Samba (you get both as standard when you install Ubuntu, but not Xubuntu).  

I can't get Thunar to find and mount newtork shares, unlike Nautilus can and K-whatever probably can as well.  You can use the mount command (if you have smbclient).  Loads of stuff about mounting network shares on [this thread]("http://www.ubuntuforums.org/showthread.php?t=288534&page=20&highlight=network+share").

As you can see - I've just been through this myself and have got Ubuntu, Xubuntu and WinXP to speak nicely to each other and a network printer.  Due mainly to these forums - thanks peeps!

---

### Post by jeisma on 2007-02-14
hi!

i have installed the software as you mentioned but, i still can't get to mount the samba share from xubuntu 6.10 desktop.

sudo mount -t smbfs -o username=jeisma,password=mypass //192.168.0.106/homes /home/jeisma/Desktop/smb/
or
sudo mount -t smbfs -o username=jeisma,password=mypass //192.168.0.106/home/share /home/jeisma/Desktop/smb/

401: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

the samba server has this in the smb.conf file:

[homes]
browseable = no
writeable = yes
path = /home/share

/share is 777 as well as the mount point /smb 777

what am i missing?


thanks!

jeisma

---

