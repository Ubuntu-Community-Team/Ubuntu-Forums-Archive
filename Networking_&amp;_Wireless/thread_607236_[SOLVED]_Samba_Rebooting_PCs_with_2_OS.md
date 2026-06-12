---
title: "[SOLVED] Samba: Rebooting PCs with 2 OS"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by hernaaan on 2007-11-08
I'm writing this because I have searched enough without a solution to my problem. Also, forgive my writing mistakes... I haven't practised the language for a while.

I will try to explain thing as clear as I can:
I have three machines joined by Samba. One, Celeron D, has Windows XP and Ubuntu 7.10. Two, Pentium 4, has Windows XP and Kubuntu 7.10. Three, Celeron M, has only Windows XP. I also have a printer in Celeron D, but it's not relevant.

You can have a look at it in the next link, and a short explanation of what it shares, although it's in spanish:
[http://hernaaan.blogspot.com/2007/11/red.html](http://hernaaan.blogspot.com/2007/11/red.html)

The network works, basically. I can access the shared folders on all machines from all of them too. But the problem comes when, without powering off any of them, I reboot one with the other Operatim System (either Celeron D or Pentium 4). Then, the Samba connection is lost, and all previous connections are lost. Moreover, Samba is not restored if I reboot again with the previous OS.

Let's put an example: I have Ubuntu on Celeron D, Kubuntu on Pentium 4 and Windows XP on Celeron M (the only OS it has). Then, I reboot Pentium 4 to see if I can access the Samba shared folders. Not only Windows doesn't detect any other machine, but also I cannot access the shared folder in Pentium 4. All connections are broken, and the only way to restore them (to what I have tried) is to power off all of them, and turning on in one OS.

I have read that the problem may be caused by Windows, since (I think) it shuts down some net component, but it's not my case, really (read above). I think it may be something with the IP addresses. Somehow, they are not updated or I miss in one setup step. I have read that the Windows commands
ipconfig /release
ipconfig /flushdns
may solve the problem, but all they do is to clean XP's IP database. The connections are not updated, but erased.

I haven't tried much more, but I would be grateful if someone gives me some **help**.

Thank you all for reading.

---

### Post by mpierce on 2007-11-08
A couple of things are causing your problem:
  1) You need a consistent smb.conf on both linux machines. The files need to differ in what volumes they share. 
 2) All machines need to be in the same workgroup, WORKGROUP
 3) Your /etc/fstab on both linux machines needs to have the volumes you want to mount defined, e.g., 
   //192.168.1.253/F$   /media/lacie250   smbfs   credentials=/home/mpierce/.smbpasswd   0   0

The above example shows that my linux machine will automatically mount the USB HD (F$ which is MS name convention) on the mount point /media/lacie250 using the samba protocol, smbfs. It will not ask for a password as this is stored in the hidden credentials file.

On your XP machine, you need to map the drives and you both the login name and password for each of your linux machines.

Hope this helps...

---

### Post by SpiritIsReality on 2007-11-09
howdy
samba
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)
Wake On Lan
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
networking
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
[http://linux-ip.net/html/](http://linux-ip.net/html/)
[http://www.google.ca/search?hl=en&q=xp+configure+nic&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=xp+configure+nic&btnG=Search&meta=)
hope all goes well
trails

---

### Post by hernaaan on 2007-11-10
Well, all in all I have solved it.

All I had to do was to unify the network machine names, and then the shared directories.

In /etc/samba/smb.conf
```
workgroup = GIO
(...)
[Documentos]
path = /home/hernan/Compartido/
available = yes
browseable = yes
public = yes
writable = no
```

Then, although neither KDE nor Gnome recognized the network (same with XP), I created links to those network paths. I could access them by:
Windows: \\192.168.1.100\Documentos
Linux: smb://192.168.1.100/Documentos
So I made all links from all machines and systems to all machines and systems. A particularity is that with the link to Celeron D (for example) I access the folder in the system being used at that moment, either Windows or Ubuntu.

Now, I have tried all possible combinations, and they all work well! My only 'problem' was that the first time I accessed Ubuntu or Kubuntu, the XPs asked for the Samba password. After that, all has been working well (about until 15 minutes ago). I know there is a way to avoid that, but I don't remember where I saw it... So many forums to rescan that...

---

### Post by SpiritIsReality on 2007-11-10
Samba
SettingUpSamba [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
Samba - Opening Windows to a Wider World [http://samba.org/](http://samba.org/)

---

