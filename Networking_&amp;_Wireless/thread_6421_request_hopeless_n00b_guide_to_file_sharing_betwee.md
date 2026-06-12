---
title: "request: hopeless n00b guide to file sharing between ubuntu &amp; windows"
date: 2004-11-28
forum: Networking &amp; Wireless
---

### Post by negativ on 2004-11-28
I'm trying to get Samba set up (NFS is the next project) so that I can share files to and from my laptop when it's running WinXP.  I really don't know what the heck I'm doing.

I don't need authentication of any sort.  I just want to be able to share some directories on both machines and move files to and from them.

I got a little farther than I had expected by following [this thread](http://ubuntuforums.org/showthread.php?t=2389), but while I CAN see the windows shares by doing smbclient -L hostname, I can't browse them with nautilus.  I don't know if this is a bug, or something I'm just not doing right.  (I'm on Hoary).

Also, the windows computer can "see" shared folders on the ubuntu machine, but can't browse them.  It asks for a username & password (which I don't really want), but doesn't accept the username & password of the only user configured on the ubuntu machine.  
 
Blah.   :-(   ](*,)    :confused:

---

### Post by FLeiXiuS on 2004-11-28
[QUOTE=negativ]I'm trying to get Samba set up (NFS is the next project) so that I can share files to and from my laptop when it's running WinXP.  I really don't know what the heck I'm doing.

I don't need authentication of any sort.  I just want to be able to share some directories on both machines and move files to and from them.

I got a little farther than I had expected by following [this thread](http://ubuntuforums.org/showthread.php?t=2389), but while I CAN see the windows shares by doing smbclient -L hostname, I can't browse them with nautilus.  I don't know if this is a bug, or something I'm just not doing right.  (I'm on Hoary).

Also, the windows computer can "see" shared folders on the ubuntu machine, but can't browse them.  It asks for a username & password (which I don't really want), but doesn't accept the username & password of the only user configured on the ubuntu machine.  
 
Blah.   :-(   ](*,)    :confused:[/QUOTE]

Samba is the best way, I had a very sweet HOW TO a while ago.  Let me see if I can dig up the archive.

[http://ubuntuforums.org/showthread.php?t=2389](http://ubuntuforums.org/showthread.php?t=2389)
There you are.

---

### Post by negativ on 2004-11-28
well, thanks, but that didn't help at all.

here's /etc/samba/smb.conf:
> 
; /etc/samba/smb.conf
;
; Make sure and restart the server after making changes to this file, ex:
; /etc/rc.d/init.d/smb stop
; /etc/rc.d/init.d/smb start

[global]
; Uncomment this if you want a guest account
  guest account = nobody
   log file = /var/log/samba-log.%m
   lock directory = /var/lock/samba
   share modes = yes

[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mode = 0750

[tmp]
   comment = Temporary file space
   path = /tmp
   read only = no
   public = yes
   
[media]
   comment = Media
   path = /home/negativ/media
   public = yes
   writable = yes
   printable = no
   write list = @ubuntu

XP can see the Ubuntu computer, but when I try to browse it from XP, I get a login prompt which does not respond to the only username & password that exists on the Linux system.  What info is it expecting?   Where do I configure this?

Also, this:> $ smbclient //windowscomputername/share
works fine, and I can browse that share (and others) in the terminal, but Computer -> Network -> Windows Network -> (workgroupname) -> (windowscomputername) allows me to see all shares on the windows computer, but trying to click one of them results only in throbbing Gnome toes forever and ever and ever.

Bug, or misconfiguration?

---

### Post by FLeiXiuS on 2004-12-01
[QUOTE=negativ]well, thanks, but that didn't help at all.

here's /etc/samba/smb.conf:


XP can see the Ubuntu computer, but when I try to browse it from XP, I get a login prompt which does not respond to the only username & password that exists on the Linux system.  What info is it expecting?   Where do I configure this?

Also, this:
works fine, and I can browse that share (and others) in the terminal, but Computer -> Network -> Windows Network -> (workgroupname) -> (windowscomputername) allows me to see all shares on the windows computer, but trying to click one of them results only in throbbing Gnome toes forever and ever and ever.

Bug, or misconfiguration?[/QUOTE]


Just to make sure, but you have set the permissions on the share folders correct.  And if there is a firewall up and running the ports for samba are opened.  Right?

---

### Post by wiseNoob on 2004-12-04
After some searching, I have as of yet not found a way to open the ports 137 + 139 in IPTABLES.  I think this is what FLeiXiuS' problem is.  Can anyone give a simple way to do this?

All I really want to do is open those ports to my lan, not to the internet.  In Fedora, this was quite easy. although on FC3, iptables has a bug that blocks samba from accessing a share (jeez talk about working against linux propagation)... Just switched to Ubunutu.

any help would help

Thanks

---

### Post by chambery on 2004-12-06
[QUOTE=wiseNoob]After some searching, I have as of yet not found a way to open the ports 137 + 139 in IPTABLES.  I think this is what FLeiXiuS' problem is.  Can anyone give a simple way to do this?[/QUOTE]

There is a Gnome app [Firestarter](http://firestarter.sourceforge.net/)  that provides graphical access to this kind of stuff. 

HTH,

Todd

---

### Post by anewculture on 2007-04-30
I believe this is our answer:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+samba+windows+network](http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+samba+windows+network)

---

