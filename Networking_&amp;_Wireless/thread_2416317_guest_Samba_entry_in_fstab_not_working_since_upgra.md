---
title: "guest Samba entry in fstab not working since upgrade to 1904 (permission denied)"
date: 2019-04-08
forum: Networking &amp; Wireless
---

### Post by nico-jabin on 2019-04-08
Hi,

I have an entry in my fstab that was working fine establishing a guest connection to my raspberry-pi-connected HDD:

```
//192.168.1.3/hdd /home/nico/hdd guest,uid=nico,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0
```
Since upgrading, I get error 13, permission denied (visible on sudo mount -a). Mounting manually using 

```
sudo mount -t cifs //192.168.1.3/hdd /home/nico/hdd -o guest,uid=nico,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0
```

has the same effect.

Any idea what could have changed? It did work just fine before the upgrade about an hour ago, though it might have not been meant to work.

The relevant entry in the smb.conf:
```

usershare allow guests = yes
[hdd]
    comment = pi hard drive
    path = /media/pi/hdd
    browseable = yes
    writeable = yes
    only guest = no
    create mask = 0777
    directory mask = 0777
    public = yes
    guest ok = yes
    force user = pi

```

Just checked in the /var/log/samba/log. file on the raspberry pi, and it is, as of this evening, full of entries like this:
```

  Bad SMB2 signature for message
[2019/04/08 23:01:47.270889,  0] ../lib/util/util.c:555(dump_data)
  [0000] 39 55 CC 79 3A 7C C0 2D   0C CC 1A 7A 1F 74 98 C1   9U.y:|.- ...z.t..
[2019/04/08 23:01:47.271223,  0] ../lib/util/util.c:555(dump_data)
  [0000] 33 EA 83 F9 1D A4 10 F5   EA 88 2C 1C 5D 3A 4C 22   3....... ..,.]:L"
[2019/04/08 23:01:47.273230,  0] ../libcli/smb/smb2_signing.c:171(smb2_signing_check_pdu)

```

---

### Post by TheFu on 2019-04-11
Update: fixed vers mistake in the code block below. It originally said ver=2, should have said "vers=2.0" - see posts below for details. I had tested the "vers=2" here and it did work.  Win7 can support vers=2.1.  

Add vers=2 into the mount options, see if that helps.  That seems to be the complaint in the logs.

```
sudo mount -t cifs //192.168.1.3/hdd /home/nico/hdd -o vers=2.0,guest,uid=nico,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0
```

Is there a reason you didn't choose to use NFS between 2 Unix systems instead?  NFS is the native method, more efficient and honors file permissions, as expected.

---

### Post by Morbius1 on 2019-04-11
What a curious bug.

It's exactly as you described it in that it only affects guest access. If I pass a username and password in the mount the same share mounts without issue. If I specify a version number ( any version number, vers=1.0, 2.0, 3.0, ... ) guest access works.

Turns out it's a kernel bug and hopefully it will be fixed before 19.04 is released: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1821053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1821053)

---

### Post by nico-jabin on 2019-04-12
Oh glad it's not me then. 

In case it helps anyone else in the meantime: *vers=2.0* helps. 

As for NFS... will have to check that out! :)

---

### Post by TheFu on 2019-04-12
My mount.cifs code above should have "vers=" not "ver=" - that is a copy/paste error.

I don't know where I found the "vers=2" option.  Today, all my autofs settings are using "vers=2.1" and haven't been modified since early March. These are only used to connect to Win7 systems. Can only guess from an old script somewhere.  I did test it on my newest system.

From the mount.cifs manpage:
```
       vers=
           SMB protocol version. Allowed values are:

           Â·   1.0 - The classic CIFS/SMBv1 protocol. This is the default.

           Â·   2.0 - The SMBv2.002 protocol. This was initially introduced in
               Windows Vista Service Pack 1, and Windows Server 2008. Note
               that the initial release version of Windows Vista spoke a
               slightly different dialect (2.000) that is not supported.

           Â·   2.1 - The SMBv2.1 protocol that was introduced in Microsoft
               Windows 7 and Windows Server 2008R2.

           Â·   3.0 - The SMBv3.0 protocol that was introduced in Microsoft
               Windows 8 and Windows Server 2012.

           Note too that while this option governs the protocol version used,
           not all features of each version are available.
```

Anyways, please mark this thread as SOLVED - thread tools button near the top to help others out.

---

### Post by Morbius1 on 2019-04-13
Well that didn't take long. Had an update to a new Linux kernel just now and the issue was resolved.  Try it without adding any vers option and see if guest access now works for you.

---

