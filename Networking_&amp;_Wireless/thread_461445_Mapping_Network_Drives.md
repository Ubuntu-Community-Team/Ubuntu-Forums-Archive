---
title: "Mapping Network Drives"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by dachinster on 2007-06-01
Hi,
I am used to having my network drives in windows

Now that I am using Ubuntu, how do i automount these Windows Network Drives so I can access them all the time, even after reboot?

oh and another thing.
I have read/write access to these networked drives

---

### Post by mijj on 2007-06-01
i'm pretty new at this, but i managed to get it working as you hope to.
this is how i did it.

1	go into synaptic and install samba

2.	go into edit /etc/fstab as root ... (kdesu kedit /etc/fstab ... or the Ubuntu equivalent: gksudo gedit /etc/fstab)
for each network drive add a line similar to the following:
//192.168.1.4/archive /home/mijj/NAS/archive smbfs credentials=/home/mijj/NAS/.smbcredentials,dmask=777,fmask=777 0 0

note: 	//192.168.1.4/archive - is my case of the network address of teh drive.
note:	/home/mijj/NAS/archive - is the empty directory I created as a mountpoint for the network drive
note:	smbfs - this is the samba file system
note:	credentials=/home/mijj/NAS/.smbcredentials - this is the file i created to keep the username, password
	.. the file content looks like this:
username=xxxxxxx
password=yyyyyyyyy

adjust the details to suit.

thus .. you will be logged onto the network drives and have access available at teh mountpoints automatically at each startup.

---

### Post by mijj on 2007-06-01
p.s .. i *think* the mountpoint has to be created as root ...

... in my example above the mountpoint was:  ***/home/mijj/NAS/archive***
this was created by the command line: ***sudo mkdir /home/mijj/NAS/archive***

---

### Post by dachinster on 2007-06-01
thanks for the response
today is friday though, so ill try again on Monday
If you think up anything else, let me know

---

### Post by mijj on 2007-06-02
why should anyone think up anything else.  The answer was perfect.

8-)

---

