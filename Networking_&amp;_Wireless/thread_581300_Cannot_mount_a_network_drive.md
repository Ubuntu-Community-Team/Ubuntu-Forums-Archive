---
title: "Cannot mount a network drive"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by helvete on 2007-10-19
i got a new network drive and i am trying to get ubuntu to find it but it can't, looking for a how to on this, i can connect to the admin part of the drive thru my browser but actully mounting it i cannot seem to do, its FAT32 320gb drive

under findsmb it shows me the drive but after that i cannot mount it at all

any help is appreciated

on Gutsy Gibbon

---

### Post by loveshackdave on 2007-10-19
do you have smbfs installed?

---

### Post by helvete on 2007-10-19
i do yeah

---

### Post by loveshackdave on 2007-10-19
hmm, have you tried mounting using the IP address of the networked drive rather than the host-name?

---

### Post by helvete on 2007-10-19
how do i go about doing that, i'm relativly new at linux, somethings i've figured out in the past, just need a pointer in the right direction

---

### Post by loveshackdave on 2007-10-19
well, if you can ping the drive, either from your linux box or an xp box, by its host name then it will spit out the ip address (will be in the form of 192.168.0.3 or something). Or, you can often go to your router's admin page to see a list of connected devices and their ip addresses. Once you have the ip address just type smb://ip-address/ in your file browser and it should show up.

Example, say drivename is the name you type in your browser to access the drives admin page:
Open a command prompt and type:

ping drivename

This will spit out the ip address. For some reason, my ubuntu install doesn't like to connect with other machines using the host-name bu the ip works fine, haven't figured this out yet, but this might be why you can't connect.

---

### Post by helvete on 2007-10-19
thanks for that i can ping it ok, so how would i mount it, or have it showing up in the network folder?

---

### Post by loveshackdave on 2007-10-19
well, if you can ping it by name, then it probably isn't a hostname problem, if you can't then that may be the problem. Say the ip address is 192.168.0.3, you can type smb://192.168.0.3/ in the file browser address bar or do the following:

sudo mkdir /media/netdrive
sudo mount -t smbfs //192.168.0.3/ /media/netdrive

this will mount it to the path /media/netdrive/

---

### Post by helvete on 2007-10-19
ok media has a file named netdrive
but the second line gave an error

> 24356: tree connect failed: ERRSRV - ERRaccess (The requester does not have  the  necessary  access  rights  within  the specified  context for the requested function. The context is defined by the TID or the UID.)
SMB connection failed


---

### Post by loveshackdave on 2007-10-19
weird, do you have your network drive passworded? if so use:

sudo mount -t smbfs //192.168.0.3/ /media/netdrive -o username=username,password=password

The other thought I had is that maybe the drive isn't accessible through root and you have to enter the path. Can you connect to the drive with a windows machine? If so is there a path after the drivename? then try

sudo mount -t smbfs //192.168.0.3/whatever_your_path_is /media/netdrive

---

### Post by helvete on 2007-10-19
i looked on my windoze box and it actually has it as M, but its also Public on M so i put in public to the sudo cmd and it picked it up, will it be permanently mounted there? is no then how can i do that?

also i can't change any permissions, i know it can be done thru sudo to change the read write permission, what cmd would i need to put in for all users to have read write access?

---

### Post by Hero of Time on 2007-10-19
If you want to have full permissions, you have to change them using chmod 777 /media/netdrive (your mountpoint) and chown <username>:<groupname> /media/netdrive.

---

### Post by loveshackdave on 2007-10-19
you can add it permanently in two ways.

1) edit your session to run the sudo -mount command when you logon. system->administration->sessions 

2) edit your fstab file to mount it at startup (probably the better option):
sudo vim /etc/fstab
add the following line:
//192.168.0.3/your_path /media/netdrive smbfs

you can also probably use the hostname instead of the ip address too now that the path is fixed.

---

### Post by helvete on 2007-10-19
great all seems to be working fine, thanks for all the help and hero of time too

---

### Post by loveshackdave on 2007-10-19
> **Hero of Time said:**
> If you want to have full permissions, you have to change them using chmod 777 /media/netdrive (your mountpoint) and chown <username>:<groupname> /media/netdrive.

also to clarify you need sudo:

sudo chmod 777 /media/netdrive

---

### Post by Hero of Time on 2007-10-19
> **loveshackdave said:**
> also to clarify you need sudo:

sudo chmod 777 /media/netdrive
It's obvious to use sudo when using chmod and chown when you're not in your home folder or logged on as root. It is helpful though to mention it, especially for the newbies.

---

### Post by helvete on 2007-10-20
i'm trying to change the owner but it says operation not permitted, putting in my username and group, right clicking on the drive tells me the permissions are as follows:
owner: root 
folder access: create and delete files
group:root
folder access: access files
others: -
folder access: access files

so if i put myself as in the root usergroup would that give me the correct permissions to read write?

thanks for the help so far :D

---

### Post by Hero of Time on 2007-10-20
> **helvete said:**
> i'm trying to change the owner but it says operation not permitted, putting in my username and group, right clicking on the drive tells me the permissions are as follows:
owner: root 
folder access: create and delete files
group:root
folder access: access files
others: -
folder access: access files

so if i put myself as in the root usergroup would that give me the correct permissions to read write?

thanks for the help so far :D
That would give you the right permissions, but causes a great security thread aswell. Use 'sudo chown user:group full folder path' and then check with ls -l (small L).

---

