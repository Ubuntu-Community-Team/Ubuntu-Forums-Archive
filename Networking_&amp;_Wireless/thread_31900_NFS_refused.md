---
title: "NFS refused"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by Gowator on 2005-05-05
> root@ubuntu:/home/myuser # mount 192.168.2.12:/media/sda1 /mnt/sda1
mount: RPC: Remote system error - Connection refused


this is driving me mad....
this is from .12 so its essentially local and my exports says 

/media/sda1    *(rw)

but 
mount localhost:/media/sda1 /mnt/sda1  works!!!!

since I actually want to mount from a remote machine this is pretty useless.  
I think its some stupid security shit since i had the same probelm with mandrake and hence ditched it because they had played about with pam....  

I just want to export and mount not fsck about with pam... so if anyone knows how to get it working please help

---

### Post by nad on 2005-05-05
How is your /etc/hosts.allow file configured? /etc/hosts.deny ? The output of: rpcinfo -p ?

---

### Post by Gowator on 2005-05-05
[QUOTE=nad]How is your /etc/hosts.allow file configured? /etc/hosts.deny ? The output of: rpcinfo -p ?[/QUOTE]


hosts.allow and hosts.deny are blank (just comment lines)

```
root@ubuntu:/home/sl # rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    953  status
    100024    1   tcp    956  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32776  nlockmgr
    100021    3   udp  32776  nlockmgr
    100021    4   udp  32776  nlockmgr
    100021    1   tcp  32828  nlockmgr
    100021    3   tcp  32828  nlockmgr
    100021    4   tcp  32828  nlockmgr
    100005    1   udp    801  mountd
    100005    1   tcp    804  mountd
    100005    2   udp    801  mountd
    100005    2   tcp    804  mountd
    100005    3   udp    801  mountd
    100005    3   tcp    804  mountd
```

---

### Post by nad on 2005-05-05
Add the line: portmap: 192.168.2.0/255.255.255.0 (if this is your networks address and netmask, modify as needed) to /etc/hosts.allow , and the line: portmap: ALL  to /etc/hosts.deny .

---

### Post by Gowator on 2005-05-05
[QUOTE=nad]Add the line: portmap: 192.168.2.0/255.255.255.0 (if this is your networks address and netmask, modify as needed) to /etc/hosts.allow , and the line: portmap: ALL  to /etc/hosts.deny .[/QUOTE]


thanks I tried but same thing, can still mount localhost but not by IP...  

I changed the hosts to have ubuntu on the IP add (it was a synonym for localhost and worked) and now thats not working so its not the resolv.conf...

---

### Post by nad on 2005-05-05
Have you made these changes to both machines? Restarted nfs to read the new configs?

Read your logs to see what the problem is. I would also replace that wildcard in your exports file with more specific addressing.

---

### Post by Gowator on 2005-05-05
[QUOTE=nad]Have you made these changes to both machines? Restarted nfs to read the new configs?

Read your logs to see what the problem is. I would also replace that wildcard in your exports file with more specific addressing.[/QUOTE]


Ah nope, it was running fine under debian testing, the other machine is an XBOX running deb too.  

I was planning on sticking the subnet and replacing the * once it was up...  basically my XBox is connected to thte big screen projector and I have no films !!!  ahhhh  



edit however I can't mount from the same machine via IP...  so its not looking good.

---

### Post by Gowator on 2005-05-05
```
May  5 15:57:29 localhost rpc.mountd: authenticated unmount request from localhost.localdomain:620 for /media/sda1 (/media/sda1)
May  5 15:57:46 localhost rpc.mountd: authenticated mount request from localhost.localdomain:622 for /media/sda1 (/media/sda1)
```

??  

from messages... but not much help !

these are to localhost and work,
the refused doesn't leave anything in messages .. which makes me think its being blocked

---

### Post by Gowator on 2005-05-05
still  lost... has anyone got it working?

---

### Post by nad on 2005-05-06
Read the nfs ubuntu wiki.

They've got this system locked down tight.

---

### Post by Gowator on 2005-05-09
[QUOTE=nad]Read the nfs ubuntu wiki.

They've got this system locked down tight.[/QUOTE]


Hmm I think I will just reinstall debian instead.  
Ubuntu isn't linux anymore if you can't do NFS from editing an exports file and doing an exportfs -ra.  

This is why I kicked Mandrake offmy boxes becaus they start fscking about in stuff they shouldn't and locking down linux so that I can no longer tell it what to do and instead it tells me...  sounds like a OS I quit years ago!  

Oh well.

---

### Post by nad on 2005-05-09
On that hosts.allow line, you have to include all the daemons: portmap lockd mountd nfsd statd

Then restart portmap and nfs-kernel-common

---

### Post by Gowator on 2005-05-10
[QUOTE=nad]On that hosts.allow line, you have to include all the daemons: portmap lockd mountd nfsd statd

Then restart portmap and nfs-kernel-common[/QUOTE]

Hmm sounds easier to go back to debian ..  
nfs is one of the most basic services and if Ubuntu can't do it then it sounds like I will have the same type of problems with every other service.  

I can hardly recognise linux under it anymore with the whole sudo stuff and implimenting whatever hack they have to prevent NFS working as it should.  
I have to work in a mixed environment with other unix's and linux distro's and I simply can't be bothered learning what some distro believes everyone else is wrong.  

This is just one of the most basic services but next I need to get my mail server back online etc. and so far I can't even get NFS working whereas any unhacked distro will have it working in minutes.  

I can reinstall Debian testing faster than I can get a single server up ... and I have yet to discover what they have done to postfix et al.  or even where these changes are made ? 

 If I install a non ubuntu NFS will that work ?  Can I force and install from stable or from source ... I don't even see where/what they have hacked or why they want to stop users using NFS?

edits:  tried various parts of the wiki non of which went into this under nfs?  
I really don't understand wtf they have done to prevent things working or why?

---

### Post by Gowator on 2005-05-11
There are 4 wiki's for NFS server + 1
 

/etc/hosts.allow and /etc/hosts.deny
NFSServer
NFSServerHowTo
SettingUpNFSHowTo
SettingUpNISHowTo

[http://www.ubuntulinux.org/wiki/NFSServerHowTo](http://www.ubuntulinux.org/wiki/NFSServerHowTo) is the one that works...

the important part is
> 
By default, the portmap service is only accessible on the local system. For NFS service to work, access must be allowed from NFS clients as well. Edit the file /etc/default/portmap and remove the -i 127.0.0.1 option from ARGS  

It seems to be a secret in Ubunbtu not to tell anyone this  so I guess this post will be edited by mods.  (lets see)

Non of the other wiki's mention this and [https://www.ubuntulinux.org/wiki/SettingUpNFSHowTo](https://www.ubuntulinux.org/wiki/SettingUpNFSHowTo) is just plain wrong.  

> 1. (Warty Only) Edit /etc/default/portmap and comment out the ARGS="-i 127.0.0.1" line. Note that this is already done if you're running the machine as an NIS server.  
In that my Hoary had this line which people alluded to but noone could be bothered to tell me about!  

anyway... this worked once I found the correct Wiki entry... though why its not explained in the debconf part of the configuration I don't know?

---

