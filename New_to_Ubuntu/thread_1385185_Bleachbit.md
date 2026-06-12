---
title: "Bleachbit"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by jnmjr on 2010-01-19
Hi, tried using this program to clean-up after a few months of using Karmic OS, it seemed to do well but gave me these errors:

 Errno 13] Permission denied: '/var/log/mail.info.1' /var/log/mail.info.1
[Errno 13] Permission denied: '/var/log/auth.log.1' /var/log/auth.log.1
[Errno 13] Permission denied: '/var/log/syslog.1' /var/log/syslog.1
[Errno 13] Permission denied: '/var/log/user.log.1' /var/log/user.log.1
[Errno 13] Permission denied: '/var/log/kern.log.1' /var/log/kern.log.1
[Errno 13] Permission denied: '/var/log/messages.1' /var/log/messages.1
[Errno 13] Permission denied: '/var/log/dpkg.log.1' /var/log/dpkg.log.1
[Errno 13] Permission denied: '/var/log/debug.1' /var/log/debug.1
[Errno 13] Permission denied: '/var/log/mail.log.1' /var/log/mail.log.1
[Errno 13] Permission denied: '/var/log/lpr.log.1' /var/log/lpr.log.1
[Errno 13] Permission denied: '/var/log/pm-powersave.log.1' /var/log/pm-powersave.log.1
[Errno 13] Permission denied: '/var/log/pm-suspend.log.1' /var/log/pm-suspend.log.1
[Errno 13] Permission denied: '/var/log/mail.err.1' /var/log/mail.err.1
[Errno 13] Permission denied: '/var/log/dmesg.0' /var/log/dmesg.0
[Errno 13] Permission denied: '/var/log/daemon.log.1' /var/log/daemon.log.1
[Errno 13] Permission denied: '/var/log/jockey.log.1' /var/log/jockey.log.1
[Errno 13] Permission denied: '/var/log/mail.warn.1' /var/log/mail.warn.1
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.1' /var/log/ConsoleKit/history.1
[Errno 13] Permission denied: '/var/log/syslog.2.gz' /var/log/syslog.2.gz
[Errno 13] Permission denied: '/var/log/mail.warn.3.gz' /var/log/mail.warn.3.gz
[Errno 13] Permission denied: '/var/log/mail.err.3.gz' /var/log/mail.err.3.gz
[Errno 13] Permission denied: '/var/log/auth.log.3.gz' /var/log/auth.log.3.gz
[Errno 13] Permission denied: '/var/log/daemon.log.4.gz' /var/log/daemon.log.4.gz
[Errno 13] Permission denied: '/var/log/daemon.log.2.gz' /var/log/daemon.log.2.gz
[Errno 13] Permission denied: '/var/log/lpr.log.2.gz' /var/log/lpr.log.2.gz
[Errno 13] Permission denied: '/var/log/syslog.6.gz' /var/log/syslog.6.gz
[Errno 13] Permission denied: '/var/log/lpr.log.3.gz' /var/log/lpr.log.3.gz
[Errno 13] Permission denied: '/var/log/debug.4.gz' /var/log/debug.4.gz
[Errno 13] Permission denied: '/var/log/wtmp.1.gz' /var/log/wtmp.1.gz
[Errno 13] Permission denied: '/var/log/syslog.3.gz' /var/log/syslog.3.gz
[Errno 13] Permission denied: '/var/log/dmesg.1.gz' /var/log/dmesg.1.gz
[Errno 13] Permission denied: '/var/log/syslog.7.gz' /var/log/syslog.7.gz
[Errno 13] Permission denied: '/var/log/user.log.3.gz' /var/log/user.log.3.gz
[Errno 13] Permission denied: '/var/log/btmp.1.gz' /var/log/btmp.1.gz
[Errno 13] Permission denied: '/var/log/messages.3.gz' /var/log/messages.3.gz
[Errno 13] Permission denied: '/var/log/mail.log.4.gz' /var/log/mail.log.4.gz
[Errno 13] Permission denied: '/var/log/kern.log.2.gz' /var/log/kern.log.2.gz
[Errno 13] Permission denied: '/var/log/dmesg.4.gz' /var/log/dmesg.4.gz
[Errno 13] Permission denied: '/var/log/mail.info.3.gz' /var/log/mail.info.3.gz
[Errno 13] Permission denied: '/var/log/user.log.2.gz' /var/log/user.log.2.gz
[Errno 13] Permission denied: '/var/log/syslog.4.gz' /var/log/syslog.4.gz
[Errno 13] Permission denied: '/var/log/syslog.5.gz' /var/log/syslog.5.gz
[Errno 13] Permission denied: '/var/log/mail.info.4.gz' /var/log/mail.info.4.gz
[Errno 13] Permission denied: '/var/log/mail.err.2.gz' /var/log/mail.err.2.gz
[Errno 13] Permission denied: '/var/log/messages.2.gz' /var/log/messages.2.gz
[Errno 13] Permission denied: '/var/log/mail.log.2.gz' /var/log/mail.log.2.gz
[Errno 13] Permission denied: '/var/log/auth.log.2.gz' /var/log/auth.log.2.gz
[Errno 13] Permission denied: '/var/log/dmesg.3.gz' /var/log/dmesg.3.gz
[Errno 13] Permission denied: '/var/log/mail.err.4.gz' /var/log/mail.err.4.gz
[Errno 13] Permission denied: '/var/log/messages.4.gz' /var/log/messages.4.gz
[Errno 13] Permission denied: '/var/log/lpr.log.4.gz' /var/log/lpr.log.4.gz
[Errno 13] Permission denied: '/var/log/aptitude.1.gz' /var/log/aptitude.1.gz
[Errno 13] Permission denied: '/var/log/mail.info.2.gz' /var/log/mail.info.2.gz
[Errno 13] Permission denied: '/var/log/user.log.4.gz' /var/log/user.log.4.gz
[Errno 13] Permission denied: '/var/log/debug.2.gz' /var/log/debug.2.gz
[Errno 13] Permission denied: '/var/log/kern.log.4.gz' /var/log/kern.log.4.gz
[Errno 13] Permission denied: '/var/log/daemon.log.3.gz' /var/log/daemon.log.3.gz
[Errno 13] Permission denied: '/var/log/dmesg.2.gz' /var/log/dmesg.2.gz
[Errno 13] Permission denied: '/var/log/jockey.log.2.gz' /var/log/jockey.log.2.gz
[Errno 13] Permission denied: '/var/log/debug.3.gz' /var/log/debug.3.gz
[Errno 13] Permission denied: '/var/log/auth.log.4.gz' /var/log/auth.log.4.gz
[Errno 13] Permission denied: '/var/log/mail.warn.2.gz' /var/log/mail.warn.2.gz
[Errno 13] Permission denied: '/var/log/kern.log.3.gz' /var/log/kern.log.3.gz
[Errno 13] Permission denied: '/var/log/mail.warn.4.gz' /var/log/mail.warn.4.gz
[Errno 13] Permission denied: '/var/log/mail.log.3.gz' /var/log/mail.log.3.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.7.gz' /var/log/cups/page_log.7.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.3.gz' /var/log/cups/error_log.3.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.3.gz' /var/log/cups/access_log.3.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.1.gz' /var/log/cups/error_log.1.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.1.gz' /var/log/cups/access_log.1.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.3.gz' /var/log/cups/page_log.3.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.6.gz' /var/log/cups/error_log.6.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.2.gz' /var/log/cups/page_log.2.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.7.gz' /var/log/cups/access_log.7.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.7.gz' /var/log/cups/error_log.7.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.2.gz' /var/log/cups/access_log.2.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.4.gz' /var/log/cups/error_log.4.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.5.gz' /var/log/cups/error_log.5.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.4.gz' /var/log/cups/access_log.4.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.5.gz' /var/log/cups/page_log.5.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.6.gz' /var/log/cups/page_log.6.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.4.gz' /var/log/cups/page_log.4.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.2.gz' /var/log/cups/error_log.2.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.6.gz' /var/log/cups/access_log.6.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.5.gz' /var/log/cups/access_log.5.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.1.gz' /var/log/cups/page_log.1.gz
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.3.gz' /var/log/ConsoleKit/history.3.gz
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.2.gz' /var/log/ConsoleKit/history.2.gz
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.5.gz' /var/log/ConsoleKit/history.5.gz
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.4.gz' /var/log/ConsoleKit/history.4.gz
[Errno 13] Permission denied: '/var/log/installer/initial-status.gz' /var/log/installer/initial-status.gz
[Errno 13] Permission denied: '/var/log/apt/term.log.1.gz' /var/log/apt/term.log.1.gz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-3.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-3.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-2.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-2.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-6.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-6.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-4.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-4.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-1.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-1.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100117-1.tgz' /var/log/bootchart/My-Desktop-karmic-20100117-1.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-5.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-5.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100119-1.tgz' /var/log/bootchart/My-Desktop-karmic-20100119-1.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100117-2.tgz' /var/log/bootchart/My-Desktop-karmic-20100117-2.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100117-3.tgz' /var/log/bootchart/My-Desktop-karmic-20100117-3.tgz
[Errno 13] Permission denied: '/var/log/Xorg.0.log.old' /var/log/Xorg.0.log.old
[Errno 13] Permission denied: '/var/log/Xorg.1.log.old' /var/log/Xorg.1.log.old

