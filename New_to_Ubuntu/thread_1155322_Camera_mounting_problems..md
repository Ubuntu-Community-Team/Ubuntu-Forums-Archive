---
title: "Camera mounting problems."
date: 2009-05-10
forum: New to Ubuntu
---

### Post by LyonTamer on 2009-05-10
I have 8.01 upgrade from 7.10 on a Dell Inspiron 8000. The camera is an Insignia NS-DSC7P09. This camera was automounting with no problems until the day the batteries died during a video upload onto Youtube. The computer no longer mounts it. I have tried reformatting the memory card in the camera, which did not help the computer situation (although it did erase all my videos!). I have plugged the camera into a Windows XP machine and  Mac OS X machine, both of which mounted the camera just fine. How do I get this Ubuntu machine to again automount the camera?

Edit: I think the dying of the batteries led to an improper dismount, obviously because the camera died without warning. It does have a driver installation disk but it is written in exe format, useless on this machine. So how do I correct whatever went wrong with the improper dismount?

---

### Post by LyonTamer on 2009-05-10
Trying some things I'm reading in other camera-problem threads. :)

Running lsusb in terminal gave this:

Bus 001 Device 003: ID 0733:7340 ViewQuest Technologies, Inc.

Running lspci gave this:

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
03:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)
03:00.1 Serial controller: Xircom Cardbus Ethernet + 56k Modem (rev 03)

The camera used to mount as a mass media drive, with the icon on the desktop. F-spot also opened it. Now neither F-spot or digikam will detect the camera.

Rebooting with the camera plugged in and turned on didn't work.

User priveledges is already checked for access to external drives.

Update Manager keeps alerting me and tries to update things, but cannot, gives me an error message, but I have not seen where to change the preferences for it. There is no Preferences button in Update Manager. (This is detailed in another thread I posted.) Does the camera problem possibly have something to do with this update failing?

I have gotten out my old camera (Toshiba PDR-3320), plugged it in and it automounted with no problems. So it's just this computer with this Insignia camera.

---

### Post by LyonTamer on 2009-05-15
Bump!:D

---

### Post by LyonTamer on 2009-05-16
Just tried reinstalling Ubuntu 7.10 and upgrading to 8.04. Still no luck with the camera mounting.

Isn't there a code to manually mount the thing in terminal?

---

### Post by LyonTamer on 2009-05-16
Ran pmount and sudo mount and got...

lenathelaptop@lenathelaptop:~$ pmount
Printing mounted removable devices:
To get a short help, run pmount -h
lenathelaptop@lenathelaptop:~$ sudo mount
[sudo] password for lenathelaptop: 
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/sdb1 type vfat (rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,fmask=0177,dmask=0077,iocharset=utf8 )
/dev/sdc1 on /media/sdc1 type vfat (rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,fmask=0177,dmask=0077,iocharset=utf8 )
lenathelaptop@lenathelaptop:~$ sudo mount /dev/sdb1 
mount: special device /dev/sdb1 does not exist
lenathelaptop@lenathelaptop:~$ sudo mount /dev/sdb2
mount: can't find /dev/sdb2 in /etc/fstab or /etc/mtab
lenathelaptop@lenathelaptop:~$ 

Guess I'll quit reading other camera-problem threads, none of it is working. (More likely, I'm not doing something right.) Please can someone out there help me with this, I'd really appreciate it. I have no further ideas except for replacing my brand new camera. :mad:

---

### Post by anewguy on 2009-05-16
Have you tried running f-spot from the command line as su?  It's possible the device is being owned by root:

sudo f-spot

Dave :)

---

### Post by LyonTamer on 2009-05-16
I have not. Update Manager prompted me one step at a time beginning at 7.10, to upgrade to Jaunty and since doing so, the camera has mounted. :)

That is I did a clean reinstall of 7.10 from my CD and then upgraded, one version at a time, to 9.04.

---

