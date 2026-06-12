---
title: "fstab not automaounting"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by CuBone on 2007-03-19
I'm trying to automount my mediaservers networkshare but it won't work. This is what my fstab looks like (password to windowsaccount edited).

```
//192.168.10.1/shared /home/mythtv/server cifs auto,rw,user=cubone,pass=*********,uid=mythtv,cubone 0 0

```

The problem is that it won't automount at boot. If I run ```
sudo mount -a
``` it mounts fine. Is there a way to automount the networkshares?

First I thougth I'd run a script with sudo automount -a in the bootprocess but then I'd have to enter my password every time.

---

### Post by H3g3m0n on 2007-03-19
Firstly, sudo won't ask for a password if you already a root user, all boot scripts generally run as root. Secondly since they are already root you wouldn't actually need sudo at all and 'mount -a' would do fine.

Try looking in the log files for any messages about mounting  'dmesg | grep cifs' also try smb, samba, mount as other alternatives to grep. And /var/log/samba

Its possible that your network interface isn't being brought up before the samba or obtaining an ip etc..., might be worth making sure that the interface works befoure xorg boots but stopping xorg from running.

You might also like to store the password and user name in a separate file, normally '/etc/smbcredentials', with permissions so only root can read it, this is done because the /etc/fstab file can be read by any user so storing passwords in there is a security risk.
```
username=yourusername
password=yourpass
```

For referance my fstab has:
```
//hextor/storage /mnt/storage cifs      credentials=/etc/smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777     0 0
```

That automounts fine for me.

If it works when mount -a is done then there isn't a configure problem, probably just a network race condition problem. You might need to make a script with "sleep 3; mount -a" and launch it in the background at boot with &

---

### Post by CuBone on 2007-03-19
Working now. Added a mount -a command at the of the startsequence. 
Thanx for the password suggestion.

---

