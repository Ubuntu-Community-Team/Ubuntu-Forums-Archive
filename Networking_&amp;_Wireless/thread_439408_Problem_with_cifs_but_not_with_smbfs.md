---
title: "Problem with cifs but not with smbfs"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by aleska on 2007-05-10
For some reason I'm getting some weird stuff occurring in my use of cifs.  I had been mounting a nas device (Buffalo Linkstation) using smbfs.  eg I had the following line in my /etc/fstab file:
[INDENT]//linkstation1/share /home/sbskarulis/ls_share smbfs guest,uid=1000,iocharset=iso8859-1,codepage=cp850,cp850 0 0[/INDENT]
For the record, the iocharset and codepage stuff were things I had to do tot get the folder contents coming through in readable english and not japanese symbols.  
Anyway, this approach seemd to work just fine.  However, one night a major read/write activity to the nas seemed to bork it, so I thought I should try cifs instead since smbfs is supposedly depreciated.

So, I changed the line to /etc/fstab to read:
[INDENT]//linkstation1/share    /home/sbskarulis/ls_share  cifs    guest,uid=1000  0       0[/INDENT]
The problem is that with the line used instead, it now somehow doesn't recognize linkstation1 as a netbiosname.  It has no problem when using smbfs, but with cifs, I get the error message:
> mount error: could not find target server. TCP name linkstation1/share not found
No ip address specified and hostname not found

dmesg | tail produce the following:
> [ 2437.984000]  CIFS VFS: No username specified
[ 2437.984000]  CIFS VFS: cifs_mount failed w/return code = -22

Can anybody tell me what I'm doing wrong here?
Thanks!

---

### Post by joey on 2007-05-10
It may require you setting up winbind to do the resolution. Make sure you have smbfs installed as well.

---

### Post by dmizer on 2007-05-10
take a look at the second link in my sig :)

---

### Post by aleska on 2007-05-10
> **dmizer said:**
> take a look at the second link in my sig :)

dmizer: just followed the steps in your second sig link.  You rock!  Seems to work great!
Cheers!

---

### Post by aleska on 2007-05-11
:confused: Ok...so, all is well with my ubuntu machine.  I just tried to replicate the steps with my kubuntu box, and I have a problem.

I've edited the nsswitch file as instructed.  I confirmed the winbind is installed and the daemon is running.  I then edited my /etc/fstab file to follow your syntax again...mine reads:
[INDENT]```
# Following dmizers howto http://ubuntuforums.org/showthread.php?t=288534
//linkstation1/share/Music      /home/aleska/music      cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777    0       0

```[/INDENT]

..and when I enter the command "sudo mount -a" I get the following:
> mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

Like I said, same as I have it set up on the ubuntu box, which seems to be working...for some reason, it isn't here.  Any thoughts?

***update to this post *** all isn't well with the first box.  I forgot to mention that when I went to my kubuntu box, I powered down the linkstation first and rebooted it.  When I went back to the ubuntu machine, it was no longer connected (of course).  When I tried to "sudo mount -a" I got that same error 13 = permission denied message.  Even get it after rebooting the ubuntu machine.  Help?!?  TIA

---

### Post by dmizer on 2007-05-11
what's the output of smbtree?
```
smbtree
```

check to see if there's a firmware update for your linkstation as well.

---

### Post by aleska on 2007-05-11
smbtree results in:
> WORKGROUP
        \\LINKSTATION1                  LinkStation
                \\LINKSTATION1\share            LinkStation Share Folder
                \\LINKSTATION1\info             LinkStation information
                \\LINKSTATION1\lp               Network Printer for Windows


I don't know about firmware.  I know it isn't something I have updated in the past.  I'll look into how one does that (unless you have an idea to point me in the right direction).

BTW - thanks so much for your assistance!

---

### Post by dmizer on 2007-05-11
you can check here for a firmware update: [http://www.buffalotech.com/support/downloads/](http://www.buffalotech.com/support/downloads/) if there is a firmware update, perform it before you do anything else.

next, we'll try changing your fstab line a bit, and reset the entire works to zero here.

replace your current kubuntu fstab line with this:
```
//LINKSTATION1/share      /home/aleska/music      cifs    guest,rw,uid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777    0       0
```
save fstab and do _not_ perform a [sudo mount -a].

turn off all computers on the network.
turn off the linkstation.
turn off (or unplug the power to) your router.
wait about 20 seconds.
turn the power back on to your router only.
wait for the router to completely boot (about 2 minutes if you are unsure)
turn the linkstation back on.
wait for the linkstation to completely boot (again, about 2 minutes if unsure)
turn on the kubuntu box.
see if your share has been mounted or not.  make some changes ... transfer some files ... whatever, just use it for a bit.  then restart your kubuntu machine and see if it automatically remounts.

afterwards ... perform the same steps with your ubuntu machine using this fstab line:
```
//linkstation1/share /home/sbskarulis/ls_share cifs guest,rw,uid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by midorigin on 2007-07-12
I've run into the same promblem
```
# Works fine
//aux/ml		/media/ml	smbfs	noauto,guest,ro,iocharset=utf8	0	0
# Causes error 13
//aux/ml		/media/ml	cifs	noauto,guest,ro,iocharset=utf8	0	0
```
The error produced when using CIFS is
```
$ sudo mount /media/ml
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```
For the record, smbtree looks fine
```
$ smbtree
KGHOME
        *some other computers*
AK
        \\AUX                           aux filserver (Samba, Ubuntu)
                \\AUX\IPC$              IPC Service (aux filserver (Samba, Ubuntu))
                \\AUX\akhdd05           AK storage drive
                \\AUX\akhdd02           AK storage drive
                \\AUX\akhdd01           AK storage drive
                \\AUX\ml                media library
                \\AUX\public            public share
```
My share definition on the server is
```
[ml]
        comment = media library
        path = /media/akhdd01/ml/main
        read only = Yes
        guest ok = Yes
```

Any thoughts?

---

### Post by moschops on 2007-10-22
FYI since I upgraded (well actually clean install) to Gutsy I can no longer ping/access or otherwise use netbios names - I have to use <netbiosname>.local - I think it could be dependent on the nsswitch.conf file but basically I'm using the default Gutsy gave me so others will probably have this problem.  AFter I added .local to my netbiosnames of Windows machiens I was able to use the mount for cifs file systems.

---

