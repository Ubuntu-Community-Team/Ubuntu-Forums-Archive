---
title: "Automatic reboot every morning"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by reaganf2 on 2011-06-22
My laptop with Ubuntu 11.04 x86 installed keeps restarting automatically by itself every morning before I wake up...

I tried checking CPU temperatures, but they all seem normal (about 70 degrees C)...

Is there any way I can check a system log to see what has been causing these reboots...?

Any help will be appreciated...

---

### Post by Beacon11 on 2011-06-22
I'd check out /var/log/messages first.

---

### Post by dargaud on 2011-06-22
Check your BIOS settings as well, some can boot at a fixed time, although it shouldn't _re_boot.

---

### Post by reaganf2 on 2011-06-22
Thanks for the quick replies, but my /var/log/messages file is empty...
I tried looking in my BIOS settings, but there's no option related to booting/re-booting at a particular time...
My processor temperatures are almost constantly around 70 degrees C (critical temperature for my Intel Core 2 Duo processors is 100 degrees C)... I really doubt this could be temperature related, but I will slow down my processors to check just in case...

Recently, while I was messing around with the "Users and Groups" settings, I gave myself complete user privileges and didn't know what the default options to be ticked were... So I left them at all options ticked... This is all I've recently changed settings-wise... Could this by any chance be causing the re-boots...?

---

### Post by dargaud on 2011-06-22
What do you mean "/var/log/messages empty" ? Do you mean 'no relevant info' or do you mean size 0 ? The latter is not normal. 

Also, check your crontab "crontab -l" and the system's crontab "ll /etc/cron.daily/" in case something crashes daily bad enough to bring the system down.

---

### Post by reaganf2 on 2011-06-22
The size of the /var/log/messages file is zero... When I open it in gedit, it's empty... There are a couple of other files called messages.1 and messages.2.gz, but when I open them, all the lines have dates in April...

When I run the command "crontab -l" in a terminal, it says "no crontab for reagan"...

On keying "ll /etc/cron.daily/", it gave me the following output:
total 92
drwxr-xr-x   2 root root  4096 2011-06-17 09:29 ./
drwxr-xr-x 149 root root 12288 2011-06-23 07:06 ../
-rwxr-xr-x   1 root root   311 2010-06-20 13:41 0anacron*
-rwxr-xr-x   1 root root   189 2010-10-01 17:47 apport*
-rwxr-xr-x   1 root root 15255 2011-04-07 16:43 apt*
-rwxr-xr-x   1 root root   502 2010-05-27 01:32 bsdmainutils*
-rwxr-xr-x   1 root root   256 2010-09-08 15:22 dpkg*
-rwxr-xr-x   1 root root  7623 2011-06-14 00:06 google-chrome*
lrwxrwxrwx   1 root root    45 2011-06-17 09:29 google-talkplugin -> /opt/google/talkplugin/cron/google-talkplugin*
-rwxr-xr-x   1 root root   341 2011-03-13 06:07 logrotate*
-rwxr-xr-x   1 root root  1335 2010-08-17 20:40 man-db*
-rwxr-xr-x   1 root root   606 2010-03-24 15:46 mlocate*
-rwxr-xr-x   1 root root  1154 2010-08-07 04:20 ntp*
-rwxr-xr-x   1 root root   249 2011-02-21 05:45 passwd*
-rw-r--r--   1 root root   102 2010-08-25 04:31 .placeholder
-rwxr-xr-x   1 root root  2149 2009-06-16 18:42 popularity-contest*
-rwxr-xr-x   1 root root   383 2011-03-04 23:30 samba*
-rwxr-xr-x   1 root root  3594 2010-08-25 04:31 standard*

---

### Post by mikenev on 2011-06-22
It is odd that your /var/log/messages is size 0. Have you run out of disk space? That could cause some very strange problems.

---

### Post by reaganf2 on 2011-06-22
No, I have 4.1 Gigs of space left on my Ubuntu partition...

The only other common thing about the reboots is that I have deluge running everytime it reboots... I usually leave my comp with only deluge open overnight...

---

### Post by jtarin on 2011-06-22
Are you connected to any kind of network? Is wake-up-on-lan enabled in the bios?

---

### Post by reaganf2 on 2011-06-23
Yes, I'm connected on a wireless network and wake-up-on-lan is enabled in my BIOS... Could this be causing the reboots...? Should I disable it in BIOS...?

---

### Post by jtarin on 2011-06-23
> **reaganf2 said:**
> Yes, I'm connected on a wireless network and wake-up-on-lan is enabled in my BIOS... Could this be causing the reboots...? Should I disable it in BIOS...?Try disable and see. I'm only guessing and pointing. We have to eliminate things one at a time. :p
Next time it happens upon reboot issue the command ```
cat /var/log/syslog
```note the time of reboot and look through the syslog and post the part beginning to just before the rebbot and the next 20 lines.

---

### Post by reaganf2 on 2011-06-23
Okay, I've just disabled wake-up-on-lan... I noticed that an option called wake-up-on-wireless-lan was present and disabled... I've left this at disabled... I'll post back results after I've played around with these settings a bit...

Thanks again for the help... Really appreciate it...

---

### Post by jtarin on 2011-06-23
> **reaganf2 said:**
> Okay, I've just disabled wake-up-on-lan... I noticed that an option called wake-up-on-wireless-lan was present and disabled... I've left this at disabled... I'll post back results after I've played around with these settings a bit...

Thanks again for the help... Really appreciate it...Your welcom. Note my edit to last post.

Change the option on updates from "download and install" to "download and ask me whether to install"....sometimes it wants to reboot after updating.

