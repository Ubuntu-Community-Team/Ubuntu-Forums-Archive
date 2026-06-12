---
title: "XP to Ubuntu Ibex network problem"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by workaholic on 2009-02-11
Hello.

I have Ibex on a dell machine using it as a home file server.
Samba is installed and running.  smb.conf file is very basic.
I am trying to share two external HDs on the Ubuntu machine with a laptop (Toshiba running XP Media) using a very simple configuration.

From the Ubuntu machine I can see and access all the shared files on the XP laptop.. no problem.
The problem comes up when I try to access the shared folders on Ubuntu from the XP laptop.  
In XP, I can see the Ubuntu shared folders in "my network places."
When I double click on the folder I get an error message saying that the path could not be found and that I might not have permission, to ask the server administrator...

sometimes, when I double click on the ubuntu Shares from XP, it gives me the option to give my username and PW, I type in the Ubuntu password, and still the same problem.


please help.

Thank you.****

---

### Post by taseedorf on 2009-02-13
this site may help you

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

try adding this to your samba configuration

usershare owner only = False

add the line under the global section

try this command

sudo gedit /etc/samba/smb.conf

---

### Post by workaholic on 2009-02-13
> **taseedorf said:**
> this site may help you

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

try adding this to your samba configuration

usershare owner only = False

add the line under the global section

try this command

sudo gedit /etc/samba/smb.conf


I already had that line in the smb.conf  still not working.  Could it be something to do with the mount or could it be on the XP side?

---

### Post by taseedorf on 2009-02-27
sounds like a problem with xp.

try allowing everyone to access the share, to check which side the problem is on.

you may need some pam smb stuff for password authentication, not sure...ive always had hit and miss with samba and linux

---

### Post by thelamer on 2009-02-27
```
sudo nautilus
```

Then navigate to the folders you want to share: 

in your case the USB drives will be located in /media (click on file system on the left) 

Right click on them and click sharing options. 

Check "share this folder" and optionally "allow other people to write in this folder". 

Guest access has never worked for me (leave it unchecked) you will have to use your username and password to login. 

Additionally if you want the drives writable over the network you will need to Chmod the folders to 777. 

```
sudo chmod 777 -R /media/path to your drive/
```

Hope this works ):P

---

### Post by Mark Phelps on 2009-02-27
You said your file server was running Ibex.  So, are the files you're trying to share on an Ext3 partition? Or did you create FAT32 or NTFS partitions for your shared files?  If the former, you're going to have to install an app in XP to be able to read Ext3 files.

---