### Post by LyonTamer on 2009-11-21
Hi! I've had a hard drive problem, got a new one, installed 7.10 and upgraded to 8.04. Would rather not do more upgrading as I'm waiting for 9.10 to come in the mail. :)

I once again have the same problem, with the same camera. I tried sudo f-spot, with the camera on, and got this:

michelle@michelle-laptop:~$ sudo f-spot
[sudo] password for michelle: 

(/usr/lib/f-spot/f-spot.exe:7316): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.16.6/gobject/gtype.c:2248: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/f-spot/f-spot.exe:7316): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(/usr/lib/f-spot/f-spot.exe:7316): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Stacktrace:

  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0x00004>
  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0xffffffff>
  at GConf.Client..ctor () <0x0003b>
  at FSpot.GConfPreferenceBackend.get_Client () <0x0001f>
  at FSpot.GConfPreferenceBackend.AddNotify (string,FSpot.NotifyChangedHandler) <0x00033>
  at FSpot.Preferences.get_Backend () <0x000ea>
  at FSpot.Preferences.Get (string) <0x00074>
  at FSpot.Driver.Main (string[]) <0x00144>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x816b20a]
	f-spot [0x807de81]
	[0xb7f14440]
	/usr/lib/libgconf-2.so.4(gconf_client_get_default+0xa9) [0xb6c259f9]
	[0xb7755e20]
	[0xb775589c]
	[0xb7755838]
	[0xb7755784]
	[0xb7755653]
	[0xb775519d]
	[0xb775193d]
	[0xb77511c4]
	f-spot(mono_runtime_exec_main+0x10e) [0x809c68e]
	f-spot(mono_runtime_run_main+0x173) [0x809c933]
	f-spot(mono_main+0x6a9) [0x805acd9]
	f-spot [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ccb450]
	f-spot [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c8d8e0 (LWP 7316)]
[New Thread 0xb7201b90 (LWP 7318)]
[New Thread 0xb7225b90 (LWP 7317)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f14410 in __kernel_vsyscall ()
  3 Thread 0xb7225b90 (LWP 7317)  0xb7f14410 in __kernel_vsyscall ()
  2 Thread 0xb7201b90 (LWP 7318)  0xb7f14410 in __kernel_vsyscall ()
  1 Thread 0xb7c8d8e0 (LWP 7316)  0xb7f14410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7225b90 (LWP 7317)):
#0  0xb7f14410 in __kernel_vsyscall ()
#1  0xb7e37196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7e2f4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d8be5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb7201b90 (LWP 7318)):
#0  0xb7f14410 in __kernel_vsyscall ()
#1  0xb7e33aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317b5 in ?? ()
#10 0xb7e2f4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d8be5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c8d8e0 (LWP 7316)):
#0  0xb7f14410 in __kernel_vsyscall ()
#1  0xb7d84881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eb41d4 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7eb459c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b2a5 in ?? ()
#5  0x0807de81 in ?? ()
#6  <signal handler called>
#7  0xb6c22423 in ?? () from /usr/lib/libgconf-2.so.4
#8  0xb6c259f9 in gconf_client_get_default () from /usr/lib/libgconf-2.so.4
#9  0xb7755e20 in ?? ()
#10 0xb775589c in ?? ()
#11 0xb7755838 in ?? ()
#12 0xb7755784 in ?? ()
#13 0xb7755653 in ?? ()
#14 0xb775519d in ?? ()
#15 0xb775193d in ?? ()
#16 0xb77511c4 in ?? ()
#17 0x0809c68e in mono_runtime_exec_main ()
#18 0x0809c933 in mono_runtime_run_main ()
#19 0x0805acd9 in mono_main ()
#20 0x0805a122 in ?? ()
#21 0xb7ccb450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#22 0x0805a091 in ?? ()
#0  0xb7f14410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
michelle@michelle-laptop:~$ 

What does this mean?

My other camera, an Olympus, mounts and f-spot starts without any problems. I want the new camera to mount, though, because it takes videos and the old one doesn't. What do I do?

---

