---
title: "Temp. file folder"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Georgia boy on 2009-11-17
Hi. I was in the temp file folder and was clearing it out. I came across this one file /tmp/tmp.fsMbBD5543. It has a x and a padlock on it. Won't let itself be taken to trash. What is this file and what does it do? When you right click the trash option is grayed out, also properties looks like it belongs to root and says that I'm not the owner and am not able to change any properties on it. It's just a habit of mine to go into the temp folders once in awhile and empty it. Old Windows habit. 

Thanks

Tom

---

### Post by ukripper on 2009-11-17
> **Georgia boy said:**
> Hi. I was in the temp file folder and was clearing it out. I came across this one file /tmp/tmp.fsMbBD5543. It has a x and a padlock on it. Won't let itself be taken to trash. What is this file and what does it do? When you right click the trash option is grayed out, also properties looks like it belongs to root and says that I'm not the owner and am not able to change any properties on it. It's just a habit of mine to go into the temp folders once in awhile and empty it. Old Windows habit. 

Thanks

Tom
Is root the owner of that file? check with this command:```
ls -al /tmp
```

---

### Post by Cuddles McKitten on 2009-11-17
As a general bit of information worth noting, your /tmp folder gets cleared automatically.  As a result, unless you have a tiny hard drive, there won't be many scenarios under which you'll need to delete files in there.

... but for future reference, to delete a file you don't have permission to delete, in a console, type:```
sudo rm /file/name/goes/here/
```Alternately, you could hit ALT+F2 and type "gksu nautilus" and do it graphically that way.

---

### Post by Georgia boy on 2009-11-17
When I went into the properties I think I did see that it was owned by root. When I checked that that trash was grayed out and that I wasn't authorized to do anything to it I got curious as to what it could be. Sorry, didn't know that you didn't have to mess with the temp files. Was used to Windows where at times it would be loaded and I would have to clean them out myself and even then there too were some files that couldn't be deleted. I didn't know if Ubuntu was like that or not and decided to ask around to find out. Still learning. 

If it's not supposed to be messed with then I'll leave it be. 

Thanks


Tom

---

### Post by ukripper on 2009-11-17
For extra info. You can check if your tmp is getting auto clean or not by running following command:
```
cat /etc/default/rcS
```
if TMPTIME=0 it means it is set to auto clean.

and if TMPTIME=-1 or some other negative number then auto tmp clean is disabled.

---

### Post by Georgia boy on 2009-11-17
Thanks for the replies.

If I did that and it was something besides temp=0, then how would I change that to 0 so it would audtomatically clean out the temp folder except for of course that one that I don't know anything about?
Might do that Saturday when I have more time to do things with it. Still curious as to why there would be one that was unable to get rid of but then again so did Windows when I used it.

Thanks

Tom

---

### Post by ukripper on 2009-11-17
> **Georgia boy said:**
> Thanks for the replies.

Still curious as to why there would be one that was unable to get rid of but then again so did Windows when I used it.

Thanks

Tom

we need to look at the timestamp on that file to make any conclusion. If you run below command to check when it was last modified:
```
ls -al /tmp
```

look for that file and check the time stamp for it

---

### Post by Georgia boy on 2009-11-18
Hmmmm, seems that the name of the temp file changed when I went in this morning. Here is the name of the new one:/tmp/tmp.yKxOvq5550

Here is the result I got when doing the time check on per code:

thomas@Thriller:~$ ls -al /tmp
total 60
drwxrwxrwt 12 root   root   12288 2009-11-18 04:47 .
drwxr-xr-x 21 root   root    4096 2009-10-22 04:27 ..
drwx------  2 thomas thomas  4096 2009-11-18 03:58 .esd-1000
drwx------  3 thomas thomas  4096 2009-11-18 03:58 gconfd-thomas
drwxrwxrwt  2 root   root    4096 2009-11-18 03:58 .ICE-unix
drwx------  2 thomas thomas  4096 2009-11-18 03:58 keyring-vvjoei
drwx------  2 thomas thomas  4096 2009-11-18 04:56 orbit-thomas
drwx------  2 thomas thomas  4096 2009-11-18 03:58 pulse-thomas
drwx------  2 thomas thomas  4096 2009-11-18 03:58 seahorse-mtwzax
-rw-------  1 root   root       0 2009-11-18 03:56 tmp.yKxOvq5550
drwx------  3 thomas thomas  4096 2009-11-18 03:59 Tracker-thomas.5855
drwx------  2 thomas thomas  4096 2009-11-18 03:59 virtual-thomas.ZiYI5b
-r--r--r--  1 root   root      11 2009-11-18 03:56 .X0-lock
drwxrwxrwt  2 root   root    4096 2009-11-18 03:56 .X11-unix
thomas@Thriller:~$ 

Included a couple of snapshots. Guess this means each time you open Ubuntu root puts a temp file in the temp file? After all this has a different name from what I had yesterday. 

Thanks
Tom

Tom

---

### Post by ukripper on 2009-11-18
> **Georgia boy said:**
> 

Included a couple of snapshots. Guess this means each time you open Ubuntu root puts a temp file in the temp file? After all this has a different name from what I had yesterday. 

Thanks
Tom

Tom

Not sure which app or service is creating your random temp file. Can you run command:
```
ps aux
```

and post output here.

it seems service or app is using mktemp to create random file. You can try create one yourself and see it by running below command in terminal:
```
mktemp
```

then look in /tmp directory:
```
ls -al /tmp
```

there is new random file generated.
```

