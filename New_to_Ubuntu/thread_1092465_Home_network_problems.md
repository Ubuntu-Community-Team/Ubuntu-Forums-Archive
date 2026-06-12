---
title: "Home network problems"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by OllieGab on 2009-03-10
When I used Windows I had a wireless "home network" set up; one desktop connected to a router and a laptop which could access files on the desktop.
I now use Ubuntu 8.10 on my desktop and Eeebuntu on a netbook (there's also a Mac in the house which had no problems when using Windows) but I have so far been unable to set the whole thing up.
I'm sure it isn't that difficult and I have tried to follow some advice from various forums but still no luck.
Could someone please guide me through where to start?
If I click on Network on my netbook there is a Windows Network icon there but I cannot "do anything with it". It says: "Unable to mount location. Failed to retrieve share list from server".

Cheers Olllie

---

### Post by Nxion on 2009-03-10
Are you trying to share files from the desktop so all the other computers in the house can access them?

Try This:
[URL="http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/"]
http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/[/URL]

---

### Post by DGortze380 on 2009-03-10
sounds like you're looking for Samba for the desktop.

It will allow you to set up Windows Shares on Linux. All of those shares should then be accessible from Windows/OS X/Linux.

Alternatively, research NFS, sshfs

---

### Post by nothingspecial on 2009-03-10
```
sudo apt get install ssh
```

On both ubuntu machines.

Then the gui way is to go into your menus Places > Connect To Server.
On the service type box choose ssh. In the server box type username@ipaddress. 

Then you should be good to go.

---

### Post by thesavager on 2009-03-10
Hi OllieGab,

It sounds like you have a firewall running , blocking samba.

Always shutdown your firewalls on laptop and desktop for testing your config when putting up a server, I asume your router accepts all local traffic.

You can check if firewall is down with this command:
```
sudo iptables -L -n
```

then output like this you must have:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

If you have this on both machines, test it again.
It should work , out of the box

Let me know if this is of any help.

---

### Post by OllieGab on 2009-03-10
> **nothingspecial said:**
> ```
sudo apt get install ssh
```

On both ubuntu machines.

Just gives me the message "command not found"

Ollie

---

### Post by ephmanjmm on 2009-03-10
sudo apt-get install ssh

---

### Post by OllieGab on 2009-03-10
Hey! It's working!
I made sure I had Samba installed on both machines, did the "install ssh"on the command line on both machines...I just have some permission issues now, but that's another problem which I'll give a go at myself!
Cheers everyone!

---

