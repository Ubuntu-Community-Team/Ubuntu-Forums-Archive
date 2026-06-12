---
title: "How can I remove a package that wont leave?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-10-11
I am trying to get the program Bluez to uninstall and go away. For some reason I get an error every time I try and uninstall it. It also always wants to update but fails that too. Below are the errors I get when trying to uninstall and update respectively. 

```
jason@Barnaby:~$ sudo apt-get remove bluez
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libimlib2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bluez
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 1262kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 153256 files and directories currently installed.)
Removing bluez ...
 * Stopping bluetooth                                                                                                       bluetoothd: no process killed
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: error processing bluez (--remove):
 subprocess pre-removal script returned error exit status 1
postinst called with unknown argument `abort-remove'
Errors were encountered while processing:
 bluez
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@Barnaby:~$ 

```

```
jason@Barnaby:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bluez
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/437kB of archives.
After this operation, 197kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 153266 files and directories currently installed.)
Preparing to replace bluez 4.53-0ubuntu1 (using .../bluez_1%3a4.39-0ubuntu2_amd64.deb) ...
 * Stopping bluetooth                                                                                                       bluetoothd: no process killed
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping bluetooth                                                                                                       bluetoothd: no process killed
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bluez_1%3a4.39-0ubuntu2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
postinst called with unknown argument `abort-upgrade'
Errors were encountered while processing:
 /var/cache/apt/archives/bluez_1%3a4.39-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@Barnaby:~$ 

```

---

### Post by khughitt on 2009-10-11
Try
```

sudo apt-get -f remove bluez
```

If that does work, try cleaning up aptitude's cache a bit:

```

sudo apt-get autoremove
sudo apt-get autoclean
sudo rm -fr /var/cache/apt/archives/*.deb

```

then try upgrading your system again and removing the package.

Goodluck!

---

### Post by slughappy1 on 2009-10-11
Did everything you said and it still will not be removed.

---

### Post by slughappy1 on 2009-10-12
Anyone else have any ideas?

---

### Post by diesch on 2009-10-12
What does
```
sudo sh -x /etc/init.d/bluetooth stop
```
say?

---

### Post by slughappy1 on 2009-10-12
```
jason@Barnaby:~$ sudo sh -x /etc/init.d/bluetooth stop
[sudo] password for jason: 
+ PATH=/sbin:/bin:/usr/sbin:/usr/bin
+ DESC=bluetooth
+ DAEMON=/usr/sbin/bluetoothd
+ test -f /etc/default/bluetooth
+ . /etc/default/bluetooth
+ BLUETOOTH_ENABLED=1
+ . /lib/lsb/init-functions
+ FANCYTTY=
+ [ -e /etc/lsb-base-logging.sh ]
+ . /etc/lsb-base-logging.sh
+ set -e
+ log_daemon_msg Stopping bluetooth
+ [ -z Stopping bluetooth ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ usplash_write TEXT Stopping bluetooth
+ log_to_console log_daemon_msg Stopping bluetooth
+ [ n != y ]
+ [ no != yes ]
+ readlink /proc/self/fd/0
+ stdin=/dev/pts/1
+ [ /dev/pts/1 != /dev/pts/1 ]
+ return 0
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ [ -t 1 ]
+ [ xxterm !=  ]
+ [ xxterm != xdumb ]
+ [ -x /usr/bin/tput ]
+ [ -x /usr/bin/expr ]
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ [ -z ]
+ FANCYTTY=1
+ true
+ /usr/bin/tput xenl
+ /usr/bin/tput cols
+ COLS=80
+ [ 80 ]
+ [ 80 -gt 6 ]
+ /usr/bin/expr 80 - 7
+ COL=73
+ printf  * Stopping bluetooth       
 * Stopping bluetooth       + /usr/bin/expr 80 - 1
+ /usr/bin/tput hpa 79
                                                                               + printf  
 + test 1 = 0
+ killall bluetoothd
bluetoothd: no process killed
jason@Barnaby:~$ 

```

---

### Post by diesch on 2009-10-12
Open the file /etc/default/bluetooth and replace the line
```
BLUETOOTH_ENABLED=1
``` with
```
BLUETOOTH_ENABLED=0
```

---

### Post by slughappy1 on 2009-10-12
Holy sweet awesome it's gone! Thank you

---

