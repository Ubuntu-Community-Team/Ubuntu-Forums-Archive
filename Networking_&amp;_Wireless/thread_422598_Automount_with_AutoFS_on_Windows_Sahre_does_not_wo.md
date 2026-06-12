---
title: "Automount with AutoFS on Windows Sahre does not work"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Lex Luthor on 2007-04-25
Hello, please, semobody help me, I spent all day yesterday and could not make this work,

[LIST=1]
[*]I have a windows file server here, and it contains several shares. I want to automount one of then, and I want it to apear as a local directory. When I enter this directory, it automount the share and show me the files.
[*]The server needs auth to enter the share.
[*]I cannot resolv its NETBIOS name, I connect only by IP address.
[*]IPs and names in this messages are not the real ones.
[*]I can mount it manually, using the command:
 ```
# mount.cifs //10.0.0.1/myshare$ /mnt/winshare -o fstype=cifs,file_mode=0644,dir_mode=0755,credentials=/etc/auto.smb.creds 
```
[/LIST]
 
Inserted the folowing line in /etc/auto.master (all others are commented):

```
/mnt/winshare   /etc/auto.cifs   --ghost
```

I created a /etc/auto.cifs script, got it from Internet (it is very similar to the one provided in the package) and modified some lines for it to get the credentials from a file dinamicaly from the IP or the name asked to mount. So, if I ask to mount /mnt/winshare/10.0.0.1/myshare$ it will look for the credentials for that server in the file /etc/auto.smb.10.0.0.1 :

```

#!/bin/bash

key="$1"

opts="-fstype=cifs,file_mode=0644,dir_mode=0755"
smbclientopts=""

credfile="/etc/auto.smb."`echo $key |awk -F \/ '{print $1}'`

for P in /bin /sbin /usr/bin /usr/sbin
do
        if [ -x $P/smbclient ]
        then
                SMBCLIENT=$P/smbclient
                break
        fi
done

[ -x $SMBCLIENT ] || exit 1

if [ -e "$credfile" ]
then
        opts=$opts",credentials=$credfile"
        smbclientopts="-A "$credfile
else
        smbclientopts="-N"
fi

$SMBCLIENT  $smbclientopts -gNL $key 2>/dev/null| awk -v key="$key" -v opts="$opts" -F'|' -- '
        BEGIN   { ORS=""; first=1 }
        /Disk/  { if (first) { print opts; first=0 }; sub(/ /, "\\ ", $2); print " \\\n\t /" $2, "://" key "/" $2 }
        END     { if (!first) print "\n"; else exit 1 }
        '

```

All right, everything done, I restarted autofs and when I type ls -al /mnt/winshare/10.0.0.1/myshare$ , I get the folowing errors on syslog:

```
Apr 24 17:05:45 localhost kernel: [ 3875.839716]  CIFS VFS: cifs_mount failed w/return code = -6
Apr 24 17:05:45 localhost kernel: [ 3875.841492]  CIFS VFS: cifs_mount failed w/return code = -6
Apr 24 17:05:45 localhost automount[10417]: >> retrying with upper case share name
Apr 24 17:05:45 localhost automount[10417]: >> mount error 6 = No such device or address
Apr 24 17:05:45 localhost automount[10417]: >> Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
Apr 24 17:05:45 localhost automount[10417]: mount(generic): failed to mount //10.0.0.1/myshare$/C (type cifs) on /mnt/windows/10.0.0.1/myshare$/C
Apr 24 17:05:45 localhost kernel: [ 3875.847419]  CIFS VFS: cifs_mount failed w/return code = -5
Apr 24 17:05:45 localhost automount[10417]: >> mount error 5 = Input/output error
Apr 24 17:05:45 localhost automount[10417]: >> Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
Apr 24 17:05:45 localhost automount[10417]: mount(generic): failed to mount //10.0.0.1/myshare$/f (type cifs) on /mnt/windows/10.0.0.1/myshare$/f

```

And a lot of then, for each share the server has.
The result is a list of the share available on the server.

Analising better, I figured out the the script auto.cifs retuns the following output when we ask for 10.0.0.1/myshare$:

```
-fstype=cifs,file_mode=0644,dir_mode=0755,credentials=/etc/auto.smb.10.0.0.1 \
         /E$ ://10.0.0.1/myshare$/E$ \
         /D$ ://10.0.0.1/myshare$/D$ \
         /G$ ://10.0.0.1/myshare$/G$ \
         /M$ ://10.0.0.1/myshare$/M$ \
         /myshare$ ://10.0.0.1/myshare$/myshare$ \
         /F$ ://10.0.0.1/myshare$/F$ \
         /ADMIN$ ://10.0.0.1/myshare$/ADMIN$ \
         /C$ ://10.0.0.1/myshare$/C$ \

```

that are all the shares that the server has. 
This line must be passed to autofs that must pass this to mount.cifs or else. But I don't know if it is correct.

I've already tried to put only the line on auto.cifs:

```
winshare         -fstype=cifs,dmask=0700,fmask=0700,credentials=/etc/auto.smb.10.0.0.1 ://10.0.0.1/myshare

```

And also did not work. I get the folowing error on syslog:

```
automount[12157]: lookup(program): lookup for 10.0.0.1 failed
Apr 24 17:39:32 localhost automount[12157]: failed to mount /mnt/winshare/10.0.0.1

```

Any HELP ... PLEASE !!!!!!!!!

---

### Post by Lex Luthor on 2007-04-25
Oh, I forgot to say that I am using Ubuntu 7.04.
I have just installed it from CD.
Thanks....

---

