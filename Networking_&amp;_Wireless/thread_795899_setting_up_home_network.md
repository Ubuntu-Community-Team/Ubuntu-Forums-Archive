---
title: "setting up home network"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by mamboze on 2008-05-15
Hi,
I want to set a simple home network, sharing files and printers and internet access. 
There are two boxes
one running Gutsy has 2 ethernet connections eth0 and eth1 which are working OK (both will connect to the internet). 
the other is a Hardy box and has 1 ethernet connection, also connectable to the internet. 
The two are connected by cable. 
My problem is how to go about this. I've check out this forum but unless I've missed some threads there doesn't seem to be anything at this simple a leve. 

thanks for any help.

---

### Post by empthollow on 2008-05-15
File Sharing:

I've found the most solid way to share files is nfs. currently there is no graphical utility to mount nfs, so you need to use the mount command or put it in /etc/fstab so that it will mount automatically (that is the method i use).  If you are looking for a graphical way to share files you may try samba which is based on windows file sharing.  Nautilus does not browse samba shares without issues as of yet so i would recommend pyNeighborhood in the repos.  

Print Sharing:
CUPS (Common Unix Printing System) is your best bet here and the server comes with a wonderful web interface.  You can access this through your web browser by visiting the url localhost:631  You can share with linux/unix/ or MacOS as the package is now maintained by apple.  

I can provide you with details and additional help if you are interested or get stumped, so feel free to ask. :guitar:

---

### Post by Iowan on 2008-05-16
[Here]("http://ubuntuforums.org/showthread.php?t=793308") is one SSH-based sharing HowTo.

---

### Post by mamboze on 2008-05-17
thanks to you both for your help, sorry I didn't reply earlier but I had a broadband outage yesterday and today I upgraded the 7.10 box to 8.04. 

One question I do have tho, what would be the best way to get one machine to access the net going thru the other machine which is online. Or is it better just to connect each machine independently to the router (it has 4 ethernet connections).

---

### Post by empthollow on 2008-05-17
you will get a better connection if you connect the machines individually.  I have never done internet connection sharing but it is possible.

---

### Post by mamboze on 2008-05-28
Hi, 
Since I last posted I've set the network up with a D-Link DES 108 hub with router to hub. I would like to file share so would the previous advice apply now? 

thanks

---

### Post by Iowan on 2008-05-28
In case you need _more_ options, in [this]("http://ubuntuforums.org/showthread.php?t=810619") thread I've referenced a few Samba setup How-To's (but I'm not suggesting you abandon NFS or SSH sharing).

---

### Post by mamboze on 2008-05-29
Hi Iowan,

I followed up your SSH link. But there are a couple of issues. When I try to connect to the server on either machine, this brings up an error message on one 192.168.1.3
[B]Can't display location "sftp://carlos@192.168.1.33/home"
connection refused by server[/B]

and on the other 192,168.1.33
[B]Can't display location "sftp://roy@192.168.1.3/home"
connection refused by server[/B]
both bookmarks are visible on Places>network but neither work. Ono returns a window saying access denied and the other repeatedly displays a password window tho it is been filled correctly.

I have Firestarter installed on on computer. But when I access the config window, I get an error message 
[B]Failed to start firewall 
the device eth1 is not ready    [/B]
eth1 refers to an unused network card installed on 192.168.1.3  
I shut down, removed it and booted again but the message still remains
Any suggestions?

---

### Post by mamboze on 2008-05-29
Hi Iowan,

I checked out your SSH link. During setup, I had a couple of issues. Connecting to server gave error messages for both comps,

[B]Can't display location "sftp://carlos@192.168.1.33/home"
Connection refused by server [/B]

[B]Can't display location "sftp://roy@192.168.1.3/home"
Connection refused by server[/B]

Both comps have firestarter, this was turned off on one but the other gave the message
[B]Failed to start the firewall
The device eth0 is not ready[/B]

I don't know what going on here. The comps are connected identically to hub and then hub to router. Tho the comp with the firewall problem was originally connected by itself to the router. 

Any suggestions?

---

### Post by mamboze on 2008-05-29
Sorry for the double post, not sure what happened there :)

---

