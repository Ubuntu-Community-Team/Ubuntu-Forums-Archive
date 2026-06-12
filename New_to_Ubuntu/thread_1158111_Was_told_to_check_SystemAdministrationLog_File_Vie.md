---
title: "Was told to check System/Administration/Log File Viewer"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by faron45 on 2009-05-13
I cannot for the life of me find this ! I think I may have accidently changed my menues at one point & I don't think they are quite the same as everybody elses Xubuntu anymore.I sure would like to go back to the old style that when I ask for help from all of you floks things would be a bit easier ! Arrrrrrrrrghhhhhhhhhhh !!

---

### Post by Elfy on 2009-05-13
Not any idea where they are in the xubuntu menus, but regardless you'll be able to get at them from thunar 

```
thunar /var/log
```

The logs which appear in the ubuntu log file viewer are - auth, messages,syslog. You should be able to read them with a text editor

Hope that at least get's you to look in the logs.

---

### Post by faron45 on 2009-05-13
Eeeeeeeeeeek !! Argh !! Aaaaaahhhhhh !! Well,thanks forestpixie.I tried the thunar /var/log thing & that indeed open up a whole new can of worms.Now I've got like 30 logs staring me in the face ! Ohhhhhhh my God ! WHICH ones do I look at ?? Hmph !

---

### Post by Elfy on 2009-05-13
> The logs which appear in the ubuntu log file viewer are - auth, messages,syslog. You should be able to read them with a text editorThese - what did you have to look for?

---

### Post by faron45 on 2009-05-13
Looking for messages I keep seeing upon shutting down that appear to be error messages.But,these messages just fly by so quickly that I cannot read them & awhile back I tried the pause/break key & that just isn't going to do the job.My comp continues to have like multiple issues & I just want the darn thing to run properly & I think this could be a part of the problem.

---

### Post by Elfy on 2009-05-13
Check messages - you should be able to see where you've rebooted/shutdown the logs are timestamped

---

### Post by faron45 on 2009-05-13
Hmmmmmmmm.Wonder what happened to my last post.I replied to post #4 but,somehow,it didn't take,I guess.See what I mean Pix ? This pc just has so many issues it's driving me insane !! What I am looking for is what I keep seeing upon shut down of this comp.....I keep seeing error messages that some things are not shutting down properly or are just not operating properly.

 Ohhhhhhh,Lord ! Ohhhhhhhh my God !! Geez !!! There's my other message !

---

### Post by faron45 on 2009-05-13
This is what I get when I do this ...thunar /var/log

log-file manager

file:///var/log/Xorg.21.log.old

file:///var/log/Xorg.21.log

file:///var/log/Xorg.20.log.old

file:///var/log/Xorg.20.log

file:///var/log/Xorg.0.log.old

file:///var/log/Xorg.0.log

file:///var/log/wvdialconf.log

file:///var/log/wtmp.1

file:///var/log/wtmp

file:///var/log/user.log.3.gz

file:///var/log/user.log.2.gz

file:///var/log/user.log.1.gz

file:///var/log/user.log.0

file:///var/log/user.log

file:///var/log/udev

file:///var/log/syslog.6.gz

file:///var/log/syslog.5.gz

file:///var/log/syslog.4.gz

file:///var/log/syslog.3.gz

file:///var/log/syslog.2.gz

file:///var/log/syslog.1.gz

file:///var/log/syslog.0

file:///var/log/syslog

file:///var/log/scrollkeeper.log.2

file:///var/log/scrollkeeper.log.1

file:///var/log/scrollkeeper.log

file:///var/log/pycentral.log

file:///var/log/pm-suspend.log

file:///var/log/messages.3.gz

file:///var/log/messages.2.gz

file:///var/log/messages.1.gz

file:///var/log/messages.0

file:///var/log/messages

file:///var/log/mail.warn

file:///var/log/mail.log

file:///var/log/mail.info

file:///var/log/mail.err

file:///var/log/lpr.log

file:///var/log/lastlog

file:///var/log/kern.log.3.gz

file:///var/log/kern.log.2.gz

file:///var/log/kern.log.1.gz

file:///var/log/kern.log.0

file:///var/log/kern.log

file:///var/log/fontconfig.log

file:///var/log/faillog

file:///var/log/dpkg.log.11.gz

file:///var/log/dpkg.log.10.gz

