---
title: "Samba Share Problems"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by immaage on 2007-01-15
Hi I'm pretty new to *nix in general, but I know how to get my way around a distro thats set up. I recently decided to set up a file server for my house and used this blog to try and set up a samba share:
[http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html](http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html)

After a couple installations, bit torrent and stuff works, but just not the shares. The guide says in a nutshell to make a directory /incoming/share and use that as the share for everyone. After setting it up however, I can see the share perfectly in Windows and Mac OSX, but when I select the share, it gives the following errors:

Windows:
"\\192.168.1.250\GeneralShare is not accessible. You might not have access to use this network resource. Contact the administrator of this server to find out if you have permission access.

The network path was not found."

Mac:
"The operation cannot be completed because one or more required items cannot be found. (Error code ~43)"


I'm not sure as to whether this is a permission problem, a port problem, or what?! I've checked many posts and it doesn't seem like any of their solutions have helped me.


Here is some other info 

The folder:
drwxrwxrwx 5 root root 4096 2007-01-14 00:40 incoming


smb.conf file:

[global]
        workgroup = WORKGROUP
        netbios name = fileserver
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[General Share]
        comment = General Share Directory
        path = /incoming/share
        valid users = immaage, aznfury684
        admin users = immaage
        read list = immaage, aznfury684
        write list = immaage, aznfury684
        browseable = yes
        writable = yes
        read only = No

---

### Post by sparky-steve on 2007-01-15
Hi,
I'm relatively new to samba, but my server is working fine, and my config differs from yours. I do remember having similar problems to those you described, due if I recall correctly to the passdb & panic action.  Try this:


```


smb.conf file:

[global]
workgroup = WORKGROUP
netbios name = fileserver
server string = %h server (Samba, Ubuntu)
socket options = TCP_NODELAY
obey pam restrictions = Yes
os level = 20
#passdb backend = tdbsam
encrypt passwords = true
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
#panic action = /usr/share/samba/panic-action %d
invalid users = root

[General Share]
comment = General Share Directory
path = /incoming/share
valid users = immaage, aznfury684
admin users = immaage
read list = immaage, aznfury684
write list = immaage, aznfury684
browseable = yes
writable = yes
read only = No


```

The above is a hybrid of your original conf and my working conf.

Hope it helps in some way, even if it doesn't solve it for you....... :-D 

Steve

---

### Post by loganrapp on 2007-06-05
I was having the same exact problem and your solution cleared it right up. Thanks!

---

