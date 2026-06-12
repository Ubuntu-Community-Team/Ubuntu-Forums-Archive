---
title: "Conecting a computer with ubunto to another one with Windows XP"
date: 2017-01-17
forum: Networking &amp; Wireless
---

### Post by jorge2017 on 2017-01-17
[COLOR=#333333][FONT=Ubuntu]Hello. First of all, I'm new using linux. I'm using ubuntu 16.04 and what I need is to create a permanent link in /etc/fstab so that I can access a windows carpet from my ubuntu machine. The windows machine I am trying to connect to, has the ip address 192.168.0.13 and the shared carpet is called myprogram.. My ubuntu machine is in the same workgroup as the windows machine, and I can see them by accesing archives, network, windows network, mygroup. The sintaxis I used in fstab is: //192.168.1.13/myprogram/media/share cifs credentials=/home/myubuntu_user_name/.smbcredentials,iocharset=uft8,gid=GID,file_mode=0777,dir_mode=0777 0 0. I've also try replacing myubuntu_user_name, with the number 1000, as per the way I understood your instructions. I created the file .smbcredentials and wrote in it: username=myubuntu_user_name and password=myubuntu_password.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I think ubuntu is not recognizing the address 198.168.01.13. Another comment I want to make is that I cannot see the archive .smbcredentials in the carpet \home\myubuntu_user_name, I imagine is because of the period at the beginning, but I just want to know if this is the case.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Any tips?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Thank you[/FONT][/COLOR]

---

### Post by TheFu on 2017-01-18
Welcome to the forums.

not sure what "windows carpet" is - check your translation please.  Also, using "code tags" would help. Things will line up better.
 ```
//192.168.1.13/myprogram/media/share cifs credentials=/home/myubuntu_user_name/.smbcredentials,iocharset=uft8,gid=GID,file_mode=0 777,dir_mode=0777 0 0
```

I'd put the credentials in /etc/samba/ with root:root and 600 permissions.  The GID must be a valid number (probably 1000), from the /etc/group file.  File_mode should probably be 664 and dir_mode=0775.

The creds file needs real usernames and the real Windows login password. Something like```

username=thefu 
password=my-password-%$235-thefu
```

Be certain that the Linux machine can ping 198.168.01.13 (windows). If it cannot, none of this will work.

---

### Post by jorge2017 on 2017-01-18
Thank you Thefu for your kind reply. You`re absolutely right, I need to check my translation, in spanish is "carpeta" in Englis is "Folder" so I meant to say "Windows Folder". I will check your suggestion and let you know. Thanks

---

### Post by TheFu on 2017-01-18
> **jorge2017 said:**
> Thank you Thefu for your kind reply. You`re absolutely right, I need to check my translation, in spanish is "carpeta" in Englis is "Folder" so I meant to say "Windows Folder". I will check your suggestion and let you know. Thanks

No worries.  I've been struggling to learn Spanish for a long time - even did intensive training and other travel to help, but then returning home I lose most of that knowledge.

Can you ping?  
Did you put in the real groupid put in?
The credentials file format clear?

---

### Post by jorge2017 on 2017-01-18
Following your advide, I replace with line in /etc/fstab with the following:

```
 //192.168.0.13/myprogram/media/share cifs credentials=/etc/samba/smbcredentials,iocharset=uft8,gid=1000,file_mode=0 777,dir_mode=0777 0 0
```

(Sorry the address is 192.168.0.13 not 192.168.1.13). I ping to the address and the connections works well.
I deleted the file .smbcredentials, and created a new file /etc/samba/smbcredentials (as you see, I deleted the period at the beggining). 
In the new smbcredentials file I wrote:
username=my_windowsxp_username
password=my_windowsxp_userpassword
(before, I had written my ubuntu username and password)
I run sudo mount -a
But I still get the message
```
mount: mount point cifs does not exists
```
Any suggestions?
Tank you

---

### Post by TheFu on 2017-01-18
Ah .... you are missing an empty directory for the "mount" to attach.

I've fixed the fstab entry. There were a number of typos/swapped characters in the one posted here.
```
//192.168.0.13/myprogram/media/share  /windata cifs credentials=/etc/samba/smbcredentials,iocharset=utf8,gid=1000,file_mode=0664,dir_mode=0775 0 0
```

Then run 
```
sudo mkdir /windata
sudo mount -a

```

That should do it.

mounts are always {source} then {target} then file system type and options.  It is a common mistake. We all miss it from time to time.

---

### Post by jorge2017 on 2017-01-18
Thanks again, I've been looking for help all over, even in the spanish ubuntu forum, but no one had been able to help me so far. 
I am getting closer, the message I get now is
```
mount error(79): Can not access a needed shared library
```

---

### Post by jorge2017 on 2017-01-18
Never mind, I've missed one of the typos. it works GREAT. Thank you

---

