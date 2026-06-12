---
title: "Rebooting after shutdown"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by paddyng on 2009-10-21
Installed Ubuntu Server 8.04LTS in an old PC to learn Linux. Managed to connect to server from a WinXP machine via SSH.

Tried to shutdown the server remotely using the command below.

sudo shutdown -h now

I'm trying to do the equivalent of a shutdown from the GUI but the server shuts down then reboot.

Am I using the correct command? What am I doing wrong?

Thanks

Paddy

---

### Post by Ravernomina on 2009-10-21
this might be a dumb one but try add this to it


```

Sudo shutdown -h now

sudo halt

sudo poweroff

sudo shutdown -h 0 

```


try these commands see how they go... (:


Btw Welcome to the forums and welcome to the LINUX community. You will like it better here (:

---

### Post by houstonbofh on 2009-10-21
"sudo shutdown -P now"

From the help...

```
lee@boat:~$ shutdown --help
Usage: shutdown [OPTION]... TIME [MESSAGE]
Bring the system down.

Options:
  -r                          reboot after shutdown
  -h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)
  -c                          cancel a running shutdown
  -k                          only send warnings, don't shutdown
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit


```

---

### Post by paddyng on 2009-10-21
Tried the various shutdown switches from the man page.

-h and -P  --> reboot
-H         --> system halts without powering down

I wonder if something is translating shutdown as reboot, due to this being a server OS.

For now I'll just have to manually power the box down, until I work out why.

---

### Post by houstonbofh on 2009-10-22
Go into your BIOS and check the power management.  You probably have it all the way off, so the OS can not power off the machine.

---

