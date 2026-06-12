---
title: "help with samba install"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by jhonijim on 2006-12-06
ive been trying to install samba i used the share folders to install, sanaptic, and the terminal but i get ```
Preconfiguring packages ...
Selecting previously deselected package libcompress-zlib-perl.
(Reading database ...

```

and it just sits there one atempt i let it sit for 20 hours with no change
i need help.

---

### Post by namich on 2006-12-07
From the command line try the following:

sudo apt-get install samba



let us know what happens

---

### Post by jhonijim on 2006-12-07
that is what i did and that was what i got in on the other atempts was```
Preconfiguring packages ...
(Reading database ...
```
and it just sat there

---

### Post by Derspankster on 2006-12-10
I am having a similar problem. It appears that Samba is partially installed and I cannot seem to reinstall. Here's my output. I have no idea how to proceed.

 sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
The following packages were automatically installed and are no longer required:
  samba
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu4) ...
 * Starting Samba daemons...                                             [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jhonijim on 2006-12-10
tryed agin and got
```
root@POS2:~# apt-get install samba
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 62 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 7250kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ...

```

any ideas i realy need to get this working

---

### Post by Derspankster on 2006-12-11
Well, in my case, I'm considering doing a complete re-install of Edgy. I haven't been able to get any help with this issue. Skype no longer works since I installed Edgy either.

---

