---
title: "Issue with mounting network drive regarding file permssions (ubuntu server 16.04)"
date: 2018-12-06
forum: Networking &amp; Wireless
---

### Post by Caleb_Christian on 2018-12-06
Hey,

I am fairly new to the syntax of Ubuntu Server (I currently have a 16.04 build running an instance of QuickBox Community). This VM is running on a esxi deployment in my house which has local access to another server running freeNAS with and NFS share I'm using for storage. I was able to mount the drive using cifs and assigning it to a directory (/networkStorage) in my user directory but after the mount I am only able to write to the directory when proceeding any command with sudo. I'm wanting to have software freely read/write from this directory so I know I have to change permissions. I attempted chmod -R 777 and chown myusername: directory to change directory permissions which dont result in an error but still fail to update directory permissions. Any help getting this directory writeable would be GREATLY appreciated as my experience with ubuntu thus far has been amazing. 

Thanks for any help guys!

-Caleb

---

### Post by Morbius1 on 2018-12-06
> I was able to mount the drive using cifs and assigning it to a directory  (/networkStorage) in my user directory but after the mount I am only  able to write to the directory when proceeding any command with sudo.  I'm wanting to have software freely read/write from this directory so I  know I have to change permissions. I attempted chmod -R 777 and chown  myusername: directory to change directory permissions which dont result  in an error but still fail to update directory permissions.
Please post your cifs mount expression so we can see how it is set up.

---

