---
title: "File sharing - Ubuntu 10.10 on both.  They can't see one another"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by guest5 on 2010-11-28
I have installed Ubuntu 10.10 on two computers. Niether one can see the other, at all.  Both have samba shares turned on as well as a folder setup to share.  Here is the smbtree for one of them.

ray@ubuntu:~$ smbtree
Enter ray's password: 
WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
		\\UBUNTU\goop           	Ray is sharing Goop on Ubuntu
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
ray@ubuntu:~$

---

### Post by llawwehttam on 2010-11-28
Sounds like a firewall issue.

install GUFW to configure it ```
sudo apt-get install gufw
```

then go to 

System > Administration > Firewall

and add an exception for the samba service.

---

### Post by guest5 on 2010-11-28
I can't see the other computer at all.

I didn't install or activate the installed firewall yet.  I wanted to get these two seeing one another first.

---

### Post by guest5 on 2010-11-28
I installed the configuration app and allowed the samba service, but that didn't help, unfortunately.

---

### Post by takisan on 2010-11-28
Can you access the internet from both computers? Do they both have an IP address? If they both have IP addresses on the same subnet, they should be able to communicate with each other.

---

### Post by guest5 on 2010-11-28
Yes, I agree.  They should.  Here is another output to review:

ray@ubuntu:~$ net usershare info
[goop]
path=/home/ray/Goop
comment=Ray is sharing Goop on Ubuntu
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by takisan on 2010-11-28
I'm sorry if I'm not exactly giving clear answers or anything, but because you're just going from Ubuntu to Ubuntu, I would recommend Linux NFS. Usually I would just use Samba for communicating between a Windows computer and something else.
[https://help.ubuntu.com/10.10/serverguide/C/network-file-system.html](https://help.ubuntu.com/10.10/serverguide/C/network-file-system.html)

---

### Post by guest5 on 2010-11-28
It's cool-I think we're on the same page here;  I used the graphical interface:

System/Administration/Shared folders, added the shared folder, then added the allowed host using NFS. Next went and shared the folder in Places/username (ray) Goop, which is the name of the shared folder...

---

### Post by guest5 on 2010-11-28
[IMG]http://uppix.net/9/2/a/1b630f5b00e50b68f4a0ebd09f289.png[/IMG]

---

### Post by guest5 on 2010-11-28
Is it possible that my host name is incorrect ?   

my pc = ray@ubuntu
other pc = helen@ubuntu

Neither pc can see the other.

---

### Post by takisan on 2010-11-28
Are their hostnames both ubuntu? That could be the problem. I just name all of my computers after Star Trek characters just to keep them organized and able to communicate with each other.

---

### Post by guest5 on 2010-11-28
yes they are both named ubuntu.  can you tell me how to rename one of the hostnames please?

---

### Post by JC Cheloven on 2010-11-28
> **guest5 said:**
> Is it possible that my host name is incorrect ?   

my pc = ray@ubuntu
other pc = helen@ubuntu

Neither pc can see the other.

It seems to be the problem: both machines are named ubuntu. The prefix before the "@" is the user, the rest is the machime name. 

Try changing the name of one of them (I'd suggest in both, so that a more descriptive name is given). It is in the file ```
/etc/hostname
```
EDIT: of course do it as root, and reboot the pc afterwards

That should be it ;)

---

### Post by guest5 on 2010-11-28
OK, now we're getting somewhere, and the comma but thing is present...

I made the change on my pc, and I can see helen's shares but she cannot see me.  Instead, her's times out.  So I looked at her share configuration via the graphical interface, and her's has added something.

Her's added the share 0.0.0.0/0

So my question must become, to add that on mine, am I adding an ip or what ?

Any ideas ?

edit in; I rebooted both pc's.

---

### Post by guest5 on 2010-11-28
I forgot to add my new host name to her pc, she can now see me and I believe after a few minutes she will also be able to access my shares.

Thanks a bunch,
Guest5

---

### Post by guest5 on 2010-11-29
This version of Ubuntu must have some issues regarding file sharing or I'm an idiot.  

This morning I continued the endeavor and, much to my dismay, I can no longer connect to any file shares, not even my own, whereas last night I could connect to her pc just fine.

I get the message:
Failed to retrieve share list from server.

---

### Post by guest5 on 2010-11-29
Resolved, finally.  It was the fact that I turned on the firewall.

I really don't see the point of this firewall if I have to allow all incoming access for all those ports for both nfs and samba.  Or are they restricted to just these two programs for those ports ?

---

### Post by JC Cheloven on 2010-11-29
> **guest5 said:**
> Resolved, finally.  It was the fact that I turned on the firewall.

I really don't see the point of this firewall if I have to allow all incoming access for all those ports for both nfs and samba.  Or are they restricted to just these two programs for those ports ?

If I were you I'd try to look a bit in deepth, despite the fact "it works now". I mean:The iptables firewall is always there in ubuntu, even if you haven't installed some GUI to control it. The default configuration of iptables should let you share your files normally. If it didn't and now does, you may have created (not on purpose of course) some security hole in your network.

It is still unclear to me what you did exactly from the beginning in order to share your files. Not asking you to do so (not specially interested LOL). I'll tell you instead what works "out of the box" for me. They're a 10.10 and a 9.10 Ubuntu systems. 

[INDENT]Nautilus on the 1st computer. Right click on the folder I want to share (that is a folder I own). Choose "Sharing options". Mark "sharing" and eventually "allow other users to write in this folder". Take care that the workgroup (=WORGROUP by default) matches the one in the 2dn (host) machine. [/INDENT]
This allows me to view and modify the files in the 1st pc remotely from the 2nd pc, using nautilus. The backend used for sharing when doing this is SAMBA.  

Conversely, doing similary on the 2nd pc, allows me to view and modify files from the 1st one. 

Dunno if this is what you did. If not, hope it helps!

Final note: In case the above were not enough for your needs, you may consider to setup a SSH server in one of both of your computers.
Final note 2: please mark your thread as solved when you feel it's solved.

Greetings
JC

---

### Post by guest5 on 2010-11-29
Thanks.  I will clarify the problem for those who it may be of some help:


I installed Ubuntu on two machines.
On BOTH machines I used the default host name of "ubuntu"

This confused the heck out of their ability to share.

Once I renamed one of the host machines the problem was resolved.

Thanks a bunch of everyone who contributed to this solution, it was a big help.

---

### Post by JC Cheloven on 2010-12-01
For your records: to mark as solved the thread you should use the "Thread tools" menu which is at the top of the page (red bold letters) ;)
Cheers

---

