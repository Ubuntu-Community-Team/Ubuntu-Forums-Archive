---
title: "Unresponsive After LogIn"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by ashton88 on 2009-05-14
Hello!

After GUI logging in to Intrepid the system becomes unresponsive.  CTRL-ALT-1,2,3.. or CTRL-ALT-BackSPce do not work.  The screen remains blank and coloured the same as the login gui (rather then the user background colour).

**What happened:**

1. I recently installed emerald and it has been working fine, through reboots and such.  This may or may not be related.

2. I noticed that my window decorator was no longer decorating: the title bar was missing on all the windows.

3. I closed everything down and did a CTRL-ALT-BCKSP.  The log in GUI screen came up fine.  Since I have auto-login set it waited 10 seconds and auto logged me in.

4. Then nothing.  My screen stayed the same color as the background of my login GUI screen.  The mouse cursor was there, and I could move it around.  However when I hit CTRL-ALT-2 to bring up a tty session nothing happened.  I tried CTRL-ALT-1 thru 6 and nothing.  CTRL-ALT-BACKSPACE also doesn't work.

5.  I kvm'd to another computer and ssh'd in.  sudo /etc/init.d/gdm stop [OK].  But the screen remained unresponsive.

6. Thinking it must be emerald given that this is the only thing that has changed recently I did a sudo apt-get uninstall emerald and rebooted.  That didn't help.

I don't know what information would be useful, but below I have put a little.  I will pull anything else that would be helpful.  The local machine is curiously unresponsive.

Many many (many) thanks in advance to any and all!

I am using Intrepid.

Here is a ps -ae:

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  137 ?        00:00:00 cqueue
  141 ?        00:00:00 kseriod
  184 ?        00:00:00 pdflush
  185 ?        00:00:00 pdflush
  186 ?        00:00:00 kswapd0
  226 ?        00:00:00 aio/0
  227 ?        00:00:00 aio/1
 1171 ?        00:00:00 kstriped
 1179 ?        00:00:00 ksnapd
 1410 ?        00:00:00 ksuspend_usbd
 1411 ?        00:00:00 khubd
 1505 ?        00:00:00 ata/0
 1507 ?        00:00:00 ata/1
 1509 ?        00:00:00 ata_aux
 2233 ?        00:00:00 scsi_eh_0
 2234 ?        00:00:00 scsi_eh_1
 2255 ?        00:00:00 scsi_eh_2
 2256 ?        00:00:00 scsi_eh_3
 2487 ?        00:00:00 kjournald
 2997 ?        00:00:00 udevd
 3511 ?        00:00:00 kpsmoused
 5036 ?        00:00:00 kjournald
 5037 ?        00:00:00 kjournald
 5254 ?        00:00:00 portmap
 5276 ?        00:00:00 rpc.statd
 5296 ?        00:00:00 rpciod/0
 5297 ?        00:00:00 rpciod/1
 5311 ?        00:00:00 nfsiod
 5321 ?        00:00:00 rpc.idmapd
 5496 tty4     00:00:00 getty
 5497 tty5     00:00:00 getty
 5500 tty2     00:00:00 getty
 5501 tty3     00:00:00 getty
 5507 tty6     00:00:00 getty
 5714 ?        00:00:00 acpid
 5769 ?        00:00:00 kondemand/0
 5771 ?        00:00:00 kondemand/1
 5854 ?        00:00:00 syslogd
 5911 ?        00:00:00 dd
 5913 ?        00:00:00 klogd
 5954 ?        00:00:00 dbus-daemon
 5976 ?        00:00:00 avahi-daemon
 5977 ?        00:00:00 avahi-daemon
 6018 ?        00:00:00 sshd
 6114 ?        00:00:00 cupsd
 6260 ?        00:00:00 gpm
 6293 ?        00:00:00 chipcardd4
 6294 ?        00:00:05 chipcardd4
 6390 ?        00:00:00 lockd
 6391 ?        00:00:00 nfsd4
 6392 ?        00:00:00 nfsd
 6393 ?        00:00:00 nfsd
 6394 ?        00:00:00 nfsd
 6395 ?        00:00:00 nfsd
 6396 ?        00:00:00 nfsd
 6397 ?        00:00:00 nfsd
 6398 ?        00:00:00 nfsd
 6399 ?        00:00:00 nfsd
 6403 ?        00:00:00 rpc.mountd
 6481 ?        00:00:00 nmbd
 6482 ?        00:00:00 nmbd
 6493 ?        00:00:00 smbd
 6524 ?        00:00:00 smbd
 6532 ?        00:00:00 snmpd
 6629 ?        00:00:00 winbindd
 6637 ?        00:00:00 winbindd
 6686 ?        00:00:01 hald
 6692 ?        00:00:00 console-kit-dae
 6693 ?        00:00:00 hald-runner
 6794 ?        00:00:00 hald-addon-inpu
 6808 ?        00:00:00 hald-addon-cpuf
 6809 ?        00:00:00 hald-addon-acpi
 6835 ?        00:00:00 hald-addon-stor
 6868 ?        00:00:00 hald-addon-stor
 6900 ?        00:00:00 bluetoothd
 6913 ?        00:00:00 btaddconn
 6914 ?        00:00:00 btdelconn
 6933 ?        00:00:00 krfcommd
 6971 ?        00:00:00 NetworkManager
 6983 ?        00:00:00 wpa_supplicant
 6985 ?        00:00:00 nm-system-setti
 7072 ?        00:00:00 gdm
 7140 ?        00:00:00 system-tools-ba
 7183 ?        00:00:00 atd
 7217 ?        00:00:00 cron
 7356 ?        00:00:00 dhclient
 7861 ?        00:00:00 ntpd
 8039 tty1     00:00:00 getty
 8295 ?        00:00:00 gdm
 8319 tty7     00:00:01 Xorg
 8378 ?        00:00:00 x-session-manag
 8461 ?        00:00:00 ssh-agent
 8464 ?        00:00:00 dbus-launch
 8465 ?        00:00:00 dbus-daemon
 8468 ?        00:00:00 pulseaudio
 8471 ?        00:00:00 gconf-helper
 8473 ?        00:00:00 gconfd-2
 8482 ?        00:00:00 seahorse-agent
 8487 ?        00:00:00 gvfsd
 8488 ?        00:00:00 gnome-keyring-d
 8494 ?        00:00:00 gvfs-fuse-daemo
 8502 ?        00:00:00 gnome-keyring-d
 8503 ?        00:00:00 gnome-settings-
 8505 ?        00:00:00 compiz
 8515 ?        00:00:00 xrdb <defunct>
 8547 ?        00:00:00 xrdb <defunct>
 8594 ?        00:00:00 glxinfo
 8595 ?        00:00:00 egrep
 8621 ?        00:00:00 sshd
 8655 ?        00:00:00 sshd
 8659 pts/0    00:00:00 bash
 8979 pts/0    00:00:00 ps

What other information would be helpful?

---

### Post by ashton88 on 2009-05-14
I can always rely on this forum!

It never fails, if I'm stumped I post something on here and minutes later I figure it out.

I rebooted with the "recovery" kernel option, and was presented with a list of "recovery" options (go figure).  One of them said, "Fix X server".. I thought that sounded good, so I went for it.

So it rewrote me Xorg.conf, which was apparently the problem.  Don't know why or how, but I'm up and running again.

Thanks!

---

