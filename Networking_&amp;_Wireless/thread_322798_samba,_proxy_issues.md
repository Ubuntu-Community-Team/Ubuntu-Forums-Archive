---
title: "samba, proxy issues?"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by smeg_head on 2006-12-21
i'm new to linux (generally a mac user) and would like some help with a file sharing problem. i have just installed ubuntu 6.10 onto an old mac which we would like to use mainly as a file server. when i attempt to access the 'shared folders' panel in applications  -> system, i'm told that 'filing services are not installed', choosing to 'install services' i get asked for my admin pasword, and then it thinks for a second and dumps me back at the 'filing services are not installed' page... 

i'm accessing the network via a proxy server, could this be my problem? is there a way i can set global proxy settings?

thanks in advance

---

### Post by DerHesse on 2006-12-21
Check th settings in apt.conf 

--> /etc/apt/apt.conf :

it should look like this:

APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "http://username:passwd@Proxy_Server_Name:Portnumber";

---

### Post by smeg_head on 2006-12-21
thanks that worked well, and i appear to be hapily sharing...

now i have another question, if you don't mind, how does one determine the address of the share ie smb://xxx.... etc?

---

### Post by DerHesse on 2006-12-22
you could try :

mount -t cifs //windowsserver/sharename /mountpoint
username=windowsuser,password=windowspassword,workgroup=windowsworkgroup -o uid=linuxuid -o gid=linuxgid -o rw

(change to your needs, all in one line)
you have to create the mountpoint on your ubuntu box e.g.  mkdir /home/your_username/Share_xy
 
linuxuid and linuxgid --> is a number! To find out use $ cat /etc/passwd
probably it's 1000 for both if it is the first user created durin setup.

is it that you are lookink for?

---

### Post by smeg_head on 2006-12-24
i think that is what i'm after, won't have access to my office now until after the holidays

thanks and merry christmas!

---

### Post by DerHesse on 2006-12-24
Merry Christammas, too. :KS

---

