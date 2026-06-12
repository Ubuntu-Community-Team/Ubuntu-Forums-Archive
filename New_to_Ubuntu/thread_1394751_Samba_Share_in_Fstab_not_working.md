---
title: "Samba Share in Fstab not working"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by uzd4ce on 2010-01-31
This is probably something simple, but I can't get it to work.

Trying to share a folder from one 9.10 machine to another.

Shared folder is /home/bill/1a. I can browse for it in Nautilus on the other machine and it mounts fine.  smb://bill-lenovo/1a/ I can bookmark it, but want it to mount at startup.

The bill-lenovo machine is 192.168.0.102.  This is the line I'm trying to add to Fstab on the second machine.

//192.168.0.102/1a /media/1a smbfs
 auto,rw,username=bill,password=*****

The error I get is "Mount point does not exist" but /media/1a does exist on the second machine.


Edit: Oh, it was something simple.  When I copied that line, I didn't take out the line break.  That solved it.

I've also tried 
//192.168.0.102/home/bill/1a /media/1a smbfs
 auto,rw,username=bill,password=*****

in case the error applies to the shared folder but that doesn't work either.

What am I doing wrong?

Thanks

---

### Post by maniaq on 2010-02-17
hello I had the same problem when I went from Hardy to Karmic..

the exact same line which worked in Hardy ***didn't*** work in Karmic

why?

because for some strange reason, TPTB decided that when someone types in the the command:

[sudo] apt-get install samba

*cifs* will not be included and you will in fact have to install it separately

-and it gets worse! you cannot actually do a:

[sudo] apt-get install cifs

-there's no such package! Despite smbfs being "deprecated" in favour of cifs some time ago, you actually have to (SEPARATELY) run the command:

[sudo] apt-get install smbfs

or do them both separately like:

[sudo] apt-get install samba smbfs

why? I don't know

...but once I installed smbfs - which was not installed by default when I installed "samba" - I was able to make my samba shares in my fstab file mount properly...

go figure

---

