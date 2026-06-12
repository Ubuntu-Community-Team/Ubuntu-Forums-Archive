---
title: "Remote Desktop"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by aliasghar1451 on 2010-03-22
I m using rdesktop to open a windows pc on my ubuntu pc i have used this command to open it 
```
rdesktop -f -n -u username -p password xxx.xxx.x.x
```
now i want share my ubuntu files with to what must i add to this command to do so. plz can anyone help

---

### Post by Kenny_Larsen on 2010-03-22
Hi,

Try something like:

```
rdesktop -f -n -u username -p password -r 'disk:linux=/home/user/' xxx.xxx.x.x
```

obviously changing the folder you want to access.

Kenny

---

### Post by 3rdalbum on 2010-03-22
> **aliasghar1451 said:**
> I m using rdesktop to open a windows pc on my ubuntu pc i have used this command to open it 
```
rdesktop -f -n -u username -p password xxx.xxx.x.x
```
now i want share my ubuntu files with to what must i add to this command to do so. plz can anyone help

Remote Desktop is not for file sharing, only for access to the screen of another computer.

To transfer files from Windows to Linux, you should install the 'system-config-samba' package (Karmic and earlier) to install and configure a Samba server which will allow the Windows computer to access a shared folder.

You can use this package on Lucid too, but Lucid already contains a "personal file sharing" program that should be able to set up Samba for you too.

---

### Post by Kenny_Larsen on 2010-03-22
Although a Samba is a generally better way of sharing files, sometimes when working on another machine it is useful to be able to access the odd file here and there, in which case just using rdesktop tends to be fine.

---

### Post by quinnten83 on 2010-03-22
> **Kenny_Larsen said:**
> Although a Samba is a generally better way of sharing files, sometimes when working on another machine it is useful to be able to access the odd file here and there, in which case just using rdesktop tends to be fine.

+1
remember there is a gui for this under applications>Internet>Terminal Server Client. looks just like the one in Windows and works just as well.

---

