---
title: "Update fail...."
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Jim2029 on 2010-12-29
I'm Running 64bit 10.10 ubuntu. The updater is failing on one thing. Python bindings for the GNOME XML library. The error reads as follows:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 143065 files and directories currently installed.)

Preparing to replace python-libxml2 2.7.7.dfsg-4 (using .../python-libxml2_2.7.7.dfsg-4ubuntu0.1_amd64.deb) ...

Unpacking replacement python-libxml2 ...

dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'

dpkg-deb: subprocess <decompress> returned error exit status 2

dpkg: error processing /var/cache/apt/archives/python-libxml2_2.7.7.dfsg-4ubuntu0.1_amd64.deb (--unpack):

 subprocess dpkg-deb --fsys-tarfile returned error exit status 2

No apport report written because MaxReports is reached already
Processing triggers for python-support ...

Errors were encountered while processing:

 /var/cache/apt/archives/python-libxml2_2.7.7.dfsg-4ubuntu0.1_amd64.deb



Originally the updater bricked Firefox so I went into the Package Manager and removed firefox then rebooted and then reinstalled firefox. That got firefox working again but then thie error is coming up.

---

### Post by JC Cheloven on 2010-12-29
try ```
sudo dpkg-reconfigure -a
```with internet connection

---

### Post by Jim2029 on 2010-12-29
I did then this happened:

jim@jim-HP-Pavilion-dv6700-Notebook-PC:~$ sudo dpkg-reconfigure -a
[sudo] password for jim: 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 2958
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
stop: Unknown instance: 
start: Job failed to start
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
atd stop/waiting
atd start/running, process 3236
avahi-daemon stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
avahi-daemon start/running, process 3276
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support         [ OK ] 
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic

Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic

cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package


When i installed this a few days ago I did select to make my home folder private but when I booted the first time i canceled the wizzard because i needed online asap then. would this have something to do with this error??

---

### Post by JC Cheloven on 2011-01-01
Hi, and happy new year :)
> **Jim2029 said:**
> When i installed this a few days ago I did select to make my home folder private but when I booted the first time i canceled the wizzard because i needed online asap then. would this have something to do with this error??
I assume you mean to *encrypt* your user directory. I'm not sure wheter cancelling that can have the culprit or not. 
But you probably don't have anything important in such a recent installation. Considering that, I'd go for a new reinstall, trying to do nothing weird during the install process.
Cheers

---

### Post by Jim2029 on 2011-01-02
Yeah, I was going to do that. I'm just dreading the 208MB of updates. I'm out in no man's land with cellular Internet. Not the fastest in the world.

---

### Post by JC Cheloven on 2011-01-02
> **Jim2029 said:**
> Yeah, I was going to do that. I'm just dreading the 208MB of updates. I'm out in no man's land with cellular Internet. Not the fastest in the world.
Oh, I understand, these gsm internet pens are a nightmare (at least in my place)... perhaps I shouldn't say that here, but if you have slow internet, it could be practical to have a Linux Mint disc/pendrive at hand. Or even using mint as your installed OS. It's basically ubuntu, but with all (proprietary) multimedia codecs & stuff included. So you 1) have a live system that manages flash, mp3 and such 2) when installing you save yourself the time&quota needed for that download.

As for your original question, I'm affraid I'm out of ideas. I never used encryption, so I dont' figure out in which state your system is after cancelling that wizard. But hope this bumps the thread and catch the attention of someone else :/

---

