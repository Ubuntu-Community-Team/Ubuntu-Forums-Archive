---
title: "UPnP client fails to to be installed/removed"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by Supersaiyan.IV on 2006-12-18
This is network related, and i thought some people setting up their UPnP in Ubutu Edgy might benefit if it's posted here.

I'm starting this thread on behalf of a handful of people that don't really know how to deal with this short of reinstalling Ubuntu. This has also been discussed in the following thread:
[HTML]http://www.ubuntuforums.org/showthread.php?t=311109&highlight=linux-igd[/HTML]

The problem lies in the upnp client, linux-igd, which upon installation (from synaptic) returns an error, and the same upon an attempt to uninstall/reinstall afterwards. 
Which means that all of the sudden there is an erroneous package which cannot be removed/reinstalled.  There is an error at the end of each Synaptic update, or installation of a (or any) package.

Here are the error logs:

> 
ote:
Selecting previously deselected package linux-igd.
(Reading database ... 99412 files and directories currently installed.)
Preparing to replace linux-igd 0.cvs20060201-1 (using .../linux-igd_0.cvs20060201-1_i386.deb) External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/linux-igd_0.cvs20060201-1_i386.deb (--unpack):
subprocess new pre-removal script returned error exit status 1
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "start" failed.
dpkg: error while cleaning up:
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
/var/cache/apt/archives/linux-igd_0.cvs20060201-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Maybe this is a manifest of incompatibility, CRC inredundancy, however there has to be an alternate (manual) way to remove this package without harm. It's just plain annoying to receive errors from an application you don't even want to have on your system.

A few words from the thread mentioned above:

[quote=spanella47]

linux-igd_0.cvs20060201-1_i386.deb
from the universe repo isn't installing correctly but asks to be reinstalled before it can be removed. an endless cycle. tried forcing the removal with dpkg but won't let me, is there another way to remove this package.

the other annoyance is that it gives that error every time you try to install anything. complete removal would be nice.
[/quote]

My intuition tells me the issue is either CRC, or incompatibility of dependencies. I welcome all suggestions as to how to get rid of this application.

 Thanx in advance.

peace

---

### Post by FeraTech on 2006-12-26
This is how to fix your problem:

```
sudo gedit /var/lib/dpkg/status
```

Find linux-igd

Write down all the file locations.
Should look something like:
/etc/upnpdb

Delete the entire entry from /var/lib/dpkg/status

Now:
Manually delete all the files you wrote down listed in the /var/lib/dpkg/status
```
sudo rm -r "directory name"
```
```
sudo rm "file name"
```

---

### Post by Peturrr on 2007-02-07
The thing that is causing the problem is the standard /etc/default/upnp configuration file.

If you edit that file and remove the comment sign (#) before the lines ext interface and internal interface it wil work.

First you'll need to run ```
sudo /etc/init.d/upnp start
```
After that you will be able to remove linux-igd.

---

### Post by Mago on 2007-03-12
In my system this was

```
sudo kate /etc/default/upnpd
```

or nano/gedit/kwrite etc

```
# Defaults for upnpd initscript
# sourced by /etc/init.d/upnpd
# installed at /etc/default/upnpd by the maintainer scripts

# External interface name
EXT_IFACE=ppp0

# Internal interface name
INT_IFACE=eth0

```

save, exit and

```
sudo /etc/init.d/upnpd start
```

then apt-get removed it just fine

---

