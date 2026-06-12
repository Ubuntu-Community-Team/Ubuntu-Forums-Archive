---
title: "Samba install fails - not K09samba"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by vanalljc on 2007-05-23
Hello,
I'm hoping someone can help with my attempts to install samba.  The install fails at the same point each time I try.  The sources I've read so far all seem to come back to a broken symlink, specifically K09samba.  

I am new to trying to set up a server using Ubuntu, and so have limited troubleshooting knowledge.  What I've tried so far

When I log in to my system, I see the following.

```
Linux BMInet 2.6.15-26-server #1 SMP Fri Sep 8 21:00:37 UTC 2006 i686 GNU/Linux
```

This is what I see when trying to install samba...

```
root@BMInet:/home/jeff# apt-get install samba
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.3) ...
 * Starting Samba daemons...
   ...fail!
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I found several resources that seemed attribute this error to a problem with a broken symlink, including ...

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/9208]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/9208")

> Matt Zimmerman said on 2004-10-19:

The samba package does not, and has never, created an /etc/rc2.d/K09samba
symlink. The bug is in some other package, which creates this faulty link.
Please send the output from:

ls -l /etc/rc?.d/*samba
ls -l /etc/init.d/samba
dpkg -l

Running the commands, I get the following outputs

```
root@BMInet:/home/jeff# ls -l /etc/rc?.d/*samba
lrwxrwxrwx 1 root root 15 2007-05-22 15:49 /etc/rc0.d/K19samba -> ../init.d/samba
lrwxrwxrwx 1 root root 15 2007-05-22 15:49 /etc/rc1.d/K19samba -> ../init.d/samba
lrwxrwxrwx 1 root root 15 2007-05-22 15:49 /etc/rc2.d/S20samba -> ../init.d/samba
lrwxrwxrwx 1 root root 15 2007-05-22 15:49 /etc/rc3.d/S20samba -> ../init.d/samba
lrwxrwxrwx 1 root root 15 2007-05-22 15:49 /etc/rc4.d/S20samba -> ../init.d/samba
lrwxrwxrwx 1 root root 15 2007-05-22 15:49 /etc/rc5.d/S20samba -> ../init.d/samba
lrwxrwxrwx 1 root root 15 2007-05-22 15:49 /etc/rc6.d/K19samba -> ../init.d/samba
```

If the target path```
 ../init.d/samba
``` is the same as ```
/etc/init.d/samba
``` then this is all fine.  Is it?

The second command returns the following

```
root@BMInet:/home/jeff# ls -l /etc/init.d/samba
-rwxr-xr-x 1 root root 2033 2007-05-15 18:46 /etc/init.d/samba
```

The various resources I've read all seem to point to a symlink "K09samba" that points to /samba as the problem that results, at this point I'm not seeing anything that looks like that situation.

These are the packages I've attempted to install

```
root@BMInet:/home/jeff# dpkg -l
iF  samba          3.0.22-1ubuntu a LanManager-like file and printer server fo
ii  samba-common   3.0.22-1ubuntu Samba common files used by both the server a
ii  samba-doc      3.0.22-1ubuntu Samba documentation
ii  smbclient      3.0.22-1ubuntu a LanManager-like simple client for Unix
ii  smbldap-tools  0.9.2-3        Scripts to manage Unix and Samba accounts
```

I tried removing all of the symlinks following the instructions in [http://ubuntuforums.org/showthread.php?t=446513&page=2]("http://ubuntuforums.org/showthread.php?t=446513&page=2")


```
root@BMInet:/home/jeff# update-rc.d -f samba remove
 Removing any system startup links for /etc/init.d/samba ...
   /etc/rc0.d/K19samba
   /etc/rc1.d/K19samba
   /etc/rc2.d/S20samba
   /etc/rc3.d/S20samba
   /etc/rc4.d/S20samba
   /etc/rc5.d/S20samba
   /etc/rc6.d/K19samba
```

and then trying to re-install, with the same results

I've also tried an uninstall and clean

```
root@BMInet:/home/jeff# apt-get remove --purge samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7258kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 84753 files and directories currently installed.)
Removing samba ...
 * Stopping Samba daemons...
   ...done.
Purging configuration files for samba ...
Removing configuration file /etc/default/samba...
Removing configuration file /etc/default/samba...
root@BMInet:/home/jeff# apt-get clean
```

attempts to reinstall met with the same result.

```
Setting up samba (3.0.22-1ubuntu3.3) ...
 * Starting Samba daemons...
   ...fail!
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

If anyone has seen this before, or can point me in the direction of troubleshooting resources or techniques I would be most appreciative.
Thanks,
Jeff

---

### Post by vanalljc on 2007-05-29
I'm not sure why, but it appears that some quirk in the smb.conf file was giving the error.  The line

```
* Stopping Samba daemons...
   ...done.

```

made me think, and so I ran
```
ps -ef
``` and saw

```
/usr/sbin/smbd
```

so, forging blindly ahead, I edited the smb.conf file to 

```
#=================================================
# BMInet Samba config file
# Last updated 29 May 2007
# Step #2
# This works, no user login, just a shared network folder
#=================================================


[global]
        guest account = nobody
        workgroup = KING_BMI
        security = share
        writable = yes

[shared]
        comment = shared drive
        path = /shared
        read only = no
        public = yes
        writable = yes
        create mask = 0775
        directory mask = 0775
```

and now I can see, read, write etc to the samba share.  I don't understand why Samba seemed to fail to install, or why it started up when _seeming_ to report otherwise, but it's working, so I'm not going to complain.

I know lots of people looked at my original post, here's hoping that this follow-up helps someone.

The "only" thing left to do is figure out how to make Samba dance the way I want it to.

---

