---
title: "Ubuntu alternate log errors"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by opodaniel on 2011-08-02
I experience some Libre Office freeze on Ubuntu alternate ( the only one I could install on my SonyVaio laptop. I wanted to see the logs and I got this errors:
> Could not open the following files:

/var/log/daemon.log: Error stating file '/var/log/daemon.log': No such file or directory
/var/log/user.log: Error stating file '/var/log/user.log': No such file or directory
/var/log/bootstrap.log: Error stating file '/var/log/bootstrap.log': No such file or directory
/var/log/jockey.log.1: Error stating file '/var/log/jockey.log.1': No such file or directory
/var/log/syslog.1: Error stating file '/var/log/syslog.1': No such file or directory
/var/log/messages: Error stating file '/var/log/messages': No such file or directory
/var/log/lpr.log: Error stating file '/var/log/lpr.log': No such file or directory
/var/log/mail.warn: Error stating file '/var/log/mail.warn': No such file or directory
/var/log/mail.info: Error stating file '/var/log/mail.info': No such file or directory
/var/log/debug: Error stating file '/var/log/debug': No such file or directory


on   ls -lha I got this
```
total 5.6M
drwxr-xr-x 14 root              root 4.0K 2011-08-02 13:59 .
drwxr-xr-x 15 root              root 4.0K 2011-08-02 09:50 ..
-rw-r--r--  1 root              root  45K 2011-08-02 11:14 alternatives.log
drwxr-xr-x  2 root              root 4.0K 2011-04-19 01:26 apparmor
drwxr-xr-x  2 root              root 4.0K 2011-08-02 09:47 apt
-rw-r--r--  1 root              root  395 2011-08-02 09:48 aptitude
-rw-r-----  1 syslog            adm   45K 2011-08-02 14:00 auth.log
-rw-r-----  1 root              adm    31 2011-08-02 09:47 boot
-rw-r--r--  1 root              root 1.1K 2011-08-02 13:59 boot.log
-rw-rw-r--  1 root              utmp  384 2011-08-02 11:15 btmp
drwxr-xr-x  2 root              root 4.0K 2011-08-02 13:53 ConsoleKit
drwxr-xr-x  2 root              root 4.0K 2011-08-02 02:54 cups
drwxr-xr-x  2 root              root 4.0K 2011-04-20 22:19 dist-upgrade
-rw-r-----  1 root              adm   56K 2011-08-02 13:59 dmesg
-rw-r-----  1 root              adm     0 2011-08-02 13:58 dmesg.0
-rw-r-----  1 root              adm   15K 2011-08-02 13:49 dmesg.1.gz
-rw-r-----  1 root              adm     0 2011-08-02 13:27 dmesg.2.gz
-rw-r-----  1 root              adm   17K 2011-08-02 12:23 dmesg.3.gz
-rw-r-----  1 root              adm   17K 2011-08-02 11:15 dmesg.4.gz
-rw-r--r--  1 root              root 1.3M 2011-08-02 14:01 dpkg.log
-rw-r--r--  1 root              root  24K 2011-08-02 09:53 faillog
-rw-r--r--  1 root              root 3.1K 2011-08-02 11:32 fontconfig.log
drwxr-xr-x  2 root              root 4.0K 2011-08-02 09:47 fsck
drwxrwx--T  2 root              gdm  4.0K 2011-08-02 13:59 gdm
drwxr-xr-x  3 root              root 4.0K 2011-08-02 09:53 installer
-rw-r--r--  1 root              root  34K 2011-08-02 01:59 jockey.log
-rw-r-----  1 syslog            adm  1.4M 2011-08-02 14:00 kern.log
-rw-rw-r--  1 root              utmp 286K 2011-08-02 09:53 lastlog
-rw-r-----  1 syslog            adm     0 2011-08-02 13:53 mail.err
-rw-r-----  1 syslog            adm     0 2011-08-02 13:53 mail.log
drwxr-xr-x  2 root              root 4.0K 2011-08-02 13:53 news
-rw-r--r--  1 root              root  52K 2011-08-02 13:59 pm-powersave.log
-rw-r--r--  1 root              root  17K 2011-08-02 09:20 pm-suspend.log
-rw-r--r--  1 root              root    0 2011-08-02 09:47 pycentral.log
drwxr-xr-x  3 root              root 4.0K 2011-08-02 02:37 samba
drwxr-xr-x  2 speech-dispatcher root 4.0K 2011-01-12 00:03 speech-dispatcher
-rw-r-----  1 syslog            adm  1.9M 2011-08-02 14:00 syslog
-rw-r--r--  1 root              root 323K 2011-08-02 13:59 udev
-rw-r-----  1 syslog            adm     0 2011-08-02 13:53 ufw.log
drwxr-xr-x  2 root              root 4.0K 2011-04-12 17:22 unattended-upgrades
-rw-r--r--  1 root              root 204K 2011-08-02 10:40 vbox-install.log
-rw-rw-r--  1 root              utmp  73K 2011-08-02 14:00 wtmp
-rw-r--r--  1 root              root  29K 2011-08-02 13:59 Xorg.0.log
-rw-r--r--  1 root              root 7.9K 2011-08-02 13:57 Xorg.0.log.old

```

what is the problem?

---

### Post by jtarin on 2011-08-02
How did you install it?

---

### Post by opodaniel on 2011-08-02
the system is sonyvaio vpcsa and it has 2 video card  Intel Sandy Bridge on chip and Ati Radeon 6630m. It also has 4ssd in Raid mode, so I couldn't install with normal desktop distro.
What do you mean by how did I install it? It is a manual step by step text mode procedure.

---

### Post by jtarin on 2011-08-02
I didn't see your Ubuntu version glaring at me me like a 20,000,000kw neon sign and had assumed you installed Libre Office manually. That's what I meant.:P

---

### Post by opodaniel on 2011-08-02
I am so sorry, I am newbie :d
I installed Ubuntu Natty 11.04
Libre Office was already installed 3.32 , not sure, but initially I didn't install it, I just made some sudo apt-get update && sudo apt-get upgrade

---

### Post by opodaniel on 2011-08-02
I just updated LibreOffice to 3.4 and for 2-3 hours computer didn't freeze anymore. 
Mysterious are the ways of IT :d.

---

### Post by jtarin on 2011-08-02
This difficulty could very well have something to do with the version of Java you are running....possibly one of the Free versions. I have a tendency to like Sun Java for my java apps.

---

### Post by opodaniel on 2011-08-03
Thanks for the info. Following your advice I have also installed SUN Java. Any way, the computer is running smoothly no more freezing.

---

### Post by opodaniel on 2011-08-11
The problem is related to the poor driver support for Intel SandyBridge HD3000 graphics.  The solution was to disable the AntiAliasing option in my LibreOffice. This problem is discussed here 
[http://ubuntuforums.org/showthread.php?t=1814190](http://ubuntuforums.org/showthread.php?t=1814190)

---