---

### Post by idoitprone on 2011-06-23
> **reaganf2 said:**
> Thanks for the quick replies, but my /var/log/messages file is empty...
I tried looking in my BIOS settings, but there's no option related to booting/re-booting at a particular time...
My processor temperatures are almost constantly around 70 degrees C (critical temperature for my Intel Core 2 Duo processors is 100 degrees C)... I really doubt this could be temperature related, but I will slow down my processors to check just in case...

 that is very odd. does it change at all?

If it doesnt

take a look at 

```
lsmod | grep -i "coretemp"

```
i wonder if you do have the kernel module. I just wanted to know so the forum does not have to go on a wild chase if the answer if just simple

---

### Post by LowSky on 2011-06-23
4.1GB isn't much free space. make sure your /tmp folder isn't filling up with random garbage files and wasting space.

Generally if a PC is resetting without notice it usually a hardware issue. Since you said it is occurring with deluge running I'm guessing it could be the PCI card that is handling your internet getting too hot, or shorting out, and the motherboard goes into safety mode and reboots to save the system..

just a thought

---

### Post by reaganf2 on 2011-06-23
@jtarin: Yes, the automatic update thing did occur to me earlier... I changed it to "only notify me about updates" but it did not stop the reboots... I've now set it to "only download automatically"... Will see how that works...
The next time it reboots, I'll put up the listing you asked for...

@idoitprone: The command when run in a terminal gives me the following output: coretemp               13283  0 
I have only 4.1 GB free since I created only a small ubuntu partition while installing (6 GB i think)... I don't store any files in my ubuntu partition... I access them from my mounted windows partition and my external hard drive... The size of my /tmp folder as of now is only 36 kB...

---

### Post by reaganf2 on 2011-06-28
Sorry I've been away the last couple of days... Just back and my laptop just pulled another reboot on me...
I've posted the contents of the /var/log/syslog file as requested:

Jun 28 09:52:40 Reagz-Toshiba rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="807" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun 28 09:52:59 Reagz-Toshiba anacron[1035]: Job `cron.daily' terminated
Jun 28 09:52:59 Reagz-Toshiba anacron[1035]: Normal exit (1 job run)
Jun 28 10:07:12 Reagz-Toshiba AptDaemon: INFO: Initializing daemon
Jun 28 10:12:12 Reagz-Toshiba AptDaemon: INFO: Quitting due to inactivity
Jun 28 10:12:12 Reagz-Toshiba AptDaemon: INFO: Shutdown was requested
Jun 28 10:17:01 Reagz-Toshiba CRON[3031]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 28 10:23:16 Reagz-Toshiba sudo: pam_sm_authenticate: Called
Jun 28 10:23:16 Reagz-Toshiba sudo: pam_sm_authenticate: username = [reagan]
Jun 28 10:53:44 Reagz-Toshiba kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 28 10:53:44 Reagz-Toshiba rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="811" x-info="http://www.rsyslog.com"] (re)start
Jun 28 10:53:44 Reagz-Toshiba rsyslogd: rsyslogd's groupid changed to 103
Jun 28 10:53:44 Reagz-Toshiba rsyslogd: rsyslogd's userid changed to 101
Jun 28 10:53:44 Reagz-Toshiba rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfcde000 (usable)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bfcde000 - 00000000bfce9000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bfce9000 - 00000000bfd43000 (usable)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bfd43000 - 00000000bfd46000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bfd46000 - 00000000bfdbb000 (usable)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bfdbb000 - 00000000bfdbf000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bfdbf000 - 00000000bfe69000 (usable)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bfe69000 - 00000000bfebf000 (ACPI NVS)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bfebf000 - 00000000bff00000 (ACPI data)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] DMI 2.4 present.
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] DMI: TOSHIBA Satellite A300/Base Board Product Name, BIOS 1.30 03/19/2008
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] last_pfn = 0xbfe69 max_arch_pfn = 0x100000
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] MTRR default type: uncachable
Jun 28 10:53:44 Reagz-Toshiba kernel: [    0.000000] MTRR fixed ranges enabled:

---

### Post by reaganf2 on 2011-06-28
Another strange occurence... When I was booted into my Windows Vista partition the other day, I experienced a similar reboot when the computer was left inactive for a while...

---

### Post by jtarin on 2011-06-28
Syslog time before reboot would be more helpful. In Windows you can use event manager to track this.....just note the time.

---

### Post by reaganf2 on 2011-06-28
The syslog file begins from where I've posted... There's nothing before it...

The computer rebooted at 10:53 when I'd stepped away...

---

### Post by jtarin on 2011-06-28
> **reaganf2 said:**
> The syslog file begins from where I've posted... There's nothing before it...

The computer rebooted at 10:53 when I'd stepped away...Check the win event manager if you were booted into win at that time. It's a hardware problem or bios setting.

---

### Post by reaganf2 on 2011-06-28
Right now when it happened, I was booted into Ubuntu... However a couple of days ago, it did happen when I was booted into Windows too... I don't remember the exact date and time this happened though... Could you please tell me how I can access the win event manager to try to find it nevertheless...?

---

### Post by jtarin on 2011-06-28
```
To start Event Viewer by using the Windows interface

    Click the Start button.

    Click Control Panel.

    Click System and Maintenance.

    Click Administrative Tools.

    Double-click Event Viewer.

```
```
To start Event Viewer by using a command line

    Open a command prompt. To open a command prompt, click Start, click All Programs, click Accessories and then click Command Prompt.

    Type eventvwr.
```

---

