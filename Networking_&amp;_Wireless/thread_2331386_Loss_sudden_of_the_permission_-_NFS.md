---
title: "Loss sudden of the permission - NFS"
date: 2016-07-21
forum: Networking &amp; Wireless
---

### Post by sed_faster on 2016-07-21
hello everyone,

I use Lubuntu 16.04 LTS on my laptop and I need mount nfs folder through this command:

```

sudo mount -t nfs 192.184.3.87:/media/pi /home/user/Documents/sandbox/usb

```

for access my files which they are being served from Raspberry PI, with SO Raspbian. 
Was running fine until when I need restart my laptop and execute this command, for mount drives on my pc, and I tried access the folders, through File Manager PCManFM I got it access the folder usb and selected the two folders which mounted but when I tried access on of them I receive this message "Error opening directory '/home/user/Documents/sandbox/usb1/folderone': Operation not permitted'
I tried, through terminal, which root and I got it access the folderone and write in inside.

I checked the id, and the id user of the folderone, on Raspberry pi, and my normal user they are the same!
What could be occur for I lost the rights on this folders?

Sorry about my english, If you need the another explanation please tell me! Thanks

---

### Post by SeijiSensei on 2016-07-22
When you say you  checked the "id" are you talking about your textual username or your numerical ID?  Use "id -n" on both machines to see if the "UIDs" match.  If not, adjust one or the other to have matching user and group IDs.

NFS only cares about numerical IDs, not their associated usernames.

---

### Post by sed_faster on 2016-07-22
Hello,
I was talking about this id:
```

eno@userpc:~$ id eno
uid=1000(eno) gid=1000(eno) groups=1000(eno),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),121(sambashare)

pi@pdpci:~ $ id pi
uid=1000(pi) gid=1000(pi) groups=1000(pi),4(adm),20(dialout),24(cdrom),27(sudo),29(audio),44(video),46(plugdev),60(games),100(users),101(input),108(netdev),999(spi),998(i2c),997(gpio)

```

When I tried execute this command I received this error:
```

eno@userpc:~$ id eno -n
id: cannot print only names or real IDs in default format

```

---

### Post by papibe on 2016-07-22
Hi Edgar_Oliveira.

The -n options needs to be use with other option:
```
 -n, --name
              print a name instead of a number, [COLOR="#FF0000"]**for -ugG**[/COLOR]
```
Thus:
```
$ id user -n
id: cannot print only names or real IDs in default format

$ id user -n -u
user

```
Does that help? Let us know how it goes.
Regards.

---

### Post by SeijiSensei on 2016-07-22
Also, since you're mounting the share as root, why not use a mount point that root owns?  All my NFS shares reside under /media with root-owned mount points.  The mounted directories are owned by root on the server as well.

Try creating a mount point on the client like "/media/pi" as root with sudo and mounting the share there.  Any better?

---

### Post by sed_faster on 2016-07-22
The main question is why left works!? Because I don't change anything!
But ok, let's see permissions of this folders:

```

drwxr-xr-x   4 root root      4096 Jun  3 18:10 home
drwx------ 44 user  user  12288 Jul 22 08:48 user
drwxr-xr-x  5 user  user     4096 Jun  5 13:04 Documents
drwxrwxr-x  9 user user 12288 Jul 18 09:39 sandbox
drwxr-xr-x  4 user user   4096 Jul 21 14:39 usb

```

But when I run command
```

sudo mount -t nfs 192.184.3.87:/media/pi /home/user/Documents/sandbox/usb

```
the owner change to root:

```

drwxr-xr-x  4 root root   4096 Jul 21 14:39 usb

```

But the owner inside the usb is user:
```

drwxr-xr-x  4 user  user   4096 Jul 19 14:56 folder 1
drwxr-xr-x 16 user  user   4096 Jul 19 14:55 folder 2

```

Why when I tried to get inside the folder 1 or folder 2, with the same user I receive the message "Error opening directory '/home/user/Documents/sandbox/usb1/folderone': Operation not permitted'"

I tried your suggested but I received the same message "Error opening directory '/media/pi/folder1': Operation not permitted
The structured the directories are:
```

drwxr-xr-x   4 root root      4096 Jul 22 20:51 media
drwxr-xr-x   4 root root 4096 Jul 21 14:39 pi
drwxr-xr-x  4 user  user   4096 Jul 19 14:56 folder 1
drwxr-xr-x 16 user  user   4096 Jul 19 14:55 folder 2

```

Thanks all

---

### Post by sed_faster on 2016-07-22
Hooo, I can't understand this! I tried, through terminal and with privileges of root I got it the folder one, which interdicts through File manager, through normal user! When I run "cd folder 1", which root, this drive was mounted and, even if I logout as root, I can get in folder 1 and write and read files inside them! 

This behaviour is totally newbie for me! :/

---

### Post by sed_faster on 2016-07-24
Hello,

Any more suggestion about this problem?
Thanks

---

