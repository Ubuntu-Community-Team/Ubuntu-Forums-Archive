---
title: "systemd-resolved.service is not loaded properly: Exec format error."
date: 2019-10-18
forum: Networking &amp; Wireless
---

### Post by cfotland on 2019-10-18
Hi!

I have a headless Ubuntu Server with some DNS trouble. After some troubeshooting to find out why it did not have an internet connection I found that starting systemd-resolved.service fixed the issue.
I didn't have time to figure out how to start it automatically at boot so I've been doing that manually via ssh for now.
This time it won't start the service;

```
$ sudo systemctl start systemd-resolved.service
Failed to start systemd-resolved.service: Unit systemd-resolved.service is not loaded properly: Exec format error.
See system logs and 'systemctl status systemd-resolved.service' for details.
$ systemctl status systemd-resolved.service
&#9679; systemd-resolved.service - dns
   Loaded: error (Reason: Exec format error)
   Active: inactive (dead)

```

Some advice on how to troubleshoot would be great!

System info:

```
$ uname -v
#74-Ubuntu SMP Tue Sep 17 17:06:04 UTC 2019
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.3 LTS"

```

---

### Post by SeijiSensei on 2019-10-18
What do you see in /var/log/syslog?  That's where systemd logs everything.  

An "Exec format error" usually means the executable program is somehow bad.  Might I suggest reinstalling systemd-resolved?

```

sudo apt remove --purge systemd-resolved
sudo apt install systemd-resolved

```

To tell systemd to run this program at boot, run the command
```
sudo systemctl enable systemd-resolved
```

See: [https://linoxide.com/linux-how-to/enable-disable-services-ubuntu-systemd-upstart/](https://linoxide.com/linux-how-to/enable-disable-services-ubuntu-systemd-upstart/)

---

### Post by cfotland on 2019-10-19
> **SeijiSensei said:**
> What do you see in /var/log/syslog?  That's where systemd logs everything.
I tried tailing it but nothing happens. I can see other events, like me logging in to ssh, but nothing about systemd-resolved. "cat /var/log/syslog | grep resolved" gives nothing.

> **SeijiSensei said:**
> An "Exec format error" usually means the executable program is somehow bad.  Might I suggest reinstalling systemd-resolved?

```

sudo apt remove --purge systemd-resolved
sudo apt install systemd-resolved

```

Ok, I tried this but it says that systemd-resolved is not installed;
```

~$ sudo apt remove --purge systemd-resolved
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package systemd-resolved
~$ sudo apt install systemd-resolved
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package systemd-resolved
~$ sudo apt update
Err:1 http://download.webmin.com/download/repository sarge InRelease
  Temporary failure resolving 'download.webmin.com'

...

```

Is it possible to use apt without internet? I am running Linux Mint on another machine. Can I download the files needed there and copy them over to my server?

---

### Post by cfotland on 2019-10-19
Ok, so I've been tinkering with this a bit and I found a solution.

Being the linux-noob that I am, I might be doing this a bit cumbersome.
I tried to figure out if I could somehow download the packages on another pc and copy them over, but I didn't find what I needed. I found something called openvpn-systemd-resolved [https://packages.ubuntu.com/bionic/openvpn-systemd-resolved](https://packages.ubuntu.com/bionic/openvpn-systemd-resolved), but I'm not sure if it is the same as systemd-resolved. Also, from what I understand I would have to download all dependecies manually to transfer over to the server and install with dpkg, so I tried something else.

I downloaded the ubuntu server 18.04 LTS image from canonical and installed it in a virtualbox vm.
I could find from "sudo systemctl status systemd-resolved.service" which file was loaded;
```

~$ sudo systemctl status systemd-resolved.service
&#9679; systemd-resolved.service - Network Name Resolution
   Loaded: loaded (**/lib/systemd/system/systemd-resolved.service**; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-10-19 20:54:06 CEST; 14min ago

...

```

I made a backup of this file on my server and copied over the one from the vm.
```
~$ ls -la /lib/systemd/system/systemd-resolved*
-rw-r--r-- 1 root root 1687 Oct 19 20:48 /lib/systemd/system/systemd-resolved.service
-rw-r--r-- 1 root root  131 Oct 18 23:53 /lib/systemd/system/systemd-resolved.service_backup
```

After a reboot it worked like charm.
I notice that the file sizes are quite different, the old one is quite small compared to the new one.
Any insight here would be great.

Could I have done this an easier way? Should I have done it differently or is it ok to replace this service-file like I did?

---

### Post by cfotland on 2019-10-19
I figured out why the file was smaller. I didn't know that those  files were plain text-files, but now I had a look to see the difference and  that led me to realise what the problem was.
I use Webmin for  administrating the server, and since the service didn't start at boot, I  tried enabling it in "Bootup and shutdown".
It wasn't in the list (still isn't) so I tried "Create new systemd service". That replaced the service-file with a new one;

```

[Unit]
Description=dns

[Service]
ExecStart=sudo systemctl start systemd-resolved.service ; 

[Install]
WantedBy=multi-user.target


```

> **SeijiSensei said:**
> To tell systemd to run this program at boot, run the command
     Code:

     sudo systemctl enable systemd-resolved


I did that now, instead of using Webmin. Thank you very much :-)

```
~$ sudo systemctl enable systemd-resolved.service
Created symlink /etc/systemd/system/dbus-org.freedesktop.resolve1.service &#8594; /lib/systemd/system/systemd-resolved.service.
```

---

