---
title: "File Sharing setup between Ubuntu and Windows XP"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Kusho on 2008-11-15
I just want to know how to setup file sharing on Ubuntu so I can see files that are on my XP boxes.  (and how to set it up to see files on Vista boxes will probally be needed in the future.  I'm probally just not searching well enough, but I keep reading thru walk thru after walkthru..  Hearing about Samba, being told I need it, i dont...  etc..  etc...

a general point in the right direction for someone fairly new to Ubuntu would be greatly appreciated.

thanks.

tom

---

### Post by Kusho on 2008-11-15
it's sad people like [http://www.pcmech.com/article/ubuntu-810-and-windows-xp-file-sharing-how-to/](http://www.pcmech.com/article/ubuntu-810-and-windows-xp-file-sharing-how-to/) make money on this stuff...

would think simple networking is something MOST people want to set up.

or maybe I'm too dense.  anyway didn't pay this guy...  not finding good answers thou.  grrr.

---

### Post by graysky on 2008-11-15
**To mount windows shares on your LINUX box**

To successfully run LINUX as a newbie (like me) google is your best friend.  Helpful and kind people in these and others forums are too.

See [this post](http://ubuntuforums.org/showthread.php?t=288534) for connecting to Windows shares on LINIX.

As an example, here is line in my /etc/fstab that connected to a WinXP share:

```
//192.168.1.2/share-ro /mnt/share  cifs    credentials=/root/.smbpasswd,iocharset=utf8,file_mode=0500,dir_mode=0500,uid=100,gid=102 0 0
```

Read that post to learn about a credentials file to hide your username/password.

**To setup shares on the LINUX side**
From memory on my Debian lenny box:

```
# apt-get install samba
```

That should bring down the needed samba packages.  

Now to make a username/password for samba to use:

```
# smbpasswd -a USERNAME
```

Where USERNAME is the username you want to use your share; it does NOT need to be the same as your LINUX users!

You'll now need a /etc/samba/smb.conf that sets up the shares.

```
[global]
        load printers = yes
        guest account = nobody
        name resolve order = lmhosts host wins bcast
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
#       socket options = TCP_NODELAY
        socket options = IPTOS_LOWDELAY TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
        preserve case = yes
        obey pam restrictions = yes
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        dns proxy = no
        printing = bsd
        server string = Palladium
        invalid users = root
        unix password sync = false
        workgroup = Workgroup
        syslog only = no
        os level = 20
        printcap name = /etc/printcap
        syslog = 0;
        security = user
        panic action = /usr/share/samba/panic-action %d
        short preserve case = yes
        max log size = 1000

#======================= Share Definitions =======================

[stuff]
        comment = stuff
        writeable = yes
        valid users = titty
        path = /stuff
```

Now restart samba to read the config:

```
# /etc/init.d/samba restart
```

To connect from windows, simply type the following into your explorer window (or map a drive):

```
\\IP.OF.SAMBA.SERVER
```

It'll ask for the username/password you defined.  

If you want to have samba startup at boot... I dunno about ubuntu, but on Debian:

```
# update-rc.d samba defaults
```

---

