---
title: "logging system crash down"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by flylehe on 2009-11-07
Hi,
My laptop shuts itself down, which I guess is due to high CPU temperature. I want to confirm this by looking at some system log file that records the reason that the system shuts itself down.

I checked my /var/log/pm-*.log, /var/log/messages and /var/log/syslog, but did not find anything mentioned the crash down of my system at the particular time yesterday. I guess perhaps the logging has not been enabled? 

Can someone give some advice?

Thanks and regards!

---

### Post by LewRockwell on 2009-11-07
> **flylehe said:**
> Can someone give some advice?

help us to help you

tell us what you've got and how long you've had it set up that way

you're probably not the first person ever to experience your difficulties

.

---

### Post by flylehe on 2009-11-07
Thank you!

Today it is my first time to realize to check such system log files, so to my knowledge I am not aware I have set up or changed its configuration on purpose.

I am not sure I am looking at the right files, so here is the list of files under /var/log
> 
$ ls /var/log
apparmor       btmp             debug.0       dmesg.3.gz     exim4           kern.log.5.gz  messages.2.gz   syslog.4.gz          wpa_supplicant.log.1.gz
apt            btmp.1           debug.1.gz    dmesg.4.gz     faillog         kern.log.6.gz  messages.3.gz   syslog.5.gz          wpa_supplicant.log.2.gz
aptitude       ConsoleKit       debug.2.gz    dpkg.log       fontconfig.log  kismet         news            syslog.6.gz          wpa_supplicant.log.3.gz
aptitude.1.gz  cups             debug.3.gz    dpkg.log.1     fsck            lastlog        peercast        udev                 wpa_supplicant.log.4.gz
aptitude.2.gz  daemon.log       debug.4.gz    dpkg.log.2.gz  gdm             lpr.log        pm-suspend.log  unattended-upgrades  wpa_supplicant.log.5.gz
auth.log       daemon.log.0     debug.5.gz    dpkg.log.3.gz  installer       mail.err       pycentral.log   user.log             wtmp
auth.log.0     daemon.log.1.gz  debug.6.gz    dpkg.log.4.gz  kern.log        mail.info      samba           user.log.0           wtmp.1
auth.log.1.gz  daemon.log.2.gz  dist-upgrade  dpkg.log.5.gz  kern.log.0      mail.log       syslog          user.log.1.gz        wvdialconf.log
auth.log.2.gz  daemon.log.3.gz  dmesg         dpkg.log.6.gz  kern.log.1.gz   mail.warn      syslog.0        user.log.2.gz        Xorg.0.log
auth.log.3.gz  daemon.log.4.gz  dmesg.0       dpkg.log.7.gz  kern.log.2.gz   messages       syslog.1.gz     user.log.3.gz        Xorg.0.log.old
boot           daemon.log.5.gz  dmesg.1.gz    dpkg.log.8.gz  kern.log.3.gz   messages.0     syslog.2.gz     wicd
bootstrap.log  debug            dmesg.2.gz    dpkg.log.9.gz  kern.log.4.gz   messages.1.gz  syslog.3.gz     wpa_supplicant.log


