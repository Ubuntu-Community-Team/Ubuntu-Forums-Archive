---
title: "simple instructions for transfering files between two computers"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by ubiubi on 2008-06-22
Hi does anyone know where I can find simple instructions/ software for transfering files from one ubuntu computer to another (conected by a router. I find the new search page/system on the Forum impossible to use. It was much easier last year!
Cheers

---

### Post by issih on 2008-06-22
Requirement no 1, can you ping one machine from the other? i.e.From the command like can you do "ping desktop" where desktop is the other computers name or "ping 192.168.0.X" where the ip address is not assigned by dhcp
Once you can do that, you have a few options.

Simplest is to just use the ssh networking options

Istall the ssh server on both pcs:

"sudo apt-get install openssh-server"

Then Go to Places->Connect To Server

Select SSH as the Service Type,
Enter the name/ip address of the other pc into the server field,
Leave Folder and Port blank for now,
Enter a valid user on the pc you are connecting to in user name
Create a bookmark if you so desire :)

Then hit connect, the system will then ask for your password, and mount the other pc's filesystem in a folder accessible from the desktop and nautilus.

Alternatively you need to use samba to set up a windows network, for which install nautilus share:

"sudo apt-get nautilus share" which will then allow you to configure folder sharing via nautilus's right click menu.

These shares should be vivble from Places->Network

Hope that helps, give me a shout if you are confused

---

### Post by tropdoug on 2008-06-22
I just found this thread, and am wanting the same information. I have two ubuntu (exclusive) machines. Can you tell me, Is samba solely for transfering files etc between a Linux box and a Microsoft windows OS box? 

What is NFS for? 
What is SSH and is there a difference between NFS and SSH which is better. 

I would like to establish a simple home office type network between my two compuuters. I would be connecting via a wireless router. I can already ping the other computer

---

### Post by plewisfdx on 2008-06-22
Samba was reverse engineered to allow unix to co-exist with the smb protocol used in Windows sharing, but also works between two linux computers just fine. 

It can be used to serve files (share a folder on the network) from a linux computer.  I have not done it this way, but here's a tutorial: [http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)

that may answer all your questions, as far as the easiest way to accomplish what you're after.

NFS is another protocol to use to share a drive on the network.  I have tried nfs and samba, and have had much better speed results from samba.  I think nfs is tweakable and could possibly be better/more efficient, but I have not had good results in my limited testing.

The above guide will allow you to try them both to see for yourself.

SSH is a secure shell.  You can connect to a remote computer using ssh, and the data that travels between the computers will be encoded, hence the secure.  You can use sshfs as a protocol to share files between computers, and I've found that to be the fastest way for me.  I have a linux router with an attached drive with an ssh server.  Then all the linux clients mount the network drive with sshfs to their local filesystem and use the files as if they were local to the machine.

Here's a howto for that:
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by tropdoug on 2008-06-22
Thanks for that info, I have set up ssh now and it works a treat. I read the article but I must confess it is too confusing for me. (ie I don't appear to have a 'fuse' group as mentioned etc). 

One thing I need to know, is using the IP address of this machine which is the desktop, gives the user on the laptop complete access to my entire system which is not wise. Can I restrict the access to a set of folders that I "share" as in the old MS way, so that the external user can only see and access those particular folders?

---

### Post by Mgiacchetti on 2008-06-22
> **tropdoug said:**
> Thanks for that info, I have set up ssh now and it works a treat. I read the article but I must confess it is too confusing for me. (ie I don't appear to have a 'fuse' group as mentioned etc). 

One thing I need to know, is using the IP address of this machine which is the desktop, gives the user on the laptop complete access to my entire system which is not wise. Can I restrict the access to a set of folders that I "share" as in the old MS way, so that the external user can only see and access those particular folders?

you do know you can add groups right?
[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#users-and-groups](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#users-and-groups)
just be sure to add yourself to the group after you create it, then do a logout login for it to take effect.

and permissions in samba are easily set...
[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

---

### Post by plewisfdx on 2008-06-22
So you are "sshing" into the desktop from the laptop?

If you want to keep doing this, then create the same user on both machines, and only give the newly created user access to the folders you want him to see on the desktop.   Then when you login from the laptop you can either be logged in as the new user, or 'ssh -l newuser host' where newuser is the name of the restricted user.

You don't need to create a new user for this, but if you use the default user for your desktop, he will now be limited even when locally using the desktop.  

To restrict access on the desktop, chmod the directories and files you want to restrict.  

A much simpler way for all of this is to "share" the desktop folders you want to share (right click "sharing options") and follow the first guide from my last post.

---

### Post by ubiubi on 2008-06-23
Hello all
I'm glad my thread has made someone in Australia happy! I'm still a little confused about the 'ping' thing. If I understand right, I open the console and type 
 "ping (name of other machine/numeric address)"

then what? Should I get conformation of a successful action, a ping noise (don't laugh! I'm really that ignorant, pity me!)?

It's very reasuring there are so many people out there who have the goodwill and patience to help!

Cheers :popcorn:

---

### Post by issih on 2008-06-23
Yup you have the right idea ubiubi, best way to think of ping is like a sonar on a ship. you send out a ping, and you measure how long it takes to come back. So pinging a specific computer (referenced by name or ip address) is basically measuring the speed of the network connection between you and them. Most commonly, however, it is just used to confirm that a connection exists.

A successful ping looks something like this:

```
PING dre-desktop (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=7.65 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=1.75 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=1.94 ms
64 bytes from 192.168.0.2: icmp_seq=4 ttl=64 time=1.78 ms
64 bytes from 192.168.0.2: icmp_seq=5 ttl=64 time=1.88 ms
```

You just hit ctrl+c to stop it, or it will go on forever.

If it fails to reach the other box for some reason you will see something like this:
"ping: unknown host dre-deskto"

To explain why this is important.... basically all networking actually relies on ip addresses to locate different machines, In the ping above, 192.168.0.2 is the IP address of the machine I call dre-desktop.

Doing "ping dre-desktop" or "ping 192.168.0.2" would reach exactly the same machine. This is possible because the hostname dre-desktop is resolved to the ip address 192.168.0.2.

If you use static ip addresses this is as much as you need to understand, you can set your network up using static ip's and everything will be fine. The trouble arises with dhcp, which is a protocol that assigns ip addresses to computers as they connect to the network. This means that the ip address of your computer can change every time you connect. Most home routers use this technology by default.

This can cause trouble with host name resolution, as the ipaddress that dre-desktop should resolve to is variable. Some routers provide a name resolution service, as they know what computer has what ip address, but not all do this.

There are ways around this however such as using winbind, in essence I need you to try pinging your machines by hostname, and let me know if it works, so we can work out what is required :)

---

### Post by ubiubi on 2008-06-24
Thanks for all your time Issih, I'm not going to be able to try anything until Thursday, but If I try to ping the second computer I use its ububtu desktop name (I dont have to bother with root?)
 Both the "client and "server" computers have the same desktop name  eg "mark~desktop"
Both machines are xp/ubuntu dual boot, I hope this won't complicate things!
Cheers
:KS

---

### Post by issih on 2008-06-24
Rename one of the machines to something else, e.g. markdesktop2

As for the dual boot, tt didn't ought to matter, but just to avoid any possible complications, make sure both machines are booted into ubuntu when testing.

---

