---
title: "cant' start xorg"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by outleradam on 2010-08-06
I have a XBMC Live setup.  It is ubuntu which just runs XBMC.  The problem I am having is that my Xorg server won't start unless I have freshly installed my drivers.  

```
xbmc@xbmc-live:~$ xbmc
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Error: unable to open display 
FEH.py: cannot connect to X server 

```So that doesn't work, I tried this
```

xbmc@xbmc-live:~$ xinit xbmc


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux xbmc-live 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=ebca974e-57ed-421f-b303-4724da2ed090 ro crashkernel=384M-2G:64M,2G-:128M splash quiet xbmc=autostart,nodiskmount,setvolume loglevel=0
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  6 18:46:01 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Error: API mismatch: the NVIDIA kernel module has version 195.36.24,
but this NVIDIA driver component has version 256.44.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
(EE) Aug 06 18:46:02 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Aug 06 18:46:02 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Aug 06 18:46:02 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xbmc@xbmc-live:~$ 

```Which does not work either.  

I am running the latest downloaded drivers from nVidia, and the 2.6.32-24-generic kernel.  

XBMC works when I have freshly installed the nVidia drivers, but then when I reboot it does not work anymore. What can I do?

---

### Post by chopinhauer on 2010-08-06
> **outleradam said:**
> 
```

Error: API mismatch: the NVIDIA kernel module has version 195.36.24,
but this NVIDIA driver component has version 256.44.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.

```

If you decided not to use the NVIDIA drivers that come with Ubuntu, you should go all the way and also compile the kernel part of the driver. There is a [manual](https://help.ubuntu.com/community/NvidiaManual) for that.

---

### Post by outleradam on 2010-08-06
I tried that.  It didn't work.  

I get this when I reinstall the drivers.  It works.

```
root@xbmc-live:~# xinit xbmc


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux xbmc-live 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=ebca974e-57ed-421f-b303-4724da2ed090 ro crashkernel=384M-2G:64M,2G-:128M splash quiet xbmc=autostart,nodiskmount,setvolume loglevel=0
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  6 20:42:45 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
WARNING: All config files need .conf: /etc/modprobe.d/lirc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/lirc-blacklist, it will be ignored in a future release.
^C
waiting for X server to shut down xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":0.0"
 ddxSigGiveUp: Closing log

```

then I reboot and get the previous error.  I can't figure out how to make it work all of the time.  I followed the directions  but I keep ending up with this:

```

root@xbmc-live:~# xinit xbmc


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux xbmc-live 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=ebca974e-57ed-421f-b303-4724da2ed090 ro crashkernel=384M-2G:64M,2G-:128M splash quiet xbmc=autostart,nodiskmount,setvolume loglevel=0
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  6 20:44:40 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Error: API mismatch: the NVIDIA kernel module has version 195.36.24,
but this NVIDIA driver component has version 256.44.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
(EE) Aug 06 20:44:40 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Aug 06 20:44:40 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Aug 06 20:44:40 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

---

### Post by WelshChris on 2010-08-06
Any info. in /var/log/kern.log?


Chris -> Sleep

---

### Post by outleradam on 2010-08-07
I don't know what I did, but now it starts with xinit xbmc every time.   It will not start by calling xbmc.bin or xbmc.  only with xinit.  I dunno..  it just works.   Oh well, it's good enough.

---

