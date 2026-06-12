---
title: "Ubuntu NFS (server) and Damm small linux (client)"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by john_spiral on 2006-10-04
Hi,

I've been trying to get my Ubuntu box to share files over my 2 machine network to my laptop running DSL (Damm Small Linux - Knoppix type distro).

I've come to the conclusion after a week of fun that DSL's NFS client isn't supported by Ubuntu's NFS server. 

Anyone had success sharing files from Ubuntu to DSL?

I'm running version 3.0 of DSL and Ubuntu 6.06 LTS.

---

### Post by kidders on 2006-10-04
One NFS implementation is the same as the next, really ... you shouldn't be having any trouble :-( Have you been using the same NFS protocol version on both Linuxes?

What kind of problems have you been having, specifically? (With luck, there's a simple explanation maybe.)

---

### Post by john_spiral on 2006-10-06
I keep getting a 'Permission denied' error when attempting to run the below mount command on the DSL box (192.168.0.2):

sudo mount -t nfs 192.168.0.1:home/john/Desktop/xubuntu /home/john/tmp

I get the following error:

mount -t nfs 192.168.0.1:home/john/Desktop/xubuntu failed, reason given by server: Permission denied

Both machines can ping each other, the ubuntu machine's etc/hosts.allow and hosts.deny are blank and the etc/exports shows the correct shared folder and the allowed ip address 192.168.0.2 (DSL machine).

If I run showmount -e 192.168.0.1 on the DSL machine I get:

Export list for  192.168.0.1:
/home/john/Desktop/xubuntu 192.168.0.2

The Ubuntu machine is seeing the DSL machine as 192.168.0.2 by using a utitlity that tells me who is pinging the Ubuntu box.

I can run a ftp session from DSL to Ubuntu, so the basic network connection between the two machines seems to be in place.

The john account on both machines has the same password.

I've also set the permissions on the /home/john/Desktop/xubuntu folder 777.

I still can't figure out why I'm getting a 'Permission denied' error.

---

### Post by kidders on 2006-10-06
Something worth checking is whether both "john" accounts have the same UID. This may work out to be a dumb suggestion, but when things like this break on _me_, it's *always* because of something silly I did!

In NFS terms, the names of the users are usually irrelevant ... it's their UIDs that really count.

"Permission denied" is so vague, isn't it?! How annoying!

---

### Post by john_spiral on 2006-10-07
I'll have a look at the UID on both machines, thanks for the suggestion

---

### Post by john_spiral on 2006-10-09
I've set the UID & GID in the /etc/passwd & /etc/groups files on the DSL machine, still same prob.

ummmmmmmmmm

any more ideas?

---

### Post by kidders on 2006-10-09
Strange! Just to double-check, both systems should share the same UID for the user you are trying to connect as, and your /etc/exports should allow the remote computer to mount the fileshare. As far as I can make out, both are true on your system. Damn.

If it were me, I'd try to turn up the log verbosity of my NFS software on both the client & server machines ... there *has* to be a reasonable explanation! Btw, are you using the same version of the NFS protocol on both computers?

---

### Post by john_spiral on 2006-10-09
Hi,

How can I determine what NFS protocol I'm using on both the server and client?

Is there a easy way to turn on log verbosity on the NFS server?

thanks

John

---

### Post by kidders on 2006-10-10
Hey again,

I did some testing, and I doubt you actually have a version-related problem. Dumb suggestion... sorry. Afaik you wouldn't see "Permission denied" if you did. Just in case, your system logs will tell you if something odd like that is happening.

Some smarter suggestions:

[LIST]
[*]Check whether you have an /etc/hosts.allow or /etc/hosts.deny that might be interfering with your access rights.
[*]Check that you're not trying to mount something in read/write mode that you only have read access to. (Is "rw" specified in your /etc/exports?)
[*]Check that you aren't exporting multiple points on the same directory tree. (eg trying to export /usr and /usr/local will fail.)
[*]Make sure you've restarted the NFS service since you last tweaked your exports.
[/LIST]

With any luck, one of these will help.

---

### Post by baechti on 2006-10-19
I have just tried to set up a connection between two ubuntu machines.
Edgy beta on server side and Dapper on client side.
After having problems to get access (same problem as you have) i got access but only read. I kept changing my exports file and ended up with this.

/home        192.168.0.100/255.255.255.0(rw,sync)

192.168.0.100 is the lowest ip in my home network and this line should give access to any computer within the same subnet.

For the mount on the client side i'm using:

sudo mount -t nfs 192.168.0.102:/home/myusername /media/myhostname

Of course the directory /media/myhostname has to be existent.

For me it worked.  ;) 

regards Baechti

---

### Post by john_spiral on 2006-12-27
I just realized yesterday why I didn't get NFS to work between my Ubuntu box and my DSL laptop.

The file I wanted to share was owned by root, running [FONT="Courier New"]**chmod 777 xxx.iso**[/FONT] as myself didn't 
respond with a warning that the permissions on the .iso file hadn't been changed. 

I'm sure if I did a 

[FONT="Courier New"][B]sudo su 
chmod 777 xxx.iso[/B][/FONT]

I would have had more joy.

---

