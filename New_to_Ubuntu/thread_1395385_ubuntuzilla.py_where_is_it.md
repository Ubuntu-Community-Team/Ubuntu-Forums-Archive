---
title: "ubuntuzilla.py: where is it?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by watchpocket on 2010-01-31
Looking at my user.log in the System Log Viewer, I see this line:

Jan 31 16:00:01 rj-home UBUNTUZILLA: /bin/sh: /usr/local/bin/ubuntuzilla.py: Permission denied

Looking in /usr/local/bin/, there is no ubuntuzilla.py

Okay, so it's a Python script and I need to look in a python directory to check perms?  But which one?

---

### Post by nanotube on 2010-01-31
> **watchpocket said:**
> Looking at my user.log in the System Log Viewer, I see this line:

Jan 31 16:00:01 rj-home UBUNTUZILLA: /bin/sh: /usr/local/bin/ubuntuzilla.py: Permission denied

Looking in /usr/local/bin/, there is no ubuntuzilla.py

Okay, so it's a Python script and I need to look in a python directory to check perms?  But which one?

post your output of ```
ls -al /usr/local/bin
```

and also try ```
dpkg -l ubuntuzilla
```
and
```
dpkg -L ubuntuzilla
```

---

### Post by watchpocket on 2010-01-31
> **nanotube said:**
> post your output of ```
ls -al /usr/local/bin
```and also try ```
dpkg -l ubuntuzilla
```and
```
dpkg -L ubuntuzilla
```

I do have the sipie.py script (for Sirius/XM) working successfully, and those are the files in /usr/local/bin.
```
--> sudo ls -al /usr/local/bin
[sudo] password for rj: 
total 32
drwx------  2 root root 4096 2010-01-03 02:15 .
drwxr-xr-x 10 root root 4096 2010-01-03 02:15 ..
-rwxr-xr-x  1 root root  278 2010-01-03 02:15 cliSipie
-rwxr-xr-x  1 root root  270 2010-01-03 02:15 gtkSipie
-rwxr-xr-x  1 root root  192 2010-01-03 02:15 sipie.py
-rwxr-xr-x  1 root root   99 2010-01-03 02:15 testall.sh
-rwxr-xr-x  1 root root  195 2010-01-03 02:15 to3.sh
-rwxr-xr-x  1 root root  268 2010-01-03 02:15 wxSipie


--> dpkg -l ubuntuzilla  
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                Version                             Description
+++-===================================-===================================-======================================================================================
rc  ubuntuzilla                         4.8.3-0ubuntu1                      Ubuntuzilla - Mozilla software installer for Ubuntu


--> dpkg -L ubuntuzilla
/etc
/etc/cron.daily
/etc/cron.daily/ubuntuzillaupdatecron
/usr/local
```Thanks.

---

### Post by llamabr on 2010-01-31
weird.  Also try:

```
locate ubuntuzilla
```

---

### Post by watchpocket on 2010-01-31
--> sudo locate ubuntuzilla
[sudo] password for rj: 
/etc/cron.daily/ubuntuzillaupdatecron
/var/lib/apt/lists/switch.dl.sourceforge.net_project_ubuntuzilla_apt_dists_all_Release
/var/lib/apt/lists/switch.dl.sourceforge.net_project_ubuntuzilla_apt_dists_all_Release.gpg
/var/lib/apt/lists/switch.dl.sourceforge.net_project_ubuntuzilla_apt_dists_all_main_binary-amd64_Packages
/var/lib/dpkg/info/ubuntuzilla.list

---

### Post by dolphinaura on 2010-01-31
seems like it isn't installed properly.
and im guessing that the package name is ubuntuzilla (im not sure, im on mac osx right now)
```

sudo dpkg --purge ubuntuzilla

```

and try installing it again.

---

### Post by nanotube on 2010-02-01
status 'rc' means the package has been removed, but configuration files remain.

just run the 'dpkg --purge' command provided above, or use ```
sudo apt-get remove --purge ubuntuzilla
```

to remove the config files, which would also remove the cron job which tries to call the now non-existent ubuntuzilla.py.

---

### Post by watchpocket on 2010-02-01
But would I then want to reinstall it?  I mean, is ubuntuzilla a name for Firefox? 

Or what is ubuntuzilla exactly? (I know it's a project encompassing seeral things, but what is it as it appears on my machine?) 

Thanks.

---

### Post by watchpocket on 2010-02-01
Ubuntuzilla purged & reinstalled.  Thanks to all.

"The Ubuntuzilla script provides an easy way to install the latest releases of Mozilla software (Firefox, Thunderbird, Seamonkey), on Ubuntu Linux, with minimal disturbance to the system."

---

### Post by nanotube on 2010-02-01
yes, the ubuntuzilla script is an installer for official mozilla builds.

there's now an ubuntuzilla repository for the mozilla software, but only for 32bit, since mozilla only makes 32bit builds.

but i see from some output above that you're on 64bit, so not suggesting it. :)

---

