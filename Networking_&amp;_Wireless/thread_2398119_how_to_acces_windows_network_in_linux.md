---
title: "how to acces windows network in linux"
date: 2018-08-07
forum: Networking &amp; Wireless
---

### Post by dogan226 on 2018-08-07
hello i have installed xubuntu 18.04 and installed samba and the system-config-samba utillitie and can share files from the linux pc and see them as share on the windows machines in the windows network on the windows pc's
what i want is to open for example in nautilus the windows network to see at least the windows pc on the network but i cannot open the windows network on my xubuntu pc can anyone tel me what i am doing wrong or need to install to do this ??
i did also did an full update
kind regards bert

---

### Post by Morbius1 on 2018-08-08
This "fix" may create a paradox depending on what version of Windows you are using:

Edit /etc/samba/smb.conf and right under the workgroup = WORKGROUP line add the following:
```
client max protocol = NT1
```
Then restart smbd:
```
sudo service smbd restart
```
The paradox involves Windows 10 or any server that has disabled SMB1. Samba calls SMB1 NT1 so if that is the highest level it can attain and your Win10 box disabled SMB1 you will be able to "see" it under Windows Network but will not be able to connect to it.

---

### Post by dogan226 on 2018-08-09
thanks i will try it out thanks for the support :-)

---

### Post by dogan226 on 2018-08-10
hello i tried adding this line nnow i can open windows network in nautilus but i still cannot see any windows pc in that network let alone the share ( i am a lazy guy i think maybe to much in windows ideas but i want to see in the windows network on nautilus the windows pc&#347; and there shares so i can easely logon ) and nod have to type lines like smb:\\192.168.1.106\sharedfolder
aspecialy for my wife :-)

---

### Post by Morbius1 on 2018-08-10
2 options:

[1] Edit smb.conf again and add this line under the workgroup = WORKGROUP line:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba in this order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```
Now wait about 5 minutes or so. nmbd is a primitive process and it takes time to reset the local network.

[2] Give all of your machines static ip addresses. Then you will only have to do smb://192.168.1.106/sharedfolder once then bookmark it. Or if you have a lot of shares per machine create a bookmark to just smb://192.168.1.106

---

