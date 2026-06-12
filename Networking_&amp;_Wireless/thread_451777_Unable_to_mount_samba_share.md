---
title: "Unable to mount samba share"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by longjeanet on 2007-05-22
I have shared a folder on the server but cannot mount that folder on the client  Ubuntu machine. I can see the share from a Windows machine.  
On the Ubuntu client the command
     sudo mount //servername  /fileNameOnClient
gave this error
      mount: wrong fs type, bad option, bad superblock on //192.168.4.100,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I then insaltted smbfs and then ran the same command
     sudo mount //servername  /fileNameOnClient
but got the following usage error
    This command is designed to be run from within /bin/mount by giving
    the option '-t smbfs'. For example:
    mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test

Please could someone tell me what is happening.

---

### Post by lintoolman on 2007-05-22
I need some more details to possibly assist you. 

What is the OS of the server with the share you are trying to mount?

Is the Server part of a domain?  

Are you suppling a correct username and password with the -o option?  You may need to provide the domain name in the "-o" option   

Can you access the share from the windows host versus simply viewing the share?

---

### Post by lintoolman on 2007-05-22
I was attempting to test some options and discovered I also was having issues listed in this thread:  [http://ubuntuforums.org/showthread.php?p=1492284](http://ubuntuforums.org/showthread.php?p=1492284) .  Installing smbfs made everything work perfectly. 

Maybe this issue is the same as yours???

---

### Post by BitTorrentBuddha on 2007-05-22
To mount a samba share use smbmnt instead of mount:```
sudo smbmnt //servername/share /path/to/mountpoint
```

---

### Post by longjeanet on 2007-05-23
Thanks for the tips.  I am not sure whiat I have done differently, but all shares on Ubuntu machines and Wiondows machines can be seen by each other.

---

### Post by lintoolman on 2007-05-23
Probably a type.  The same happens to me.  ;)

---

### Post by noMScraig on 2007-05-30
Another low-tech answer to my problem...meaning no editing configs etc.

I tried konquerer to view my network shares and still could not get the shares to work.

I finally loaded smb4k and now I can access my windows shares

I had to configure smb4k to mount the windows shares as a super user (sudo) but now I can view through conqueror.

Anyway, that's how I got it to work.

-c

[global]
workgroup = @home
security = share
wins support = yes

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups

[Share]
path = /home/craig/Desktop/Share
available = yes
browsable = yes
public = yes
writable = yes

[Movies and Pictures]
path = /media/NETHDD_/Movies and Pictures
available = yes
browsable = yes
public = yes
writable = yes

---

