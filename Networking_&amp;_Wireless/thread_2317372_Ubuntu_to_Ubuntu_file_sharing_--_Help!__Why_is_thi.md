---
title: "Ubuntu to Ubuntu file sharing -- Help!  Why is this so frustrating?!"
date: 2016-03-16
forum: Networking &amp; Wireless
---

### Post by Mr._Hope__Change on 2016-03-16
[LIST]
[*]Laptop 1 has Ubuntu 14.04
[*]Laptop 2 has Lubuntu 14.04
[/LIST]

All I want is the ability for file sharing between these two computers. Laptop 2 in particular has all my music, documents, etc that I want to access from Laptop 1.  Any help would be appreciated!

---

### Post by Petre_Cristian_Cre on 2016-03-16
A small search and the answer is right here -> [http://askubuntu.com/questions/310180/how-to-share-files-through-the-local-network](http://askubuntu.com/questions/310180/how-to-share-files-through-the-local-network)

---

### Post by Bucky Ball on 2016-03-16
> **Petre_Cristian_Cre said:**
> A small search and the answer is right here -> [http://askubuntu.com/questions/310180/how-to-share-files-through-the-local-network](http://askubuntu.com/questions/310180/how-to-share-files-through-the-local-network)

That's one way, but yes, it pays to search prior to posting. There are many ways to do this and if you are sharing Ubuntu to Ubuntu you don't need Samba. I use Filezilla myself. It's in the repositories. 

Another and really easy way is to install Gigolo mount the partition on the other machine on your local machine. It creates an icon as if the partition was internal on the machine you're working on. Also in the repositories.

Filesharing with either of the above methods is best done with static IP addresses on each machine (so you don't need to look up new ones everytime you want to connect).

If you need help with either of the above methods, sing out.

---

### Post by Morbius1 on 2016-03-16
The problem with Lubuntu is the number of things that are not installed by default.

On Lubuntu:

[1] Install avahi:
```
sudo apt-get install avahi-daemon
```
[2] Make sure it's running:
```
sudo service avahi-daemon restart
```
[3] Install SSH:
```
sudo apt-get install ssh
```
[4] Create an avahi ssh service file:
```
gksu leafpad /etc/avahi/services/ssh.service
```
[5] Then add this content - the first line cannot have any leading spaces:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SSH</name>
   <service>
       <type>_sftp-ssh._tcp</type>
       <port>22</port>
   </service>
</service-group>
```

On ubuntu open Nautilus, go to Browse Network and you should see something that looks like this:
> *lubuntu-host-name* SSH

If you want to go the Samba route the file manager cannot create shares like you can in Ubuntu but you can install a package that will do that:
```
sudo apt-get install system-config-samba
```
It should bring in all the samba related dependencies.

Since you already have avahi enabled you can create a Samba service file as well:

[1] Create the file:
```
gksu leafpad /etc/avahi/services/samba.service
```
[2] Add this content:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```

Browse Network on Ubuntu should show something like this:
```
*lubuntu-host-name *SMB
```
Samba discovery done the Linux/OSX way for those that have been told and truly believe that samba is just for windows.

---

### Post by kurt18947 on 2016-03-16
Home routers these days often come with USB ports. I've plugged external hard drives & flash drives into that port to make available stored content I may want to access from multiple machines. Powered USB hubs make multiple USB devices available. Not only can I access data from any machine, there is a backup function as well. It's sort of a NAS-lite.

---

