---
title: "Cron not starting at boot-up?"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by chuangt2u on 2011-04-27
Hi.

Been having problems with cron for a few days, and have found that cron is not starting at boot-up.

ps -ef | grep cron

gives:
> rob@ubuntu:~$ ps -ef | grep cron
rob      14965 14907  0 10:32 pts/1    00:00:00 grep --color=auto cron


and chkconfig gives:

> rob@ubuntu:~$ chkconfig
acpi-support                2345
acpid                       off
alsa-mixer-save             off
anacron                     off
apache2                     on
apparmor                    on
apport                      off
atd                         off
avahi-daemon                off
binfmt-support              on
bluetooth                   on
bootlogd                    off
brltty                      on
console-setup               off
cron                        off
cups                        on
dbus                        off
dmesg                       off
dns-clean                   on
failsafe-x                  off
fancontrol                  on
firestarter                 S
gdm                         off
grub-common                 on
hostname                    off
hwclock                     off
hwclock-save                off
irqbalance                  off
kerneloops                  on
killprocs                   on
lm-sensors                  on
module-init-tools           off
mysql                       off
network-interface           off
network-interface-security  off
network-manager             off
networking                  0
nullmailer                  on
ondemand                    on
pcmciautils                 on
plymouth                    off
plymouth-log                off
plymouth-splash             off
plymouth-stop               off
pppd-dns                    on
procps                      off
pulseaudio                  on
rc.local                    on
rcS                         off
rsync                       on
rsyslog                     off
saned                       on
screen-cleanup              on
sendsigs                    0
speech-dispatcher           on
ssh                         off
stop-bootlogd               off
stop-bootlogd-single        off
udev                        off
udev-finish                 off
udevmonitor                 off
udevtrigger                 off
ufw                         off
umountfs                    0
umountnfs.sh                0
umountroot                  0
unattended-upgrades         0
urandom                     0S
wpa-ifupdown                0
x11-common                  on

Cron is not starting at boot.

sudo service cron start

gives:
> rob@ubuntu:~$ sudo service cron start
[sudo] password for rob: 

Warning: Fake initctl called, doing nothing.

I've read that a hard stop, eg a power cut can affect the system and cause problems with starting cron. 

The solution given was:

sudo service cron stop
restart machine
sudo service cron stop
restart machine again and all should be well.

This doesn't work for me.

I've also read that this could be a bug in "upstart", does anyone know of this? [link]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/592114")

Does anyone know if there's a way to restart cron, if so - what's the method?

Cheers

Rob

---

### Post by stmiller on 2011-04-28
```
sudo start cron
```

Should start it. 

```
status cron
```

Should say if it is running.

Interesting bug report. I'm going to dig around on that...

Edit:

This usually puts a service on at default levels (so it will then also run at boot). But it barfs with cron!

```
stmiller@brahms:~$ sudo chkconfig cron on
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: warning: script 'S85vpnagentd_init' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gdm' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'mysql' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and apache2 if stopped
insserv:  loop involving service apache2 at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv:  loop involving service sendsigs at depth 5
insserv: exiting now without changing boot order!
/sbin/insserv failed, exit code 1

```

---

### Post by chuangt2u on 2011-04-28
Thanks for the suggestion stmiller, that did it - although the warning threw me off a little...

> rob@ubuntu:~$ sudo start cron
[sudo] password for rob: 

Warning: Fake initctl called, doing nothing.
rob@ubuntu:~$ 


status cron gives me nothing at all. Does that command report to a file somewhere?
> rob@ubuntu:~$ status cron

Warning: Fake initctl called, doing nothing.
rob@ubuntu:~$ 

There's something wrong here, but I can't figure out what it is.

I added the cron job

> 53 * * * * PYTHONPATH=::/usr/lib/python2.6/dist-packages/gtk-2.0/:$PYTHONPATH /usr/bin/python /u$hon /usr/share/gnome-schedule/xwrapper.py c 19

and now cron can start gedit - many thanks - that's part one sorted out!! :D:D

Now for part 2.

Cron won't start Dropbox. I can start Dropbox manually from either terminal or Apps menu, but not with cron.

Error report generated is:

> pid:	20265
ppid:	20263
uid:	1000
user_info:	('rob', 'x', 1000, 1000, 'rob,,,', '/home/rob', '/bin/bash')
[COLOR="Red"]effective_user_info:	('rob', 'x', 1000, 1000, 'rob,,,', '/home/rob'[/COLOR], '/bin/bash')
euid:	1000
gid:	1000
egid:	1000
group_info:	('rob', 'x', 1000, [])
effective_group_info:	('rob', 'x', 1000, [])
appdata:	u'/home/rob/.dropbox'
	mode=040700	uid=1000	gid=1000
parent	mode=040755	uid=1000	gid=1000
dropbox_path:	u'/home/rob/Dropbox'
	mode=040700	uid=1000	gid=1000
parent	mode=040755	uid=1000	gid=1000
HOME:	/home/rob
tempdir:	'/tmp'
	mode=041777	uid=0	gid=0
parent	mode=040755	uid=0	gid=0
Traceback (most recent call last):
  File "__main__dropbox__.py", line 843, in main_startup
  File "__main__dropbox__.py", line 499, in run
  File "__main__dropbox__.py", line 336, in activate_translation
  File "common_util/i18n.py", line 131, in activate_translation
  File "common_util/i18n.py", line 172, in system_lang_code
AttributeError: 'NoneType' object has no attribute 'split'