Looks like these are all log files....Are they that important that cannot be cleaned out?
I must say I may still have a windows mentality, that is, about cleaning out the hard drive, maybe Linux doesn't need it, any opinions out there? THX.

---

### Post by presence1960 on 2010-01-19
> **jnmjr said:**
> Hi, tried using this program to clean-up after a few months of using Karmic OS, it seemed to do well but gave me these errors:

```
 Errno 13] Permission denied: '/var/log/mail.info.1' /var/log/mail.info.1
[Errno 13] Permission denied: '/var/log/auth.log.1' /var/log/auth.log.1
[Errno 13] Permission denied: '/var/log/syslog.1' /var/log/syslog.1
[Errno 13] Permission denied: '/var/log/user.log.1' /var/log/user.log.1
[Errno 13] Permission denied: '/var/log/kern.log.1' /var/log/kern.log.1
[Errno 13] Permission denied: '/var/log/messages.1' /var/log/messages.1
[Errno 13] Permission denied: '/var/log/dpkg.log.1' /var/log/dpkg.log.1
[Errno 13] Permission denied: '/var/log/debug.1' /var/log/debug.1
[Errno 13] Permission denied: '/var/log/mail.log.1' /var/log/mail.log.1
[Errno 13] Permission denied: '/var/log/lpr.log.1' /var/log/lpr.log.1
[Errno 13] Permission denied: '/var/log/pm-powersave.log.1' /var/log/pm-powersave.log.1
[Errno 13] Permission denied: '/var/log/pm-suspend.log.1' /var/log/pm-suspend.log.1
[Errno 13] Permission denied: '/var/log/mail.err.1' /var/log/mail.err.1
[Errno 13] Permission denied: '/var/log/dmesg.0' /var/log/dmesg.0
[Errno 13] Permission denied: '/var/log/daemon.log.1' /var/log/daemon.log.1
[Errno 13] Permission denied: '/var/log/jockey.log.1' /var/log/jockey.log.1
[Errno 13] Permission denied: '/var/log/mail.warn.1' /var/log/mail.warn.1
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.1' /var/log/ConsoleKit/history.1
[Errno 13] Permission denied: '/var/log/syslog.2.gz' /var/log/syslog.2.gz
[Errno 13] Permission denied: '/var/log/mail.warn.3.gz' /var/log/mail.warn.3.gz
[Errno 13] Permission denied: '/var/log/mail.err.3.gz' /var/log/mail.err.3.gz
[Errno 13] Permission denied: '/var/log/auth.log.3.gz' /var/log/auth.log.3.gz
[Errno 13] Permission denied: '/var/log/daemon.log.4.gz' /var/log/daemon.log.4.gz
[Errno 13] Permission denied: '/var/log/daemon.log.2.gz' /var/log/daemon.log.2.gz
[Errno 13] Permission denied: '/var/log/lpr.log.2.gz' /var/log/lpr.log.2.gz
[Errno 13] Permission denied: '/var/log/syslog.6.gz' /var/log/syslog.6.gz
[Errno 13] Permission denied: '/var/log/lpr.log.3.gz' /var/log/lpr.log.3.gz
[Errno 13] Permission denied: '/var/log/debug.4.gz' /var/log/debug.4.gz
[Errno 13] Permission denied: '/var/log/wtmp.1.gz' /var/log/wtmp.1.gz
[Errno 13] Permission denied: '/var/log/syslog.3.gz' /var/log/syslog.3.gz
[Errno 13] Permission denied: '/var/log/dmesg.1.gz' /var/log/dmesg.1.gz
[Errno 13] Permission denied: '/var/log/syslog.7.gz' /var/log/syslog.7.gz
[Errno 13] Permission denied: '/var/log/user.log.3.gz' /var/log/user.log.3.gz
[Errno 13] Permission denied: '/var/log/btmp.1.gz' /var/log/btmp.1.gz
[Errno 13] Permission denied: '/var/log/messages.3.gz' /var/log/messages.3.gz
[Errno 13] Permission denied: '/var/log/mail.log.4.gz' /var/log/mail.log.4.gz
[Errno 13] Permission denied: '/var/log/kern.log.2.gz' /var/log/kern.log.2.gz
[Errno 13] Permission denied: '/var/log/dmesg.4.gz' /var/log/dmesg.4.gz
[Errno 13] Permission denied: '/var/log/mail.info.3.gz' /var/log/mail.info.3.gz
[Errno 13] Permission denied: '/var/log/user.log.2.gz' /var/log/user.log.2.gz
[Errno 13] Permission denied: '/var/log/syslog.4.gz' /var/log/syslog.4.gz
[Errno 13] Permission denied: '/var/log/syslog.5.gz' /var/log/syslog.5.gz
[Errno 13] Permission denied: '/var/log/mail.info.4.gz' /var/log/mail.info.4.gz
[Errno 13] Permission denied: '/var/log/mail.err.2.gz' /var/log/mail.err.2.gz
[Errno 13] Permission denied: '/var/log/messages.2.gz' /var/log/messages.2.gz
[Errno 13] Permission denied: '/var/log/mail.log.2.gz' /var/log/mail.log.2.gz
[Errno 13] Permission denied: '/var/log/auth.log.2.gz' /var/log/auth.log.2.gz
[Errno 13] Permission denied: '/var/log/dmesg.3.gz' /var/log/dmesg.3.gz
[Errno 13] Permission denied: '/var/log/mail.err.4.gz' /var/log/mail.err.4.gz
[Errno 13] Permission denied: '/var/log/messages.4.gz' /var/log/messages.4.gz
[Errno 13] Permission denied: '/var/log/lpr.log.4.gz' /var/log/lpr.log.4.gz
[Errno 13] Permission denied: '/var/log/aptitude.1.gz' /var/log/aptitude.1.gz
[Errno 13] Permission denied: '/var/log/mail.info.2.gz' /var/log/mail.info.2.gz
[Errno 13] Permission denied: '/var/log/user.log.4.gz' /var/log/user.log.4.gz
[Errno 13] Permission denied: '/var/log/debug.2.gz' /var/log/debug.2.gz
[Errno 13] Permission denied: '/var/log/kern.log.4.gz' /var/log/kern.log.4.gz
[Errno 13] Permission denied: '/var/log/daemon.log.3.gz' /var/log/daemon.log.3.gz
[Errno 13] Permission denied: '/var/log/dmesg.2.gz' /var/log/dmesg.2.gz
[Errno 13] Permission denied: '/var/log/jockey.log.2.gz' /var/log/jockey.log.2.gz
[Errno 13] Permission denied: '/var/log/debug.3.gz' /var/log/debug.3.gz
[Errno 13] Permission denied: '/var/log/auth.log.4.gz' /var/log/auth.log.4.gz
[Errno 13] Permission denied: '/var/log/mail.warn.2.gz' /var/log/mail.warn.2.gz
[Errno 13] Permission denied: '/var/log/kern.log.3.gz' /var/log/kern.log.3.gz
[Errno 13] Permission denied: '/var/log/mail.warn.4.gz' /var/log/mail.warn.4.gz
[Errno 13] Permission denied: '/var/log/mail.log.3.gz' /var/log/mail.log.3.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.7.gz' /var/log/cups/page_log.7.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.3.gz' /var/log/cups/error_log.3.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.3.gz' /var/log/cups/access_log.3.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.1.gz' /var/log/cups/error_log.1.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.1.gz' /var/log/cups/access_log.1.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.3.gz' /var/log/cups/page_log.3.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.6.gz' /var/log/cups/error_log.6.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.2.gz' /var/log/cups/page_log.2.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.7.gz' /var/log/cups/access_log.7.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.7.gz' /var/log/cups/error_log.7.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.2.gz' /var/log/cups/access_log.2.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.4.gz' /var/log/cups/error_log.4.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.5.gz' /var/log/cups/error_log.5.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.4.gz' /var/log/cups/access_log.4.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.5.gz' /var/log/cups/page_log.5.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.6.gz' /var/log/cups/page_log.6.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.4.gz' /var/log/cups/page_log.4.gz
[Errno 13] Permission denied: '/var/log/cups/error_log.2.gz' /var/log/cups/error_log.2.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.6.gz' /var/log/cups/access_log.6.gz
[Errno 13] Permission denied: '/var/log/cups/access_log.5.gz' /var/log/cups/access_log.5.gz
[Errno 13] Permission denied: '/var/log/cups/page_log.1.gz' /var/log/cups/page_log.1.gz
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.3.gz' /var/log/ConsoleKit/history.3.gz
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.2.gz' /var/log/ConsoleKit/history.2.gz
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.5.gz' /var/log/ConsoleKit/history.5.gz
[Errno 13] Permission denied: '/var/log/ConsoleKit/history.4.gz' /var/log/ConsoleKit/history.4.gz
[Errno 13] Permission denied: '/var/log/installer/initial-status.gz' /var/log/installer/initial-status.gz
[Errno 13] Permission denied: '/var/log/apt/term.log.1.gz' /var/log/apt/term.log.1.gz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-3.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-3.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-2.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-2.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-6.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-6.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-4.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-4.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-1.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-1.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100117-1.tgz' /var/log/bootchart/My-Desktop-karmic-20100117-1.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100118-5.tgz' /var/log/bootchart/My-Desktop-karmic-20100118-5.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100119-1.tgz' /var/log/bootchart/My-Desktop-karmic-20100119-1.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100117-2.tgz' /var/log/bootchart/My-Desktop-karmic-20100117-2.tgz
[Errno 13] Permission denied: '/var/log/bootchart/My-Desktop-karmic-20100117-3.tgz' /var/log/bootchart/My-Desktop-karmic-20100117-3.tgz
[Errno 13] Permission denied: '/var/log/Xorg.0.log.old' /var/log/Xorg.0.log.old
[Errno 13] Permission denied: '/var/log/Xorg.1.log.old' /var/log/Xorg.1.log.old
```

Looks like these are all log files....Are they that important that cannot be cleaned out?
I must say I may still have a windows mentality, that is, about cleaning out the hard drive, maybe Linux doesn't need it, any opinions out there? THX.

When it comes to Linux forget what you know about windows and become like a sponge to absorb new ideas and new ways of doing things. 

If security is your concern here is a good read: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

P.S next time you paste a lot of text on here highlight the text after pasting it and then click the # sign on the toolbar to place code tags around the text as I did above in your quoted text.

---

### Post by spiderbatdad on 2010-01-19
The permission denied error are due to the process try to clear root owned files. Indeed they are old logs that have been zipped. You would have to run the program as root from the command line...Personally I would be wary of doing that. You don't need this program. Firefox already has cache, cookie, history clearing. If you want to clear old logs, do so manually.

---

### Post by MelDJ on 2010-01-19
run applications-system tools-bleacbit as administrator rather than the normal bleachbit

---

### Post by jnmjr on 2010-01-19
THX all for your input.

---

