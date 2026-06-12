---
title: "access shared files"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by irshan on 2008-05-28
dear friends 

i installed samba and working properly. when i shared data or any files it can access other machines but i cant access the shared files in my ubuntu so pls give good guidelines how to enable and access files.

---

### Post by superprash2003 on 2008-05-28
go to Places->Computer and in location type smb://(ip address of machine) to connect to the machine and access its files

---

### Post by irshan on 2008-05-28
im not given ip address.is there anyway to view all work group machines in network, such as what we do in windows.In network place when click view work group it show all machines in network which is relevent to workgroup then we can access data or files from the machines we want.

---

### Post by kevn3k on 2008-05-28
I'm afraid I can't help on the issue, but I would like to add a question... is it possible to do the reverse? eg: have a windows computer access the linux files, or at least just a specific folder? My laptop is an old machine running Xubuntu and it doesn't have USB 2.0 so external drives are a pain when I need to transfer files around.

---

### Post by superprash2003 on 2008-05-28
@irshan - try places->Network

@kevn3k
  for this you first need to install samba in the linux machine and from the windows machine in windows explorer type \\pcname where pcname is the name or ip of the linux machine.. to setup samba read this [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by irshan on 2008-05-29
Dear Friend,

follow the following link then u will get to know 

[http://prash-babu.blogspot.com/2008/...-in-linux.html](http://prash-babu.blogspot.com/2008/...-in-linux.html)

---