I want to investigate the crash down yesterday, but my /var/log/syslog starts logging from today, so it seems not help. But I found there is another file /var/log/syslog.0, which gives info around the time 12:18 when the system crashed down yesterday during compiling a big program by gcc:
> 
Nov  6 12:12:09 lehe /usr/sbin/cron[5223]: (CRON) INFO (pidfile fd = 3)
Nov  6 12:12:09 lehe /usr/sbin/cron[5224]: (CRON) STARTUP (fork ok)
Nov  6 12:12:09 lehe /usr/sbin/cron[5224]: (CRON) INFO (Running @reboot jobs)
Nov  6 12:12:10 lehe /USR/SBIN/CRON[5248]: (ting) CMD (\rm -r ~/.chmsee/bookshelf >/dev/null 2>&1 #JOB_ID_2)
Nov  6 12:12:15 lehe gdmgreeter[5367]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Nov  6 12:13:20 lehe pulseaudio[5541]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  6 12:13:20 lehe pulseaudio[5543]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  6 12:13:20 lehe pulseaudio[5543]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  6 12:13:27 lehe x-session-manager[5423]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov  6 12:13:40 lehe x-session-manager[5423]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Nov  6 12:13:40 lehe x-session-manager[5423]: WARNING: Unable to parse command '(null)': Key file contains key 'Terminal' which has value that cannot be inter
preted. 
Nov  6 12:13:40 lehe x-session-manager[5423]: WARNING: Could not launch application 'smart-notifier.desktop': Unable to start application: Key file contains k
ey 'Terminal' which has value that cannot be interpreted. 
Nov  6 12:13:40 lehe x-session-manager[5423]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child 
process "nm-applet" (No such file or directory) 
Nov  6 12:13:40 lehe pulseaudio[5543]: module-x11-xsmp.c: X11 session manager not running.
Nov  6 12:13:40 lehe pulseaudio[5543]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov  6 12:17:01 lehe /USR/SBIN/CRON[5917]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 13:08:22 lehe syslogd 1.5.0#2ubuntu6: restart.
Nov  6 13:08:22 lehe kernel: Inspecting /boot/System.map-2.6.27-15-generic
Nov  6 13:08:22 lehe kernel: Cannot find map file.
Nov  6 13:08:22 lehe kernel: Loaded 50605 symbols from 102 modules.
Nov  6 13:08:22 lehe kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  6 13:08:22 lehe kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  6 13:08:22 lehe kernel: [    0.000000] Linux version 2.6.27-15-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Oct 20 06:52:09 UTC 2009 (Ubuntu 2.6.27-15.43-generic)



Similarly in /var/log/messages, the info around that time is
> 
Nov  6 12:11:57 lehe kernel: [   22.203710] type=1505 audit(1257527516.016:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3846
Nov  6 12:11:57 lehe kernel: [   22.391172] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov  6 12:11:57 lehe kernel: [   23.385902] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-30 processors (1 cpu cores) (version 2.20.00)
Nov  6 12:11:57 lehe kernel: [   23.385944] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4
Nov  6 12:11:57 lehe kernel: [   23.385948] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
Nov  6 12:13:20 lehe pulseaudio[5541]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  6 12:13:20 lehe pulseaudio[5543]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  6 12:13:20 lehe pulseaudio[5543]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  6 13:08:22 lehe syslogd 1.5.0#2ubuntu6: restart.
Nov  6 13:08:22 lehe kernel: Inspecting /boot/System.map-2.6.27-15-generic
Nov  6 13:08:22 lehe kernel: Cannot find map file.
Nov  6 13:08:22 lehe kernel: Loaded 50605 symbols from 102 modules.



As I see these files, I have not found any info at Nov 6 12:18 and any info about overheating of CPU.

---

### Post by jmundinger on 2009-11-07
A couple of suggestions - if you are having problems with high temperatures, you might have an accumulation of dust around the heat sink.  You also might think about getting a cooling stand for your laptop.

---

### Post by flylehe on 2009-11-07
Thanks! I Have tried this before but crashing down still happens when running big program or opening some webpages with heavy video and flash. I now want to find if there is some logging info about the reason causing the crashing down, overheating or other reasons. I saw somewhere online someone saying
> 
 The syslog showed the following error message:

    ACPI: Critical trip point
    Critical temperature reached (100 C), shutting down. 

I just wonder where I can get such info just as he did?

> **jmundinger said:**
> A couple of suggestions - if you are having problems with high temperatures, you might have an accumulation of dust around the heat sink.  You also might think about getting a cooling stand for your laptop.

---

### Post by LewRockwell on 2009-11-07
> **flylehe said:**
> I Have tried this before but crashing down still happens when running big program or opening some webpages with heavy video and flash. I now want to find if there is some logging info about the reason causing the crashing down, overheating or other reasons.

ok, so this isn't the first time your laptop has overheated then

we opened up a laptop a while back and hair, dust, and such was completely covering the cooling fins on the processor heat sink

not to mention the thermal compound was dried out and worthless

no cooling could even take place

unless it's new, we would definitely check that out

.

---

