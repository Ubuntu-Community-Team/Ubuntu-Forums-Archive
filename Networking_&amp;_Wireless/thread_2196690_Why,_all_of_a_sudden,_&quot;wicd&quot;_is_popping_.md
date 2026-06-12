---
title: "Why, all of a sudden, &quot;wicd&quot; is popping up errors Ubuntu 13.10 (what is it anyway?)"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by Jim_Granite on 2013-12-30
I have no idea what 'wicd' is doing on my system, nor, 'till today, had I ever heard of wicd, and, after googling, I see it's a secondary networking system that I didn't (knowingly) install on my Ubuntu 13.10 laptop.
My laptop has been working for a few months, always wirelessly, yet, today, when booting, all of a sudden, I get a series of wicd errors.
I have googled for what those errors are - but - the real question here is what is WICD doing on my system in the first place?

Isn't it optional? 
Did I add it somehow?
Or is it a default of Ubuntu 13.10?
[ATTACH=CONFIG]249042[/ATTACH]
ERRORS (in order):
1. Wicd needs to access your computer's network cards. Password: 
2. Could not connect to wicd's D-Bus interface. Check the wicd log for error messages.
2. The wicd daemon has shut down. The UI will not function properly unti it is restarted.

Note: There is no wicd log that I can find, and, I am networking on Ubuntu 13.10 to send this message, even with all those wicd errors.
```

$ locate wicd|grep log
=> /usr/lib/python2.7/dist-packages/wicd/logfile.py
=>/usr/lib/python2.7/dist-packages/wicd/logfile.pyc
=>/usr/lib/python2.7/dist-packages/wicd/logfile.pyo
=>/usr/share/doc/python-wicd/changelog.Debian.gz
=>/usr/share/doc/wicd-daemon/changelog.Debian.gz
=>/usr/share/doc/wicd-gtk/changelog.Debian.gz
=>/usr/share/pyshared/wicd/logfile.py
=>/var/log/wicd
$ file /var/log/wicd
> /var/log/wicd: directory
$ ls -l /var/log/wicd
=> total 0

```

```

$ sudo wicd --version
Traceback (most recent call last):
  File "/usr/share/wicd/daemon/wicd-daemon.py", line 1859, in <module>
    main(sys.argv)
  File "/usr/share/wicd/daemon/wicd-daemon.py", line 1708, in main
    os.symlink(dest, backup_location)
OSError: [Errno 17] File exists

```

---

### Post by monkeybrain20122 on 2013-12-30
It shouldn't be in your system unless you or somebody installed it. Is network-manager installed? You can just install or reinstall network-manager and remove wicd

```
sudo apt-get install --reinstall network-manager 

sudo apt-get --purge remove wicd
```

Then reboot.

---

### Post by Bucky Ball on 2013-12-30
Do those commands the other way around. Theoretically, they can not be installed at the same time. Installing wicd should have killed Network Manager for all intents and purposes. The message you are getting is probably some conflict as a consequence. So:

```
sudo apt-get --purge remove wicd

```
... first. You may just need to reboot then, but if that doesn't work, do the Network Manager reinstall.

---

### Post by Jim_Granite on 2014-01-02
> **Bucky Ball said:**
> 
sudo apt-get --purge remove wicd


I got the 3-step error again today when I rebooted, exactly as shown in the original post.
1. It asks for a login into wicd (where I can't screenshot it because it locks up the entire display)
2. Then it unlocks the display and errors about the D-Bus interface
3. Lastly, it says the wicd daemon has shut down.

The funny thing is, wicd doesn't show up as being installed?????
At least running the command above, nets the following, which implies that wicd isn't installed:
```

$ sudo apt-get --purge remove wicd
=> Reading package lists... Done
=> Building dependency tree       
=> Reading state information... Done
=> Package 'wicd' is not installed, so not removed
=> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Yet, the program seems to exist:
```

$ which wicd
=> /usr/sbin/wicd
$ file /usr/sbin/wicd
=> /usr/sbin/wicd: POSIX shell script, ASCII text executable
$ cat /usr/sbin/wicd
#!/bin/sh

exec /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py $@

```

EDIt: After running the above commands, I ran this anyway, just in case:
```

$ sudo apt-get install --reinstall network-manager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 614 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ saucy/main network-manager amd64 0.9.8.0-0ubuntu22 [614 kB]
Fetched 614 kB in 1s (520 kB/s)          
(Reading database ... 257256 files and directories currently installed.)
Preparing to replace network-manager 0.9.8.0-0ubuntu22 (using .../network-manager_0.9.8.0-0ubuntu22_amd64.deb) ...
Unpacking replacement network-manager ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up network-manager (0.9.8.0-0ubuntu22) ...
Processing triggers for libc-bin ...

```

---

### Post by Bucky Ball on 2014-01-02
So what's happening now? Is Network Manager installed but wicd still there? This is truly strange ... but there must be some logical explanation.

---

### Post by Jim_Granite on 2014-01-03
> **Bucky Ball said:**
> there must be some logical explanation.
I think I figured it out.

I had installed the following, in an attempt to learn how WiFi worked, about a week or so ago:
$ sudo apt-get install wifi-radar
$ [sudo apt-get install kismet]("http://ubuntuforums.org/showthread.php?t=2195547")
$ sudo apt-get install wicd-daemon

So, I just ran these commands:
$ sudo apt-get remove wifi-radar
$ sudo apt-get remove kismet
$ sudo apt-get remove wicd-daemon
The following packages will be REMOVED:
  wicd-daemon wicd-gtk

I rebooted a couple of times, and everything seems fine.
I'll wait a couple of days to see if this truly solves the problem, but, something appears to be buggy in one (or more) of those three wi-fi sniffing programs.

---

### Post by Bucky Ball on 2014-01-03
Ah! That explains a lot. That should have fixed. Good work!

Yep, if all seems good with this issue in a day or two, mark thread as solved to help others. ;)

---

### Post by Jim_Granite on 2014-01-05
> **Bucky Ball said:**
> mark thread as solved to help others. ;)

I should look to see if there is a log file for "apt-get install", but, to report back, this persistent wicd problem upon reboot resolved itself when I uninstalled those programs.
Thanks.

---