```

---

### Post by Georgia boy on 2009-11-18
Per ps aux:

thomas@Thriller:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2844  1688 ?        Ss   03:55   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   03:55   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   03:55   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   03:55   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   03:55   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   03:55   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   03:55   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   03:55   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   03:55   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   03:55   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   03:55   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   03:55   0:00 [kblockd/0]
root        47  0.0  0.0      0     0 ?        S<   03:55   0:00 [kblockd/1]
root        50  0.0  0.0      0     0 ?        S<   03:55   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   03:55   0:00 [kacpi_notify]
root       130  0.0  0.0      0     0 ?        S<   03:55   0:00 [kseriod]
root       170  0.0  0.0      0     0 ?        S    03:55   0:00 [pdflush]
root       171  0.0  0.0      0     0 ?        S    03:55   0:00 [pdflush]
root       172  0.0  0.0      0     0 ?        S<   03:55   0:00 [kswapd0]
root       213  0.0  0.0      0     0 ?        S<   03:55   0:00 [aio/0]
root       214  0.0  0.0      0     0 ?        S<   03:55   0:00 [aio/1]
root      1408  0.0  0.0      0     0 ?        S<   03:55   0:00 [ksuspend_usbd]
root      1409  0.0  0.0      0     0 ?        S<   03:55   0:00 [khubd]
root      1522  0.0  0.0      0     0 ?        S<   03:55   0:00 [ata/0]
root      1529  0.0  0.0      0     0 ?        S<   03:55   0:00 [ata/1]
root      1532  0.0  0.0      0     0 ?        S<   03:55   0:00 [ata_aux]
root      1537  0.0  0.0      0     0 ?        S<   03:55   0:00 [khpsbpkt]
root      2307  0.0  0.0      0     0 ?        S<   03:55   0:00 [scsi_eh_0]
root      2308  0.0  0.0      0     0 ?        S<   03:55   0:00 [usb-storage]
root      2322  0.0  0.0      0     0 ?        S<   03:55   0:00 [scsi_eh_1]
root      2323  0.0  0.0      0     0 ?        S<   03:55   0:00 [scsi_eh_2]
root      2324  0.0  0.0      0     0 ?        S<   03:55   0:00 [scsi_eh_3]
root      2325  0.0  0.0      0     0 ?        S<   03:55   0:00 [scsi_eh_4]
root      2377  0.0  0.0      0     0 ?        S<   03:55   0:00 [knodemgrd_0]
root      2380  0.0  0.0      0     0 ?        S<   03:55   0:01 [scsi_eh_5]
root      2381  0.0  0.0      0     0 ?        S<   03:55   0:00 [scsi_eh_6]
root      2594  0.0  0.0      0     0 ?        S<   03:55   0:00 [kjournald]
root      2800  0.0  0.0   2404   952 ?        S<s  03:56   0:00 /sbin/udevd --d
root      3119  0.0  0.0      0     0 ?        S<   03:56   0:00 [kpsmoused]
root      4602  0.0  0.0   1716   512 tty4     Ss+  03:56   0:00 /sbin/getty 384
root      4603  0.0  0.0   1716   512 tty5     Ss+  03:56   0:00 /sbin/getty 384
root      4607  0.0  0.0   1716   508 tty2     Ss+  03:56   0:00 /sbin/getty 384
root      4608  0.0  0.0   1716   508 tty3     Ss+  03:56   0:00 /sbin/getty 384
root      4609  0.0  0.0   1716   508 tty6     Ss+  03:56   0:00 /sbin/getty 384
root      4789  0.0  0.0   2456  1356 ?        Ss   03:56   0:00 /usr/sbin/acpid
root      4817  0.0  0.0      0     0 ?        S<   03:56   0:00 [kondemand/0]
root      4818  0.0  0.0      0     0 ?        S<   03:56   0:00 [kondemand/1]
syslog    4914  0.0  0.0   1936   720 ?        Ss   03:56   0:00 /sbin/syslogd -
root      4970  0.0  0.0   1872   540 ?        S    03:56   0:00 /bin/dd bs 1 if
klog      4972  0.0  0.1   3696  2608 ?        Ss   03:56   0:00 /sbin/klogd -P
108       4994  0.0  0.0   2900  1376 ?        Ss   03:56   0:00 /usr/bin/dbus-d
root      5010  0.0  0.1  12776  2080 ?        Ssl  03:56   0:00 /usr/sbin/Netwo
root      5024  0.0  0.0   3416  1284 ?        Ss   03:56   0:00 /usr/sbin/Netwo
root      5037  0.0  0.0   4112  1108 ?        Ss   03:56   0:00 /usr/bin/system
avahi     5057  0.0  0.0   2760  1452 ?        Ss   03:56   0:00 avahi-daemon: r
avahi     5058  0.0  0.0   2760   468 ?        Ss   03:56   0:00 avahi-daemon: c
root      5099  0.0  0.1   6036  2528 ?        Ss   03:56   0:00 /usr/sbin/cupsd
root      5178  0.0  0.0   2020   896 ?        Ss   03:56   0:00 /usr/sbin/dhcdb
111       5197  0.0  0.2   6252  4196 ?        Ss   03:56   0:00 /usr/sbin/hald
root      5200  0.0  0.1   7764  2340 ?        Ssl  03:56   0:00 /usr/sbin/conso
root      5262  0.0  0.0   3236  1084 ?        S    03:56   0:00 hald-runner
111       5284  0.0  0.0   2204   904 ?        S    03:56   0:00 hald-addon-acpi
root      5290  0.0  0.0   3300  1052 ?        S    03:56   0:00 hald-addon-inpu
root      5306  0.0  0.0   3304  1040 ?        S    03:56   0:00 hald-addon-stor
root      5308  0.0  0.0   3304  1040 ?        S    03:56   0:00 hald-addon-stor
root      5310  0.0  0.0   3304  1040 ?        S    03:56   0:00 hald-addon-stor
root      5312  0.0  0.0   3304  1040 ?        S    03:56   0:00 hald-addon-stor
root      5315  0.0  0.0   3304  1040 ?        S    03:56   0:01 hald-addon-stor
root      5335  0.0  0.0   3052  1256 ?        Ss   03:56   0:00 /usr/sbin/hcid
root      5345  0.0  0.0      0     0 ?        S<   03:56   0:00 [btaddconn]
root      5346  0.0  0.0      0     0 ?        S<   03:56   0:00 [btdelconn]
root      5372  0.0  0.0   2900  1072 ?        S    03:56   0:00 /usr/lib/blueto
root      5373  0.0  0.0   2964  1256 ?        S    03:56   0:00 /usr/lib/blueto
root      5378  0.0  0.0      0     0 ?        S<   03:56   0:00 [krfcommd]
root      5417  0.0  0.0  14048  1604 ?        Ss   03:56   0:00 /usr/sbin/gdm
root      5420  0.0  0.1  14512  2996 ?        S    03:56   0:00 /usr/sbin/gdm
root      5424  0.8  1.5  37504 31808 tty7     SLs+ 03:56   1:10 /usr/bin/X :0 -
daemon    5469  0.0  0.0   1984   420 ?        Ss   03:56   0:00 /usr/sbin/atd
root      5483  0.0  0.0   2104   888 ?        Ss   03:56   0:00 /usr/sbin/cron
dhcp      5536  0.0  0.0   2440  1216 ?        S    03:56   0:00 /sbin/dhclient
root      5582  0.0  0.0   1716   508 tty1     Ss+  03:56   0:00 /sbin/getty 384
thomas    5681  0.0  0.1   7036  4148 ?        S    03:58   0:00 /usr/lib/libgco
thomas    5683  0.0  0.0  14240  2032 ?        S    03:58   0:00 /usr/bin/gnome-
thomas    5684  0.0  0.3  28952  7540 ?        Ssl  03:58   0:00 x-session-manag
thomas    5799  0.0  0.3  23180  6808 ?        Ss   03:58   0:00 /usr/bin/seahor
thomas    5803  0.0  0.0   2700  1084 ?        Ss   03:58   0:00 dbus-daemon --f
thomas    5804  0.0  0.4  40060 10228 ?        Sl   03:58   0:00 gnome-settings-
thomas    5808  0.0  0.2  28472  5772 ?        Sl   03:58   0:04 /usr/bin/pulsea
thomas    5811  0.0  0.1   5676  2200 ?        S    03:58   0:00 /usr/lib/pulsea
thomas    5828  0.0  0.2  15424  4692 ?        Ss   03:59   0:03 gnome-screensav
thomas    5829  0.1  0.5  20976 12356 ?        S    03:59   0:09 /usr/bin/metaci
thomas    5831  0.1  0.9  44020 20660 ?        S    03:59   0:08 gnome-panel --s
thomas    5832  0.1  1.5  82044 31648 ?        S    03:59   0:07 nautilus --no-d
thomas    5839  0.0  0.1  40992  3076 ?        Ssl  03:59   0:00 /usr/lib/bonobo
thomas    5842  0.0  0.1   5372  2104 ?        S    03:59   0:00 /usr/lib/gvfs/g
thomas    5843  0.0  0.2  14716  5720 ?        S    03:59   0:00 bluetooth-apple
thomas    5846  0.0  0.6  25136 13512 ?        S    03:59   0:00 update-notifier
thomas    5851  0.0  0.2  15200  5516 ?        S    03:59   0:00 tracker-applet
thomas    5855  0.0  0.4  31536 10368 ?        SNl  03:59   0:00 trackerd
thomas    5863  0.0  0.5  23260 10752 ?        S    03:59   0:02 nm-applet --sm-
thomas    5864  0.0  0.2  20760  4656 ?        Ss   03:59   0:00 /usr/lib/gnome-
thomas    5865  0.0  0.5  24168 12144 ?        S    03:59   0:00 python /usr/sha
thomas    5867  0.0  0.3  23552  7788 ?        Ss   03:59   0:00 gnome-power-man
thomas    5873  0.0  0.0  29048  1888 ?        Ssl  03:59   0:00 /usr/lib/gvfs//
thomas    5882  0.0  0.4  22364  9876 ?        S    03:59   0:00 /usr/lib/gnome-
thomas    5884  0.0  0.1   5372  2136 ?        S    03:59   0:00 /usr/lib/gvfs/g
thomas    5886  0.0  0.1  22032  2692 ?        S    03:59   0:00 /usr/lib/gvfs/g
thomas    5898  0.0  0.7  43972 15008 ?        Sl   03:59   0:00 /usr/lib/gnome-
thomas    5902  0.0  0.6  25252 12920 ?        S    03:59   0:00 /usr/lib/fast-u
thomas    5984  0.0  0.0   1772   520 ?        S    04:03   0:00 /bin/sh /usr/bi
thomas    5996  0.0  0.0   1772   524 ?        S    04:03   0:00 /bin/sh /usr/li
thomas    6000  1.3  3.1 169664 65364 ?        Sl   04:03   1:44 /usr/lib/thunde
thomas    6266  1.0  3.4 188432 71712 ?        Sl   04:54   0:46 /usr/lib/firefo
thomas    6411  5.3  0.9  73780 20388 ?        Sl   06:10   0:00 gnome-terminal
thomas    6413  0.0  0.0   2796   752 ?        S    06:10   0:00 gnome-pty-helpe
thomas    6414  2.0  0.1   5648  3068 pts/0    Ss   06:10   0:00 bash
thomas    6431  0.0  0.0   2644  1004 pts/0    R+   06:10   0:00 ps aux
thomas@Thriller:~$ 

App or service making an auto template each time start up? Why would one do that?
Sorry for dumb questions when I notice something odd I ask. Still learning.

Thanks
Tom

---

### Post by ukripper on 2009-11-18
This may explain the behaviour if bash script is using it.
[http://www.cyberciti.biz/tips/shell-scripting-bash-how-to-create-temporary-random-file-name.html](http://www.cyberciti.biz/tips/shell-scripting-bash-how-to-create-temporary-random-file-name.html)

---

### Post by Georgia boy on 2009-11-18
So, at this rate it is creating it's own temp file in root and there's no need to worry about anything right? I have never been into the temp file before and so I never knew what was going on. From what I've noticed yesterday and today both files were created using different file numbers each day and then both being locked and unreadable. This being the case then I shouldn't be concerned right? It's just normal behavior for the system then.

Thanks

Tom

---

### Post by ukripper on 2009-11-19
> **Georgia boy said:**
> So, at this rate it is creating it's own temp file in root and there's no need to worry about anything right? I have never been into the temp file before and so I never knew what was going on. From what I've noticed yesterday and today both files were created using different file numbers each day and then both being locked and unreadable. This being the case then I shouldn't be concerned right? It's just normal behavior for the system then.

Thanks

Tom

yeh that is normal especially when you running some cutom bash scripts or an app which uses tmp directory. 

And also the file you see is run by root, if you think someone has your root password and accessing you tmp by gaining acces to root ,in that case Game is over  for you anyway and tmp would be least of your problem  as that person can access anything on your computer, why he would be bother with your tmp when he can do whatever he wants?

So i think this is normal behaviour for root to create tmp files

---

### Post by Georgia boy on 2009-11-19
> **ukripper said:**
> yeh that is normal especially when you running some cutom bash scripts or an app which uses tmp directory. 

And also the file you see is run by root, if you think someone has your root password and accessing you tmp by gaining acces to root ,in that case Game is over  for you anyway and tmp would be least of your problem  as that person can access anything on your computer, why he would be bother with your tmp when he can do whatever he wants?

So i think this is normal behaviour for root to create tmp files

I don't know anything about custom bash scripts. Wonder what applications would be creating a new root file each time I sign on. I don't think that anyone has my root password. Would root password be a separate password from others? I've never done anything except the add/removes and through synaptic when I tried to get some games out of the repos.

Here is the check on temp cleaning byself when shut down.

thomas@Thriller:~$ cat /etc/default/rcS
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no
thomas@Thriller:~$ 

Looks like it cleans self.

So, something is creating it's own locked root temp file. Wonder which is doing so.

Thanks

Tom

---

### Post by Malac on 2009-11-19
I wouldn't worry about it, /tmp is set to auto clean each time and the file may not actually be in use by the time the system is up and running. It may just be created at startup by any one of a number of scripts/programs run by root as the system is brought up.
 
Hope this helps.

---

### Post by ukripper on 2009-11-19
> **Georgia boy said:**
> I don't know anything about custom bash scripts. Wonder what applications would be creating a new root file each time I sign on. I don't think that anyone has my root password. Would root password be a separate password from others? I've never done anything except the add/removes and through synaptic when I tried to get some games out of the repos.

Here is the check on temp cleaning byself when shut down.

thomas@Thriller:~$ cat /etc/default/rcS
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no
thomas@Thriller:~$ 

Looks like it cleans self.

So, something is creating it's own locked root temp file. Wonder which is doing so.

Thanks

Tom

This tmp.randomnumber is created on every reboot. i think it is part of initscript during boot

---

### Post by Georgia boy on 2009-11-19
Thanks everyone. You put an old man's mind at rest. I am constantly trying to learn new things. I go to the forums here to try and view what is happening to everyone else, their problems and fixes. I get nosey on my system and check things out and when I see something I don't understand I ask. I know that some of my questions sound dumb but when I don't see anything pertaining to what I notice I ask to learn. Sometimes I might wind up with my foot in my mouth and red faced but that's all part of learning as far as I'm concerned.:p

I'll just mosey back to the forums to do some more learning and keep on playing on my machine. I really like Ubuntu and the people here in the forums. I'm waiting for the next LTS and plan on doing a complete install to wipe out everything and be Ubuntu only.

Again, thanks for your help and showing me things to try and understand what goes on with this system. When I do something stupid just reach out and pop me on top of my head.

Tom

---

