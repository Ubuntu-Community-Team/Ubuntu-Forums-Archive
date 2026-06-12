---
title: "console-kit-daemon 97% CPU from rsync ssh .sh script"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by jeffk on 2008-11-22
Recently a client bash script with a single rsync via ssh command set the server's console-kit-daemon into a very high CPU utilization:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3985 root      20   0 27596  12m 1624 R 93.4  2.5   1984:53 console-kit-daemon
    4 root      15  -5     0    0    0 S  0.3  0.0   0:30.39 ksoftirqd/0
 3816 syslog    20   0  2012  712  552 S  0.3  0.1   0:13.68 syslogd
 4165 root      15  -5     0    0    0 S  0.3  0.0   0:22.17 nfsd
 4223 haldaemo  20   0 14864  12m 3200 S  0.3  2.5   2:07.57 hald
20177 myuser    20   0 15860 5300  992 S  0.3  1.0   0:13.42 sshd
    1 root      20   0  3056 1888  564 S  0.0  0.4   0:07.68 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.08 watchdog/0
```
The user runs the following script when they want to archive their entire home directory to the server:

```
myuser@workstation1:~$ cat rsync_to_server1.sh 
rsync --delete --exclude=.dbus/ --exclude=.rnd --exclude=.mozilla/firefox/*/Cache --exclude=.mozilla/firefox/*/urlclassifier3.sqlite -avPe ssh /home/myuser/ server1:
```
This runs well as a bash command, but since the Ubuntu-8.10 upgrades has been hit-or-miss when run as ./rsync_to_server1.sh. The script takes a long time before displaying any typical rsync output.

Is ConsoleKit and/or PolicyKit intervening in rsync over ssh activity?

---

### Post by NickD-NLUG on 2008-12-21
> **jeffk said:**
> Recently a client bash script with a single rsync via ssh command set the server's console-kit-daemon into a very high CPU utilization:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3985 root      20   0 27596  12m 1624 R 93.4  2.5   1984:53 console-kit-daemon
    4 root      15  -5     0    0    0 S  0.3  0.0   0:30.39 ksoftirqd/0
 3816 syslog    20   0  2012  712  552 S  0.3  0.1   0:13.68 syslogd
 4165 root      15  -5     0    0    0 S  0.3  0.0   0:22.17 nfsd
 4223 haldaemo  20   0 14864  12m 3200 S  0.3  2.5   2:07.57 hald
20177 myuser    20   0 15860 5300  992 S  0.3  1.0   0:13.42 sshd
    1 root      20   0  3056 1888  564 S  0.0  0.4   0:07.68 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.08 watchdog/0
```
The user runs the following script when they want to archive their entire home directory to the server:

```
myuser@workstation1:~$ cat rsync_to_server1.sh 
rsync --delete --exclude=.dbus/ --exclude=.rnd --exclude=.mozilla/firefox/*/Cache --exclude=.mozilla/firefox/*/urlclassifier3.sqlite -avPe ssh /home/myuser/ server1:
```
This runs well as a bash command, but since the Ubuntu-8.10 upgrades has been hit-or-miss when run as ./rsync_to_server1.sh. The script takes a long time before displaying any typical rsync output.

Is ConsoleKit and/or PolicyKit intervening in rsync over ssh activity?

Did you get anywhere with this?

---

### Post by jeffk on 2008-12-22
No, unfortunately. It has happened on a few occasions since the original post. I can only guess from the timing of these incdidents that it is related to users running a bash script with an rsync -e ssh command by double-clicking the executable script. Most of the time it works (over OpenVPN), but sometimes it fails. Whether this is a cause or symptom I have no idea yet. 

The console-kit-daemon process is killable, so I can usually avoid a server reboot.

I would like to have had the option (or at least the documentation) to skip things like this (console-kit) on a server distro. I can see some usefullness for desktop permissions management, but AFAICT it's not adding any benefit to the 8.10 server for me.

---

### Post by iponeverything on 2008-12-22
maybe attach strace to console-kit-daemon when going bonkers. Though, you might want have another window open on the same machine with a "killall strace" ready, since it probably won't respond to Ctl-c when it chewing so fast.

---

### Post by NickD-NLUG on 2008-12-22
> **jeffk said:**
> No, unfortunately. It has happened on a few occasions since the original post. I can only guess from the timing of these incdidents that it is related to users running a bash script with an rsync -e ssh command by double-clicking the executable script. Most of the time it works (over OpenVPN), but sometimes it fails. Whether this is a cause or symptom I have no idea yet. 

The console-kit-daemon process is killable, so I can usually avoid a server reboot.


Inspired by this, I've put it down to some kind of issue with logging into the host many times, which I tend to do remotely...

[https://bugs.freedesktop.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=ConsoleKit&content=](https://bugs.freedesktop.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=ConsoleKit&content=)

...it is a desktop, but I treat it like a server too :)


> **jeffk said:**
> I would like to have had the option (or at least the documentation) to skip things like this (console-kit) on a server distro. I can see some usefullness for desktop permissions management, but AFAICT it's not adding any benefit to the 8.10 server for me.

Agreed.  I did try "apt-get remove consolekit", and apt-get presented me with a list of 135 packages it was going to remove.  Before I start googling for information, any suggestions on how I can submit this as a feature request?

---

### Post by jeffk on 2008-12-25
Good find. The bugfix looks like a one-line fix. [https://bugs.freedesktop.org/show_bug.cgi?id=18330](https://bugs.freedesktop.org/show_bug.cgi?id=18330)

Since it's reproducible, I hope someone with commit access gets inspired to pull the upstream packages in.

---

