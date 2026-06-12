---
title: "Question about /var/run"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-06
Happy Friday :popcorn:

What should the permissions settings be for the /var/run folder and the folders underneath?

I think I changed them and don't know exactly what they should be.

thanks and have a SUPER weekend !

---

### Post by Joeb454 on 2009-03-06
```
drwxr-xr-x 13 root root   400 Mar  5 02:41 run
```

That's what they are on my server :)

---

### Post by Elfy on 2009-03-06
my desktop has
```
drwxr-xr-x 16 root       root        660 2009-03-06 18:00 .
drwxr-xr-x 15 root       root       4096 2009-02-04 05:25 ..
srw-rw-rw-  1 root       root          0 2009-03-06 07:50 acpid.socket
-rw-r--r--  1 root       root          5 2009-03-06 07:50 atd.pid
drwxr-xr-x  2 avahi      avahi        80 2009-03-06 07:50 avahi-daemon
drwxr-xr-x  2 root       root         60 2009-03-06 18:00 console
drwxr-xr-x  2 root       root         60 2009-03-06 18:00 ConsoleKit
-rw-r--r--  1 root       root          5 2009-03-06 07:50 console-kit-daemon.pid
-rw-r--r--  1 root       root          5 2009-03-06 07:50 crond.pid
----------  1 root       root          0 2009-03-06 07:50 crond.reboot
drwxr-xr-x  3 root       lp          120 2009-03-06 07:50 cups
drwxr-xr-x  2 messagebus messagebus   80 2009-03-06 07:50 dbus
-rw-r--r--  1 root       root          5 2009-03-06 17:28 dhclient-eth0.pid
-rw-r--r--  1 root       root          5 2009-03-06 07:50 gdm.pid
srw-rw-rw-  1 root       root          0 2009-03-06 07:50 gdm_socket
drwxr-xr-x  2 haldaemon  haldaemon    80 2009-03-06 18:00 hald
drwxr-xr-x  2 klog       klog        100 2009-03-06 07:50 klogd
-rw-r--r--  1 root       root         62 2009-03-06 18:00 motd
drwxr-xr-x  2 root       root         60 2009-03-06 07:50 network
drwxr-xr-x  2 root       root         60 2009-03-06 07:50 NetworkManager
-rw-r--r--  1 root       root       1764 2009-03-06 07:50 nm-dhclient-eth0.conf
drwxrwx---  2 root       polkituser   40 2009-03-06 07:50 PolicyKit
drwxr-xr-x  2 root       root         40 2009-03-06 07:50 pppconfig
-rw-r--r--  1 root       root          0 2009-03-06 07:46 .ramfs
drwxrwxr-x  2 root       utmp         40 2009-03-06 07:50 screen
-rw-r--r--  1 root       root          0 2009-03-06 07:46 sendsigs.omit
drwx------  3 root       kevin        60 2009-03-06 08:04 sudo
-rw-r--r--  1 root       root          5 2009-03-06 07:50 syslogd.pid
-rw-r--r--  1 root       root          4 2009-03-06 07:50 system-tools-backends.pid
drwxr-xr-x  2 root       root         80 2009-03-06 08:00 update-motd
-rw-r--r--  1 root       root         49 2009-03-06 18:00 update-motd.lastrun
-rw-r--r--  1 root       root         62 2009-03-06 17:50 updates-available
-rw-rw-r--  1 root       utmp       4224 2009-03-06 18:00 utmp
```

---

### Post by mistypotato on 2009-03-06
thanks for taking the time to assist :KS:KS:KS:KS:KS

---

### Post by kpatz on 2009-03-06
By default Ubuntu mounts a tmpfs on /var/run, meaning everything in there disappears on a reboot.  So you don't have to worry about messing up the permissions on /var/run or /var/lock either.  Just reboot and they'll be back to what they should be...

---

### Post by mistypotato on 2009-03-06
oh yeah....I remmeber that now :)

I'm trying to do a MondoArchive backup and it gets "almost" done, like down to the last disc and then I get a Fatal Error saying that there is not enough room on the device.....

**[COLOR="Red"]afio: "/var/run/mondo.tmp.CMlpfZ/tmpfs/201.afio.bz2" [offset 4m+256k+0]: No space left on device[/COLOR]**

And since I can't see any Mondo temp files there, I assume it never was able to write the files it wanted to there and thus the fatal error.

But the drive has 137GB and only 4 used so I thought it was a permissions thing .

Now I'm in trouble again :(

---

### Post by Elfy on 2009-03-06
Does the /partition have 137Gb though?

```
df -h
```

Will show the mountpoints and available space

---

### Post by mistypotato on 2009-03-06
hmmmm.....

you may be on to something there.....

Here's the result of df -h (done at /var )

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             142G  8.5G  127G   7% /
tmpfs                     1.5G     0  1.5G   0% /lib/init/rw
**[COLOR="Blue"]varrun                    1.5G  196K  [COLOR="Red"]1.5G[/COLOR]   1% /var/run[/COLOR]**
varlock                  1.5G     0  1.5G   0% /var/lock
udev                     1.5G  2.9M  1.5G   1% /dev
tmpfs                    1.5G  464K  1.5G   1% /dev/shm
lrm                        1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6             942M   41M  854M   5% /boot

Can I allocate more space to /var/run ?

---

### Post by kpatz on 2009-03-06
> **mistypotato said:**
> Can I allocate more space to /var/run ?The default size of tmpfs is 1/2 your total memory.  You can increase it with a size= parameter in the mount options (fstab).  But since tmpfs uses RAM/swap space, it may be better off to set MondoArchive to put its temp files somewhere else, like /tmp?

---

