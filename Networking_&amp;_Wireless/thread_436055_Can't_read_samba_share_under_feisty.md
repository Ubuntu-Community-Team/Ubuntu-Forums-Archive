---
title: "Can't read samba share under feisty"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by adrpater on 2007-05-07
Dear Ubuntu-lovers,

My router has an USB-stick connected which is accessible from M$ Window$ under \\SMC\Share.
I check this to know if the build-in fileserver on my router was working, and that's the case.
Not that I use any M$ Window$ since I made the switch to Ubuntu. 

Mounting this USB-stick under /media/smc/ works fine.
But... 
when I try to read it like: 

```

:/media/smc$ ls

```

it gives:

```

ls: .: Input-/Output error

```

Well I'm using the dutch Ubuntu translation so this is a translation actually.
On the dutch forum nobody was able to help me.
(For those of you reading dutch, see: [http://forum.ubuntu-nl.org/message/102548](http://forum.ubuntu-nl.org/message/102548))

Anybody any ideas? 

Greetz...

Adr.

---

### Post by dmizer on 2007-05-08
what are you using for your mount command?

---

### Post by adrpater on 2007-05-08
I tried different ways of mounting: 

$ sudo smbmount //SMC/Share ~/mnt/SMC/Share
$ sudo mount -t smbfs //SMC/Share ~/mnt/SMC/Share
$ sudo mount -t smbfs //SMC/SHARE ~/mnt/SMC/SHARE -o guest,rw
$ sudo mount -t smbfs //SMC/SHARE ~/mnt/SMC/SHARE -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

These commands give no error's - only the mentioned I O error.

Mounting with cifs though gives errors

$ sudo mount -t cifs //SMC/SHARE ~/mnt/SMC/SHARE -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

gives:
```

mount error: could not find target server. TCP name SMC/SHARE not found
No ip address specified and hostname not found

```

$ sudo mount -t cifs //192.168.2.1/SHARE ~/mnt/SMC/SHARE -o guest,rw
gives:
```

mount error 20 = Not a directory

```

$ sudo mount -t cifs //192.168.2.1/ ~/mnt/SMC/SHARE -o guest,rw
gives:
```

retrying with upper case share name
mount error 6 = No such device or address

```

Using 
$ smbclient //SMC/SHARE
I can do this:

```

smb: \> ls
SUCCESS - 0 listing \*

                62628 blocks of size 16384. 62608 blocks available
smb: \> mkdir test
smb: \> ls
SUCCESS - 0 listing \*

                62628 blocks of size 16384. 62607 blocks available
smb: \> cd test
smb: \test\> ls
SUCCESS - 0 listing \test\*

                62628 blocks of size 16384. 62607 blocks available
smb: \test\> cd \
smb: \> ls
SUCCESS - 0 listing \*

                62628 blocks of size 16384. 62607 blocks available
smb: \> rd test
smb: \> cd test
cd \test\: ERRDOS - ERRbadpath (Directory invalid.)

```

So with smbclient I can make dirs and delete them (I verified this bij mounting my
USB directly on my system].

dmesg | grep smb gives some errors:

```

[ 1280.568212] smb_errno: class ERRSRV, code 64 from command 0x32
[ 1280.574390] smb_errno: class ERRSRV, code 64 from command 0x32
[ 1280.574399] smb_lookup: find //iPod_Control failed, error=-5
[ 1280.579036] smb_errno: class ERRSRV, code 64 from command 0x32
[ 1280.581114] smb_errno: class ERRSRV, code 64 from command 0x32
[ 1291.471403] smb_errno: class ERRSRV, code 64 from command 0x32
[ 1291.953275] smb_errno: class ERRSRV, code 64 from command 0x32
[ 1310.558865] smb_add_request: request [dd193d80, mid=3] timed out!
[ 1310.558874] smb_lookup: find //.is_audio_player failed, error=-5
[ 1405.013637] smb_errno: class ERRSRV, code 64 from command 0x32

```

I don't have any iPods so I don't understand dmesg mentioning that.

Hope this helps (for helping me) :) 

Thanks for asking,
Greetz,

Adr.

---

### Post by dmizer on 2007-05-08
unless you have your smb.conf file configured properly to look for a wins server, you'll need to use the actual ip of the usb stick.

try:
```
sudo mount -t cifs //192.168.2.1/SHARE /home/username/mnt/SMC/SHARE -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

or in other words ... you should replace the ~/mnt/SMC/SHARE with the full directory listing ... /home/yourusername/mnt/SMC/SHARE

---

### Post by adrpater on 2007-05-08
dmizr the code you gave me just gives:

```

mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

Also mounting on /media/smc doesn't work.

I believe I have my smb.conf configured to use wins server

Here's (some of) my smb.conf: 

```

[global]
; General server settings
    netbios name = adriaan-desktop 
; server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes


```



Something wrong here?

Greetz,

adr.

---

### Post by dmizer on 2007-05-08
yes, i think so.  change wins support to: no

unless you have your network configured as static, and your /etc/hosts file lists all of your network's machine ip addresses and names.

have you installed winbind and configured /etc/nsswitch to include wins?

what is the output of:
```
smbtree
```

---

### Post by adrpater on 2007-05-09
I've set wins to no.
Restarted samba.
Still this I/O error.

smbtree asks for my password and then just gives nothing...   :confused: 

I have winbind installed. 
But I didn't configure /etc/nsswitch

It now looks like this:

```

# /etc/nsswitch.conf

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Thanks dmizr!
I really appreciate your help!

Greetz,

A.

---

### Post by dmizer on 2007-05-10
what router do you have?

---

### Post by adrpater on 2007-05-10
A SMC Barricade g SMC7908 VoWBRA.

---

### Post by dmizer on 2007-05-10
i'm afraid i found absolutely zero information about the built in fileserver on your router.  there appears to be a firmware update available for your router, so you might try that if you haven't already.

do you have any ability to configure the file server on your router?  if so, what kind of options do you have?

---

### Post by adrpater on 2007-05-11
I discovered here: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/730766.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/730766.html) (scan down) that 
the siemens sx541 router has the same hardware as the smc 7908.

More people have the same problem like I have: [http://ubuntuforums.org/showthread.php?p=1108925](http://ubuntuforums.org/showthread.php?p=1108925) 
It seems this indeed is a firmware problem!

When you speak dutch:  [http://gathering.tweakers.net/forum/list_messages/1027751/15](http://gathering.tweakers.net/forum/list_messages/1027751/15)
When you don't speak dutch here a translation of the relevant information found there:

[indent]
This will not work unfortunately. The SMB-serve of the SMC 7908 is a mess. I tested it myself with Linux (OpenSuse 10.1). Mount does not work. With smbclient, you can do nothing sensibly. I was able to upload a file with smbclient once without a password thoug the read and write was password enabled... Reading, even simply asking a listing doen't work at all. 
I simply gave up....
[/indent]

Well I do not give up yet. According to this tread: [http://www.yabu.nl/forum/forum_posts.asp?TID=32&PN=1](http://www.yabu.nl/forum/forum_posts.asp?TID=32&PN=1)
I had to activate UPnP in the router configuration. So I did. Still does not work.

But there seem to be some german fora handeling the problem which I'm going to read...
And else I will contact SMC

dmizr thanks very much for your help!
I discovered this is a firmware problem because you pointed me in that direction!
It wasn't a problem with my settings, like I thought it was, because I have no experience with Samba.
Thanks and thanks again!

---

### Post by adrpater on 2007-05-11
Just a little bit more info:
According to this link: [http://bs.netgaroo.com/sx541/](http://bs.netgaroo.com/sx541/) 
the Siemens sx541 seems to run RTOS ([http://www.smx-rtos.com/ussw/](http://www.smx-rtos.com/ussw/))
I don't know if the SMC does the same, but it seems likely.
For the hackers among us: [http://www.ip-phone-forum.de/showthread.php?t=72010](http://www.ip-phone-forum.de/showthread.php?t=72010).

---

### Post by adrpater on 2007-05-11
The SMC seems to run VxWorks ([http://en.wikipedia.org/wiki/VxWorks](http://en.wikipedia.org/wiki/VxWorks))
POSIX compliant so I don't get why SMB implementation is so bugy.

---

### Post by dmizer on 2007-05-11
well, it looks like all i can do at this point is offer encouragement.  there's some great links you've posted.  if all else fails, it looks like you can replace the firmware with linux firmware.

it could be that the firmware is using an antiquated version of VxWorks which is unable to handle current smbfs/cifs mounts ... but there's nothing more to this statement than educated guessing.

---

