---
title: "PXE diskless boot problems"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by draggy on 2008-04-27
I've been setting up a PXE diskless boot with ubuntu systems using this guide: [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
Though I've looked at many others to.

Here are my settings:

**nfs root**
```
drwxr-xr-x 21 root root /nfsroot/shuttle
```

**tftp boot**
```
-rwxr-xr-x 1 root root /tftpboot/shuttle/vmlinuz-2.6.22-14-server
-rwxr-xr-x 1 root root /tftpboot/shuttle/initrd.img-2.6.22-14-server
drwxr-xr-x  2 root root  /tftpboot/shuttle
-rwxr-xr-x 1 root root /tftpboot/pxelinux.cfg/default
drwxr-xr-x  2 root root /tftpboot/pxelinux.cfg
-rwxr-xr-x 1 root root /tftpboot/pxelinux.0
drwxr-xr-x  2 root root /tftpboot/
```

**/etc/dhcp3/dhcpd.conf**
```
host shuttle {
        fixed-address 192.168.0.10;
        hardware ethernet 00:30:1b:b6:cf:b5;
        next-server 192.168.0.1;
       filename "/pxelinux.0";
        }
```

**/tftpboot/pxelinux.cfg/default**
```
label xbmc
kernel shuttle/vmlinuz-2.6.22-14-server
append root=/dev/nfs initrd=shuttle/initrd.img-2.6.22-14-server nfsroot=192.168.0.1:/nfsroot/shuttle ip=dhcp rw
```

**/etc/exports**
```
/nfsroot/shuttle             192.168.0.10(rw,no_root_squash,async)
```



When I boot the client, it finds the ip, and tries to load the image, but it throws this error message:
```

ip=192.168.0.10:192.168.0.1:192.168.0.1:255.255.255.0
TFTP prefix: /
Trying to load: pxelinux.cfg/01-00-a0-cc-de-21-39
Trying to load: pxelinux.cfg/C0A8010F
Trying to load: pxelinux.cfg/C0A8010
Trying to load: pxelinux.cfg/C0A801
Trying to load: pxelinux.cfg/C0A80
Trying to load: pxelinux.cfg/C0A8
Trying to load: pxelinux.cfg/C0A
Trying to load: pxelinux.cfg/C0
Trying to load: pxelinux.cfg/C
Trying to load: pxelinux.cfg/default
Could not find kernel image: linux
boot: 

```

**/var/log/syslog**
```

Apr 26 15:20:35 tavari dhcpd: DHCPDISCOVER from 00:30:1b:b6:cf:b5 via eth0
Apr 26 15:20:35 tavari dhcpd: DHCPOFFER on 192.168.0.10 to 00:30:1b:b6:cf:b5 via eth0
Apr 26 15:20:37 tavari dhcpd: Dynamic and static leases present for 192.168.0.10.
Apr 26 15:20:37 tavari dhcpd: Remove host declaration shuttle or remove 192.168.0.10
Apr 26 15:20:37 tavari dhcpd: from the dynamic address pool for 192.168.0/24
Apr 26 15:20:37 tavari dhcpd: DHCPREQUEST for 192.168.0.10 (192.168.0.1) from 00:30:1b:b6:cf:b5 via eth0
Apr 26 15:20:37 tavari dhcpd: DHCPACK on 192.168.0.10 to 00:30:1b:b6:cf:b5 via eth0
Apr 26 15:20:37 tavari in.tftpd[15785]: tftp: client does not accept options

```

I've done some research, and found some information that says that the message means that the pxelinux.0 loaded, but it failed to find the pxelinux.cfg/default file. But it's there, and it should work fine. And I've verified that it's using the correct pxelinux.0 file.

I've also read that adding the "Next Server" option to the dhcp config fixes it, but as you can see, I already have it. I did the entry right, didn't I?

Does anyone have suggestions on what could be wrong? The guide is a little old, but it's really not much different from gutsy instructions (which I have also tried, and it resulted in the same error message)

---

### Post by draggy on 2008-04-28
no one has any ideas? :(

---

### Post by odnalro on 2008-05-10
I have the same problem.

---

### Post by draggy on 2008-05-14
I fixed mine, in the /tftpboot/pxelinux.cfg/default file, it MUST have the label linux:

```

LABEL linux 
        kernel shuttle/vmlinuz-2.6.22-14-server
        append root=/dev/nfs initrd=shuttle/initrd.img-2.6.22-14-server nfsroot=192.168.0.1:/nfsroot/shuttle ip=dhcp rw

```

and in my dhcpd.conf I changed it to:
```

host pxe_client {
  hardware ethernet xx:xx:xx:xx:xx:xx;
  fixed-address 192.168.0.xxx;
  next-server 192.168.0.1;
  filename "pxelinux.0";
}

```
I don't know if the dhcpd.conf change did anything, but you definitely need to change the label to linux in the default file.

---

### Post by chrismyers on 2011-01-19
Try this how-to. It works on later versions of Ubuntu:
 
[URL="http://ubuntuforums.org/showthread.php?t=1112209"]http://ubuntuforums.org/showthread.php?t=1112209
[/URL]

---

### Post by chrismyers on 2011-01-19
Try this how-to. It was written quite a while ago, but it still works on later versions of Ubuntu:
 
[URL="http://ubuntuforums.org/showthread.php?t=1112209"]http://ubuntuforums.org/showthread.php?t=1112209
[/URL]

---

### Post by chrismyers on 2011-01-19
Try this how-to. It works on later versions of Ubuntu:
 
[URL="http://ubuntuforums.org/showthread.php?t=1112209"]http://ubuntuforums.org/showthread.php?t=1112209
[/URL]

---

