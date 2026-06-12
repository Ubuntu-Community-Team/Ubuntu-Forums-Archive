---
title: "Massive Log Files (UFW)"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by Petrovic on 2011-08-21
Sorry about this one guys and gals. This is purely my fault due to lack of understanding and ignorance, and now I ask your help.
Used 10.10, then upgraded to 11.04 when it came out through the update manager. I'm running an old Intel P4 2ghz with 1gb ram, so she's not the quickest out the gates, and I've had to use the 'Ubuntu Classic' option (so no Ubuntu One or any extras of the like) but still chugs along and does the job. I've a dual boot drive, sharing with XP with about 14gb per partition. Know bust all about terminal, but am always willing to learn.
As I use Zone Alarm when using xp, I can take note of the network activity while using it, which is a very small amount of the time in comparison. Anyway, while browsing through the latest logs of attacks on my machine, I noticed a couple of addresses that were hammering one port in particular. When I logged out of windows, and back into Ubuntu, I did some (very brief I will admit) searching and came across some recommendations for ufw firewall configuration tool in the hopes I could keep some information for later studies. 
So, I installed firewall configuration, enabled it, opened preferences and told ufw to do full logging, and gufw options to Listening Ports and Show Notifications. Now, however, I have some HUGE log files within /var/log. My Kern.log is 1.4gb, Kern.log.1 is 3.3gb. sys.log ~900mb, Syslog.1 is 1.1gb, ufw.log 1.4gb and ufw.log.1 1.8gb. I can't open the files in gedit as my computer can't handle it, but from the little I could see, it all looks like ufw log info (within kern.log)
I would like to undo the hogging of the logging space if I could, but don't know how or where to start. I read a little about others having massive log files, but wasn't able to get a clear answer, or at least one that I could understand :redface: 
I've since turned ufw logging to off, but this hasn't helped return the space. I would just outright delete them, but as I have no idea what the consequences would be, this hasn't been done.
Thanks in advance for any assistance offered.

---

### Post by lidex on 2011-08-22
Use your terminal to see the contents of the directory containing the log files. Terminal="Applications->Accessories->Terminal"
(in classic). Change the working directory by entering this command (use the return/enter key to execute):
```
cd /var/log
```
Now list the contents:
```
ls
```
Here's my output:
```
alternatives.log       bootstrap.log    jockey.log.3.gz        syslog.4.gz
alternatives.log.1     btmp             jockey.log.4.gz        syslog.5.gz
alternatives.log.2.gz  btmp.1           kern.log               syslog.6.gz
apparmor               ConsoleKit       kern.log.1             syslog.7.gz
apport.log             cups             kern.log.2.gz          udev
apport.log.1           dist-upgrade     kern.log.3.gz          ufw.log
apport.log.2.gz        dmesg            kern.log.4.gz          unattended-upgrades
apport.log.3.gz        dmesg.0          lastlog                wtmp
apport.log.4.gz        dmesg.1.gz       lightdm                wtmp.1
apport.log.5.gz        dmesg.2.gz       mail.err               Xorg.0.log
apport.log.6.gz        dmesg.3.gz       mail.log               Xorg.0.log.old
apport.log.7.gz        dmesg.4.gz       news                   Xorg.1.log
apt                    dpkg.log         pm-powersave.log       Xorg.1.log.old
aptitude               dpkg.log.1       pm-powersave.log.1     Xorg.2.log
aptitude.1.gz          dpkg.log.2.gz    pm-powersave.log.2.gz  Xorg.2.log.old
aptitude.2.gz          faillog          pm-suspend.log         Xorg.3.log
auth.log               fontconfig.log   pycentral.log          Xorg.3.log.old
auth.log.1             fsck             samba                  Xorg.4.log
auth.log.2.gz          gdm              speech-dispatcher      Xorg.4.log.old
auth.log.3.gz          installer        syslog                 Xorg.5.log
auth.log.4.gz          jockey.log       syslog.1               Xorg.5.log.old
boot                   jockey.log.1     syslog.2.gz
boot.log               jockey.log.2.gz  syslog.3.gz

```
Use the remove command (rm) with sudo to delete the file in question appending the filename shown in previous output. Ex:
```
sudo rm syslog.3.gz
```
The log files are safe to remove.

---

### Post by Petrovic on 2011-08-22
Alright, I believe I can do that. 
Is there a risk in deleting .log files with regards to lost information? I wouldn't imagine it being a problem, being only a log file, but like to be safer than sorry.
The logs I intend to remove are kern.log, kern.log.1, syslog, ufw.log and, ufw.log.1. The ufw logs should be fine, but unsure on the kernal and syslog. 
Again, taa.

---

### Post by lidex on 2011-08-22
> **Petrovic said:**
> Alright, I believe I can do that. 
Is there a risk in deleting .log files with regards to lost information? I wouldn't imagine it being a problem, being only a log file, but like to be safer than sorry.
The logs I intend to remove are kern.log, kern.log.1, syslog, ufw.log and, ufw.log.1. The ufw logs should be fine, but unsure on the kernal and syslog. 
Again, taa.

Those files are safe to remove, the system doesn't read from them, its just output.

---

### Post by Petrovic on 2011-08-22
Aces. Is done and done. 
Cheers.

---

### Post by CVGH on 2011-08-22
Any way to do this with cron and a script?

---

### Post by sisco311 on 2011-08-22
Log files are 'rotated' by logrotate. System specific logs are configured in /etc/logrotate.conf other logs have config files in /etc/logrotate.d

For configuration options, see:
```
man logrotate
```

For example, if you want to rotate ufw.log when it grows bigger than 300M, you can edit /etc/logrotate.d/ufw to look like this:
```
/var/log/ufw.log
{
        rotate 4
        **size 300M**
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                invoke-rc.d rsyslog reload >/dev/null 2>&1 || true
        endscript
}

```

---

### Post by bodhi.zazen on 2011-08-22
If you are not going to read your logs, turn them off ;)

---

### Post by denbagusjkt on 2012-10-23
> If you are not going to read your logs, turn them off :wink:

how i can do that on ubuntu 12.04

---

