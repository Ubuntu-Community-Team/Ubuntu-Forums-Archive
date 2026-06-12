---
title: "SAMBA won't reinstall"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by dchurch on 2008-05-28
Hi all,

I was following an example of how to set up samba shares in Ubuntu (for my XBMC xbox), and it really cocked things up.

It suggested that I do: sudo apt-get remove samba --purge

and then start again.

Did that, but when I went to reinstall samba I get the following:

```

The following NEW packages will be installed
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4192kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com hardy/main samba 3.0.28a-1ubuntu4 [4192kB]
Fetched 4192kB in 5s (773kB/s)  
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 104615 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.28a-1ubuntu4_amd64.deb) ...
Setting up samba (3.0.28a-1ubuntu4) ...
Generating /etc/default/samba...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am now at a complete loss, does anyone have any idea what has happened and how to fix this?

Thanks in advance,

dchurch.

---

### Post by lurch89 on 2008-06-14
I'm having the exact same problem, only I'm on i386 Ubuntu 8.04 Server. HELP!!!

---

