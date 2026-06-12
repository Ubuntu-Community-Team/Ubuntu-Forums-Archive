---
title: "smb and NFS servers are not installed on this machine"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by brainstuffch on 2008-08-04
BajaPaul says: 

sudo apt-get install samba smbfs

solve the problem. And this is right, only, on my system the hdd is shared, but it is still not visible... I see only the printers and a pdf printer. But not in the right Workgroup ...   

What can I do to have access to the hdd from the Windows network? 

The next problem is the "Workgroup" .. Where can I change the name of the workgroup? 

thank you for your help.
braisntuffch

---

### Post by McNils on 2008-08-04
Look in the file /etc/samba/smb.conf
There you can change workgroup and control what you share.
After editing the file as root, **sudo nano /etc/samba/smb.conf** restart samba, **sudo /etc/init.d/samba restart**

---

### Post by lacis_alfredo on 2008-12-13
Hi,
I had a similar problem, but when I tried ```
sudo apt-get install samba smbfs
``` I just got these errors:```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.7 is to be installed
  smbfs: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.7 is to be installed
E: Broken packages

```

---

### Post by bab1 on 2008-12-14
> I just got these errors:
Code:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.7 is to be installed [COLOR="Red"]<-- need to install first[/COLOR]
  smbfs: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.7 is to be installed
E: Broken packages



The smbfs package is only the client side suite of commands for the Samba server.  

If you want to share files you need to install Samba server.  From the command line:```
sudo apt-get install samba samba-common samba client
```

The error code shows that these need to be installed before you can install smbfs.

---

### Post by lacis_alfredo on 2008-12-19
Hi, thanks for that . . .```
$ **sudo bash**
[sudo] password for homer:
this is .bashrc
root@krusty2:~
# **apt-get install samba samba-common samba client** [COLOR="Red"]first try[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba-common is already the newest version.
E: Couldn't find package client
root@krusty2:~

``````
# **apt-get install samba samba-common samba-client** [COLOR="Red"]second try with hyphen[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba-common is already the newest version.
Package samba-client is a virtual package provided by:
  smbclient 3.0.28a-1ubuntu4.7
You should explicitly select one to install.
E: Package samba-client has no installation candidate
root@krusty2:~

``````
# **apt-get install samba samba-common smbclient** [COLOR="Red"]third try with suggested name[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba-common is already the newest version.
smbclient is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[B]The following packages have unmet dependencies: [COLOR="Red"]similar error as before[/COLOR]
  samba: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.7 is to be installed
E: Broken packages[/B]
root@krusty2:~

```Let's try some of the other posters' suggestions:```
# apt-get install samba-common [COLOR="Red"]let's just try samba-common[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@krusty2:~

``````
# apt-get install samba smbclient [COLOR="Red"]OK: try the other stuff[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
smbclient is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[B]The following packages have unmet dependencies: [COLOR="Red"]similar error as before[/COLOR]
  samba: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.7 is to be installed
E: Broken packages[/B]
root@krusty2:~
#
```**[COLOR="Magenta"]What's the difference between <blah>ubuntu 4 and <blah>ubuntu4.7?[/COLOR]**

---

