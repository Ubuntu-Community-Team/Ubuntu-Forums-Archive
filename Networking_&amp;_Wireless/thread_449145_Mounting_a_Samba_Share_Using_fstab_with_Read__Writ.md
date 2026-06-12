---
title: "Mounting a Samba Share Using fstab with Read / Write Access"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by TubaTodd on 2007-05-19
I have done extensive reading on the forum, other forums and Google and I have yet to find a solution that works on my system. 

I have 2 Ubuntu PCs (laptop and desktop) on a wireless network in my home. They are both sharing their HOME folders so that my wife and I can share files. The desktop PC houses some family files that I would like to be able to read and WRITE. I have Samba configured sufficiently to read the appropriate shares on each of our machines. I can sit at my laptop and read any file in the HOME folder on the desktop machine. 

I decided to take this a step further and create an fstab line on my laptop that allows me to mount the desktop's share automatically. The line I added was...

```
//KELLY-DESKTOP/kelly /media/sony smbfs auto,username=,password=,uid=1000,umask=000,user  0  0
```

The preceding line automatically mounted the share and produced a drive icon on my Gnome desktop called "Sony" (the desktop machine is a Sony VAIO)

Everything appeared to be great except when I tried to rename a file on the desktop machine from my laptop. The mounted share does NOT have read/write access. It is read-only. I went to the desktop machine and right clicked on the folder and checked the share status. It says that it is using samba and the read-only option is NOT checked. I checked the samba.conf file and at the end it shows that the share is writable. 

Please help me to figure out a solution. Thanks.

---

### Post by TubaTodd on 2007-05-20
bump

---

### Post by TubaTodd on 2007-05-20
bump

No one has seen this before?

---

### Post by Mujaheiden on 2007-05-22
heyTubaTodd

i think its

```
//SERVER/SHARE	/mnt/folder smbfs **dmask=777**,username=,password=	 0 0
```

reboot and it works for me

---

### Post by TubaTodd on 2007-05-22
Thanks I will give it a shot.

---

### Post by dmizer on 2007-05-22
if both computers are linux ... ditch samba for nfs.  take a look at the fourth link in my sig (easier, faster, more stable).

if you're stuck on samba ... take a look at the second link in my sig :)

---

### Post by TubaTodd on 2007-05-23
dmizer:


I followed your link and instructions and configured NFS. It went VERY smoothly. As everyone has said, it's easy to setup and very fast!!! 

I have hit one snag though. I shared my **/home/todd**  folder on my laptop and my laptop can mount it, but my desktop machine keeps saying "server not found" when I mount the share. 

On my desktop I have the **/home/kelly** folder shared and I can mount it from both machines. 

What am I doing wrong? Thanks!!

---

### Post by dmizer on 2007-05-23
> **TubaTodd said:**
> dmizer:


I followed your link and instructions and configured NFS. It went VERY smoothly. As everyone has said, it's easy to setup and very fast!!! 

I have hit one snag though. I shared my **/home/todd**  folder on my laptop and my laptop can mount it, but my desktop machine keeps saying "server not found" when I mount the share. 

On my desktop I have the **/home/kelly** folder shared and I can mount it from both machines. 

What am I doing wrong? Thanks!!

well, first ... credit where credit is due: the link was in my sig, but the thread and instructions were not created by me.  they simply helped me so much that i thought it would be nice to share :)

can you post the contents of your /etc/exports file from the laptop?  do you have iptables (your firewall) configured on the laptop (eg. firestarter)?

---

### Post by TubaTodd on 2007-05-23
> **dmizer said:**
> well, first ... credit where credit is due: the link was in my sig, but the thread and instructions were not created by me.  they simply helped me so much that i thought it would be nice to share :)

can you post the contents of your /etc/exports file from the laptop?  do you have iptables (your firewall) configured on the laptop (eg. firestarter)?

With regard to your signature link....as one of my IT coworkers would say "Take all of the credit and none of the blame."

As a matter of fact I DO have a firewall setup on the laptop....but not the desktop.

Here is my **/etc/exports** 

```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home/todd      192.168.2.1/24(rw) 
```

My laptop is 192.168.2.100
Desktop is 192.168.2.101

Thanks for your help!

---

### Post by dmizer on 2007-05-24
on the laptop, you'll have to configure your firewall to allow port 2049 for your lan (192.168.2.1/24).

---

### Post by TubaTodd on 2007-05-28
Well, we have success....but it's still not perfect. 

1. The desktop still can't mount the share from the laptop even if I modify the Firestarter configuration allowing the port and allowing ALL ip addresses in this range (192.168.2.1/24). It probably goes without saying, but this also means that it's NOT being detected in fstab.

2. I can get it to mount manually, but only after I first shut OFF the firewall AND restart nfs-kernel-server.

3. Suppose I startup one machine without the other being turned on. Of course this means that the fstab will not find the proper network share. Can I somehow automount that fstab network partition as soon as the machine is turned on?? In order words...I bootup the laptop and it doesn't mount the desktop share because the desktop machine is not powered on. Then when I power on the desktop machine, the laptop detects this share as available, so it auto mounts. Can this be done?

---

### Post by TubaTodd on 2007-05-28
Bump!!

---

### Post by dmizer on 2007-05-31
sorry todd, you will need to open one more port on your firewall.

2049 is for nfs, and you'll also need to open port 111 for portmap to work.  my fault, i forgot to mention it.

more information here: [http://www.troubleshooters.com/linux/nfs.htm#_disable_firewalls](http://www.troubleshooters.com/linux/nfs.htm#_disable_firewalls)

---

### Post by dmizer on 2007-06-02
one more fantastic link for configuring your firewall: [http://ubuntuforums.org/showthread.php?t=352486](http://ubuntuforums.org/showthread.php?t=352486)

---