file:///var/log/dpkg.log.9.gz

file:///var/log/dpkg.log.8.gz

file:///var/log/dpkg.log.7.gz

file:///var/log/dpkg.log.6.gz

file:///var/log/dpkg.log.5.gz

file:///var/log/dpkg.log.4.gz

file:///var/log/dpkg.log.3.gz

file:///var/log/dpkg.log.2.gz

file:///var/log/dpkg.log.1

file:///var/log/dpkg.log

file:///var/log/dmesg.4.gz

file:///var/log/dmesg.3.gz

file:///var/log/dmesg.2.gz

file:///var/log/dmesg.1.gz

file:///var/log/dmesg.0

file:///var/log/dmesg

file:///var/log/debug.3.gz

file:///var/log/debug.2.gz

file:///var/log/debug.1.gz

file:///var/log/debug.0

file:///var/log/debug

file:///var/log/daemon.log.3.gz

file:///var/log/daemon.log.2.gz

file:///var/log/daemon.log.1.gz

file:///var/log/daemon.log.0

file:///var/log/daemon.log

file:///var/log/btmp.1

file:///var/log/btmp

file:///var/log/bootstrap.log

file:///var/log/boot

file:///var/log/auth.log.3.gz

file:///var/log/auth.log.2.gz

file:///var/log/auth.log.1.gz

file:///var/log/auth.log.0

file:///var/log/auth.log

file:///var/log/acpid.4.gz

file:///var/log/acpid.3.gz

file:///var/log/acpid.2.gz

file:///var/log/acpid.1.gz

file:///var/log/acpid

file:///var/log/unattended-upgrades

file:///var/log/tor

file:///var/log/samba

file:///var/log/news

file:///var/log/installer

file:///var/log/gdm

file:///var/log/fsck

file:///var/log/dist-upgrade

file:///var/log/cups

file:///var/log/clamav

file:///var/log/apt

file:///var/log/apparmor

---

### Post by faron45 on 2009-05-13
This is some of the stuff I see when I opened file:///var/log/messages


May 13 09:39:54 cybertek kernel: [   16.574889] SELinux:  Disabled at boot.
May 13 09:39:54 cybertek kernel: [   16.574958] Failure registering capabilities with primary security module
May 13 09:39:54 cybertek kernel: [   17.908103] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 13 09:39:54 cybertek kernel: [   17.914078] SMP motherboard not detected.
May 13 09:39:54 cybertek kernel: [   17.914087] Local APIC not detected. Using dummy APIC emulation.
May 13 09:39:54 cybertek kernel: [   17.980441] ACPI: Power Resource [URP1] (off)
May 13 09:39:54 cybertek kernel: [   17.980567] ACPI: Power Resource [URP2] (off)
May 13 09:39:54 cybertek kernel: [   17.980684] ACPI: Power Resource [FDDP] (off)
May 13 09:39:54 cybertek kernel: [   17.980799] ACPI: Power Resource [LPTP] (off)
May 13 09:39:54 cybertek kernel: [   17.995850] PnPBIOS: Disabled by ACPI PNP
May 13 09:39:54 cybertek kernel: [   29.715817] sd 0:0:0:0: [sda] Write Protect is off
May 13 09:39:54 cybertek kernel: [   29.715916] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 13 09:39:54 cybertek kernel: [   47.852064] iTCO_wdt: No card detected
May 13 09:39:54 cybertek kernel: [   69.006431] No dock devices found.
May 13 09:39:55 cybertek kernel: [   72.832570] apm: BIOS not found.
May 13 09:40:03 cybertek dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 13 09:40:06 cybertek dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 13 09:40:06 cybertek dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 13 09:40:06 cybertek dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
May 13 09:40:08 cybertek kernel: [   85.672002] lo: Disabled Privacy Extensions
May 13 09:43:59 cybertek kernel: [   92.103283] ^Idriver to use reclaim_buffers_idlelocked() instead.
May 13 09:43:59 cybertek kernel: [   92.103288] ^II will go on reclaiming the buffers anyway.

---

### Post by kanikilu on 2009-05-13
I don't remember if it's installed in Xubuntu, but I think the GUI log viewer you are looking for is called **gnome-system-log**.

---

### Post by faron45 on 2009-05-13
I'm soooooo sorry for the long thread guys & gals.

---