Does this mean that I need to change the access permissions of something somewhere?

Thanks for your help

Rob

---

### Post by liferules on 2011-05-08
I too am having the same problems since upgrading to Natty

ps -ef | grep cron

gives:
```
chuck     1749  1379  0 16:21 pts/0    00:00:00 grep cron
```

and chkconfig:
```
root@natty-chimera:/home/chuck# chkconfig
acpi-support                2345
acpid                       off
alsa-restore                off
alsa-store                  off
anacron                     off
apparmor                    on
apport                      off
atd                         off
avahi-daemon                off
binfmt-support              on
bluetooth                   on
bootlogd                    off
brltty                      on
console-setup               off
cron                        off
cups                        off
dbus                        off
dmesg                       off
dns-clean                   on
failsafe-x                  off
gdm                         off
grub-common                 on
hddtemp                     on
hostname                    off
hwclock                     off
hwclock-save                off
irqbalance                  off
kerneloops                  on
killprocs                   on
module-init-tools           off
network-interface           off
network-interface-security  off
network-manager             off
networking                  0
ondemand                    on
pcmciautils                 on
plymouth                    off
plymouth-log                off
plymouth-splash             off
plymouth-stop               off
plymouth-upstart-bridge     off
postfix                     on
pppd-dns                    on
procps                      off
pulseaudio                  on
rc.local                    on
rcS                         off
rsync                       on
rsyslog                     off
saned                       on
sendsigs                    0
setvtrgb                    off
speech-dispatcher           on
stop-bootlogd               off
stop-bootlogd-single        off
sudo                        on
udev                        off
udev-fallback-graphics      off
udev-finish                 off
udevmonitor                 off
udevtrigger                 off
ufw                         off
umountfs                    0
umountnfs.sh                0
umountroot                  0
unattended-upgrades         0
urandom                     0S
vboxballoonctrl-service     on
vboxdrv                     on
vboxweb-service             on
x11-common                  on

```

```

root@natty-chimera:/home/chuck# start cron

Warning: Fake initctl called, doing nothing.

```
I have yet been able to get cron to start. Any ideas?

---

### Post by liferules on 2011-05-15
Bump

Can anyone help me get cron actually to run 
on Natty?

---

### Post by seawolf167 on 2011-05-16
Does

```
sudo service cron start
```

work?

Check with 

```
 ps -ef | grep -i cron
```

---

### Post by liferules on 2011-05-16
```

ps -ef | grep -i cron
chuck    14569  1426  0 10:03 pts/0    00:00:00 grep -i cron

```

```

chuck@natty-chimera:~$ sudo service cron start
[sudo] password for chuck: 

Warning: Fake initctl called, doing nothing.

```

---

### Post by seawolf167 on 2011-05-16
> **liferules said:**
> ```

chuck@natty-chimera:~$ sudo service cron start
[sudo] password for chuck: 

Warning: Fake initctl called, doing nothing.

```

I think this occurs because of a bad start-stop-daemon, but I'm not 100% sure about that or how to fix it sorry :( It sounds like you may have had a botched install or upgrade.

---

### Post by liferules on 2011-05-16
Thanks for the help. Based on your comments and on a whim, I opened Synaptic and reinstalled upstart. This fixed the cron startup issues completely. 

Also, it fixed my problems with Virtualbox loading the vboxdrv. Previously it would not load this kernel module and I was loading manually. But know all is well.. 

Thanks again.

---

### Post by seawolf167 on 2011-05-16
> **liferules said:**
> Thanks for the help. Based on your comments and on a whim, I opened Synaptic and reinstalled upstart. This fixed the cron startup issues completely. 

Also, it fixed my problems with Virtualbox loading the vboxdrv. Previously it would not load this kernel module and I was loading manually. But know all is well.. 

Thanks again.

Awesome :) I'll remember this in case I see this issue again!

---

### Post by jasonsmith01 on 2012-03-23
> **liferules said:**
> Thanks for the help. Based on your comments and on a whim, I opened Synaptic and reinstalled upstart. This fixed the cron startup issues completely. 

Also, it fixed my problems with Virtualbox loading the vboxdrv. Previously it would not load this kernel module and I was loading manually. But know all is well.. 

Thanks again.

Hi folks. First post, don't hurt me. I'm running 12.04 fully updated and cron isn't running. I'm trying to run Simple Back Suite but the scheduling is grayed out assuming because cron isn't running. 

```
XXXXXX@ubuntu:~$ ps -ef | grep cron
root      1356     1  0 15:31 ?        00:00:00 cron
xxxxxx   4638  4578  0 16:18 pts/0    00:00:00 grep --color=auto cron
```

When I try and start it, it states it's already running??

```
xxxxxxx@ubuntu:~$ sudo service cron start
[sudo] password for xxxxxxx: 
start: Job is already running: cron
```

chkconfig shows it's "off". 

I'm totally new with Linux and such, how do I go about re-installing upstart without messing things up?

I'm assuming I can't just uninstall and re-install via Software Center... or can I?

---

### Post by jasonsmith01 on 2012-03-23
Update: 

Installed Synaptic and re-installed Upstart. Rebooted and cron is still not running. Attempted to start cron and the same as before states it's already running. 

I'm at a loss.

[ATTACH]214828[/ATTACH]

Is there anything else in the above pic that needs to be installed?

EDIT:

Okay all is working, I guess it was always working. I have no idea what's going on, please excuse my posts.

---

