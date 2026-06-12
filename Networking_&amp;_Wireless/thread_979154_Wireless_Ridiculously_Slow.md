---
title: "Wireless Ridiculously Slow"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by scathmandra on 2008-11-11
Using a Dell Inspiron 1501, standard 802.11g wireless card with the BCM43xx driver. Strange thing is, my wireless download speed is ridiculously low--my usual is about 15 kb/s. When I have a wired ethernet connection, it's 1 mb/s. Any explanation for this?

---

### Post by iponeverything on 2008-11-11
you might get an idea of what is going on by taking a peek in /var/log/syslog and /var/log/message.

---

### Post by scathmandra on 2008-11-12
I've looked into it, but it's gobbledegook to me...

/var/log/syslog:

```
Nov 12 17:22:27 Nicodemus syslogd 1.5.0#2ubuntu6: restart.
Nov 12 17:22:27 Nicodemus anacron[5859]: Job `cron.daily' terminated
Nov 12 17:22:27 Nicodemus anacron[5859]: Normal exit (1 job run)
Nov 12 17:22:58 Nicodemus kernel: [ 2855.584024] APIC error on CPU0: 40(40)
Nov 12 17:22:58 Nicodemus kernel: [ 2855.584036] APIC error on CPU1: 40(40)
Nov 12 17:24:06 Nicodemus kernel: [ 2923.600053] APIC error on CPU1: 40(40)
Nov 12 17:24:06 Nicodemus kernel: [ 2923.600059] APIC error on CPU0: 40(40)
Nov 12 17:25:59 Nicodemus kernel: [ 3036.804024] APIC error on CPU0: 40(40)
Nov 12 17:25:59 Nicodemus kernel: [ 3036.804037] APIC error on CPU1: 40(40)
Nov 12 17:30:01 Nicodemus /USR/SBIN/CRON[11864]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov 12 17:32:15 Nicodemus kernel: [ 3413.241076] APIC error on CPU0: 40(40)
Nov 12 17:32:15 Nicodemus kernel: [ 3413.241091] APIC error on CPU1: 40(40)
Nov 12 17:32:42 Nicodemus gdm[8349]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:32:42 Nicodemus kernel: [ 3440.163394] npviewer.bin[11581]: segfault at f5602044 ip 00000000f78769f0 sp 00000000ff929d34 error 4 in libpthread-2.8.90.so[f786f000+15000]
Nov 12 17:32:49 Nicodemus acpid: client connected from 12162[0:0] 
Nov 12 17:32:51 Nicodemus kernel: [ 3449.102584] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:32:51 Nicodemus kernel: [ 3449.108485] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:32:51 Nicodemus kernel: [ 3449.108502] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:33:04 Nicodemus pulseaudio[12273]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:33:04 Nicodemus pulseaudio[12275]: pid.c: Stale PID file, overwriting.
Nov 12 17:33:04 Nicodemus pulseaudio[12275]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:33:04 Nicodemus pulseaudio[12275]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:33:04 Nicodemus pulseaudio[12275]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:33:04 Nicodemus pulseaudio[12275]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:33:10 Nicodemus x-session-manager[12212]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:33:21 Nicodemus x-session-manager[12212]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:33:22 Nicodemus pulseaudio[12275]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:33:22 Nicodemus pulseaudio[12275]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:33:25 Nicodemus python: hp-systray(init)[12415]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:33:28 Nicodemus anacron[12495]: Anacron 2.3 started on 2008-11-12
Nov 12 17:33:29 Nicodemus anacron[12495]: Normal exit (0 jobs run)
Nov 12 17:33:29 Nicodemus kernel: [ 3486.745884] CPU0 attaching NULL sched-domain.
Nov 12 17:33:29 Nicodemus kernel: [ 3486.745932] CPU1 attaching NULL sched-domain.
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760574] CPU0 attaching sched-domain:
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760593]  domain 0: span 0-1 level CPU
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760601]   groups: 0 1
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760611]   domain 1: span 0-1 level NODE
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760617]    groups: 0-1
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760629] CPU1 attaching sched-domain:
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760634]  domain 0: span 0-1 level CPU
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760639]   groups: 1 0
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760646]   domain 1: span 0-1 level NODE
Nov 12 17:33:29 Nicodemus kernel: [ 3486.760651]    groups: 0-1
Nov 12 17:35:23 Nicodemus gdm[12147]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:35:25 Nicodemus acpid: client connected from 12739[0:0] 
Nov 12 17:35:27 Nicodemus kernel: [ 3605.008740] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:35:27 Nicodemus kernel: [ 3605.015968] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:35:27 Nicodemus kernel: [ 3605.015989] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:35:35 Nicodemus gdm[12719]: WARNING: Couldn't authenticate user 
Nov 12 17:35:41 Nicodemus pulseaudio[12852]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:35:41 Nicodemus pulseaudio[12854]: pid.c: Stale PID file, overwriting.
Nov 12 17:35:41 Nicodemus pulseaudio[12854]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:35:41 Nicodemus pulseaudio[12854]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:35:41 Nicodemus pulseaudio[12854]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:35:41 Nicodemus pulseaudio[12854]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:35:42 Nicodemus x-session-manager[12791]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:35:52 Nicodemus x-session-manager[12791]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:35:53 Nicodemus pulseaudio[12854]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:35:53 Nicodemus pulseaudio[12854]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:35:54 Nicodemus python: hp-systray(init)[12991]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:35:54 Nicodemus anacron[13071]: Anacron 2.3 started on 2008-11-12
Nov 12 17:35:54 Nicodemus anacron[13071]: Normal exit (0 jobs run)
Nov 12 17:35:54 Nicodemus kernel: [ 3631.822842] CPU0 attaching NULL sched-domain.
Nov 12 17:35:54 Nicodemus kernel: [ 3631.822869] CPU1 attaching NULL sched-domain.
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841171] CPU0 attaching sched-domain:
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841185]  domain 0: span 0-1 level CPU
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841189]   groups: 0 1
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841193]   domain 1: span 0-1 level NODE
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841196]    groups: 0-1
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841207] CPU1 attaching sched-domain:
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841209]  domain 0: span 0-1 level CPU
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841212]   groups: 1 0
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841215]   domain 1: span 0-1 level NODE
Nov 12 17:35:54 Nicodemus kernel: [ 3631.841217]    groups: 0-1
Nov 12 17:37:28 Nicodemus kernel: [ 3725.828901] compiz.real[12970] trap stack segment ip:41024e sp:7fff5d590340 error:0
Nov 12 17:37:28 Nicodemus gdm[12719]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:37:30 Nicodemus acpid: client connected from 13250[0:0] 
Nov 12 17:37:32 Nicodemus kernel: [ 3729.544813] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:37:32 Nicodemus kernel: [ 3729.552299] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:37:32 Nicodemus kernel: [ 3729.552319] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:37:38 Nicodemus pulseaudio[13357]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:37:38 Nicodemus pulseaudio[13359]: pid.c: Stale PID file, overwriting.
Nov 12 17:37:38 Nicodemus pulseaudio[13359]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:37:38 Nicodemus pulseaudio[13359]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:37:38 Nicodemus pulseaudio[13359]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:37:38 Nicodemus pulseaudio[13359]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:37:39 Nicodemus x-session-manager[13296]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:37:50 Nicodemus x-session-manager[13296]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:37:50 Nicodemus pulseaudio[13359]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:37:50 Nicodemus pulseaudio[13359]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:37:51 Nicodemus python: hp-systray(init)[13496]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:37:52 Nicodemus anacron[13591]: Anacron 2.3 started on 2008-11-12
Nov 12 17:37:52 Nicodemus anacron[13591]: Normal exit (0 jobs run)
Nov 12 17:37:52 Nicodemus kernel: [ 3749.657809] CPU0 attaching NULL sched-domain.
Nov 12 17:37:52 Nicodemus kernel: [ 3749.657837] CPU1 attaching NULL sched-domain.
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685155] CPU0 attaching sched-domain:
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685166]  domain 0: span 0-1 level CPU
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685169]   groups: 0 1
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685174]   domain 1: span 0-1 level NODE
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685176]    groups: 0-1
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685182] CPU1 attaching sched-domain:
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685184]  domain 0: span 0-1 level CPU
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685186]   groups: 1 0
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685189]   domain 1: span 0-1 level NODE
Nov 12 17:37:52 Nicodemus kernel: [ 3749.685191]    groups: 0-1
Nov 12 17:38:30 Nicodemus gdm[13235]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:38:30 Nicodemus kernel: [ 3788.281101] compiz.real[13475] trap stack segment ip:41024e sp:7fff8e002db0 error:0
Nov 12 17:38:31 Nicodemus bonobo-activation-server (bernard-13683): could not associate with desktop session: Failed to connect to socket /tmp/dbus-MBCoe2PWG5: Connection refused
Nov 12 17:38:32 Nicodemus acpid: client connected from 13713[0:0] 
Nov 12 17:38:34 Nicodemus kernel: [ 3791.929798] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:38:34 Nicodemus kernel: [ 3791.935090] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:38:34 Nicodemus kernel: [ 3791.935110] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:38:40 Nicodemus pulseaudio[13820]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:38:40 Nicodemus pulseaudio[13822]: pid.c: Stale PID file, overwriting.
Nov 12 17:38:40 Nicodemus pulseaudio[13822]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:38:40 Nicodemus pulseaudio[13822]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:38:40 Nicodemus pulseaudio[13822]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:38:40 Nicodemus pulseaudio[13822]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:38:40 Nicodemus kernel: [ 3798.408105] APIC error on CPU0: 40(40)
Nov 12 17:38:40 Nicodemus kernel: [ 3798.408118] APIC error on CPU1: 40(40)
Nov 12 17:38:41 Nicodemus x-session-manager[13759]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:38:51 Nicodemus x-session-manager[13759]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:38:52 Nicodemus pulseaudio[13822]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:38:52 Nicodemus pulseaudio[13822]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:38:53 Nicodemus python: hp-systray(init)[13960]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:38:53 Nicodemus anacron[14058]: Anacron 2.3 started on 2008-11-12
Nov 12 17:38:53 Nicodemus anacron[14058]: Normal exit (0 jobs run)
Nov 12 17:38:54 Nicodemus kernel: [ 3811.477623] CPU0 attaching NULL sched-domain.
Nov 12 17:38:54 Nicodemus kernel: [ 3811.477648] CPU1 attaching NULL sched-domain.
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497144] CPU0 attaching sched-domain:
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497155]  domain 0: span 0-1 level CPU
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497158]   groups: 0 1
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497163]   domain 1: span 0-1 level NODE
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497166]    groups: 0-1
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497172] CPU1 attaching sched-domain:
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497174]  domain 0: span 0-1 level CPU
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497176]   groups: 1 0
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497179]   domain 1: span 0-1 level NODE
Nov 12 17:38:54 Nicodemus kernel: [ 3811.497181]    groups: 0-1
Nov 12 17:40:01 Nicodemus /USR/SBIN/CRON[14159]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov 12 17:41:01 Nicodemus kernel: [ 3939.300023] APIC error on CPU1: 40(40)
Nov 12 17:41:01 Nicodemus kernel: [ 3939.300035] APIC error on CPU0: 40(40)
Nov 12 17:42:01 Nicodemus gdm[13699]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:42:01 Nicodemus kernel: [ 3999.394475] compiz.real[13938] trap stack segment ip:41024e sp:7fff42beb9a0 error:0
Nov 12 17:42:02 Nicodemus bonobo-activation-server (bernard-14329): could not associate with desktop session: Failed to connect to socket /tmp/dbus-1XfejqF3cn: Connection refused
Nov 12 17:42:04 Nicodemus acpid: client connected from 14372[0:0] 
Nov 12 17:42:05 Nicodemus kernel: [ 4003.276838] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:42:05 Nicodemus kernel: [ 4003.285071] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:42:05 Nicodemus kernel: [ 4003.285089] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:42:16 Nicodemus pulseaudio[14483]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:42:16 Nicodemus pulseaudio[14485]: pid.c: Stale PID file, overwriting.
Nov 12 17:42:16 Nicodemus pulseaudio[14485]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:42:16 Nicodemus pulseaudio[14485]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:42:16 Nicodemus pulseaudio[14485]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:42:16 Nicodemus pulseaudio[14485]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:42:17 Nicodemus x-session-manager[14422]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:42:27 Nicodemus x-session-manager[14422]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:42:28 Nicodemus pulseaudio[14485]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:42:28 Nicodemus pulseaudio[14485]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:42:28 Nicodemus python: hp-systray(init)[14621]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:42:29 Nicodemus anacron[14707]: Anacron 2.3 started on 2008-11-12
Nov 12 17:42:29 Nicodemus anacron[14707]: Normal exit (0 jobs run)
Nov 12 17:42:29 Nicodemus kernel: [ 4026.822276] CPU0 attaching NULL sched-domain.
Nov 12 17:42:29 Nicodemus kernel: [ 4026.822307] CPU1 attaching NULL sched-domain.
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841036] CPU0 attaching sched-domain:
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841053]  domain 0: span 0-1 level CPU
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841056]   groups: 0 1
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841061]   domain 1: span 0-1 level NODE
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841064]    groups: 0-1
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841073] CPU1 attaching sched-domain:
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841074]  domain 0: span 0-1 level CPU
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841077]   groups: 1 0
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841080]   domain 1: span 0-1 level NODE
Nov 12 17:42:29 Nicodemus kernel: [ 4026.841082]    groups: 0-1
Nov 12 17:43:57 Nicodemus gdm[14352]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:43:57 Nicodemus kernel: [ 4115.029118] compiz.real[14597]: segfault at 70 ip 000000000041024e sp 00007fff2c8d9680 error 4 in compiz.real[400000+3b000]
Nov 12 17:43:58 Nicodemus bonobo-activation-server (bernard-14856): could not associate with desktop session: Failed to connect to socket /tmp/dbus-YlR4Pdul26: Connection refused
Nov 12 17:43:58 Nicodemus console-kit-daemon[5553]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)' 
Nov 12 17:43:58 Nicodemus console-kit-daemon[5553]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Nov 12 17:43:58 Nicodemus console-kit-daemon[5553]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Nov 12 17:43:59 Nicodemus acpid: client connected from 14888[0:0] 
Nov 12 17:44:01 Nicodemus kernel: [ 4118.865770] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:44:01 Nicodemus kernel: [ 4118.874308] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:44:01 Nicodemus kernel: [ 4118.874330] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:44:25 Nicodemus pulseaudio[15006]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:44:25 Nicodemus pulseaudio[15008]: pid.c: Stale PID file, overwriting.
Nov 12 17:44:25 Nicodemus pulseaudio[15008]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:44:25 Nicodemus pulseaudio[15008]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:44:25 Nicodemus pulseaudio[15008]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:44:25 Nicodemus pulseaudio[15008]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:44:26 Nicodemus x-session-manager[14946]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:44:36 Nicodemus x-session-manager[14946]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:44:37 Nicodemus pulseaudio[15008]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:44:37 Nicodemus pulseaudio[15008]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:44:38 Nicodemus python: hp-systray(init)[15144]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:44:38 Nicodemus anacron[15230]: Anacron 2.3 started on 2008-11-12
Nov 12 17:44:38 Nicodemus anacron[15230]: Normal exit (0 jobs run)
Nov 12 17:44:38 Nicodemus kernel: [ 4156.171978] CPU0 attaching NULL sched-domain.
Nov 12 17:44:38 Nicodemus kernel: [ 4156.172050] CPU1 attaching NULL sched-domain.
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216135] CPU0 attaching sched-domain:
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216145]  domain 0: span 0-1 level CPU
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216149]   groups: 0 1
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216154]   domain 1: span 0-1 level NODE
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216156]    groups: 0-1
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216162] CPU1 attaching sched-domain:
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216164]  domain 0: span 0-1 level CPU
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216166]   groups: 1 0
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216170]   domain 1: span 0-1 level NODE
Nov 12 17:44:38 Nicodemus kernel: [ 4156.216172]    groups: 0-1
Nov 12 17:45:19 Nicodemus kernel: [ 4196.690351] compiz.real[15120] trap stack segment ip:41024e sp:7fff06bad960 error:0
Nov 12 17:45:19 Nicodemus gdm[14870]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:45:21 Nicodemus acpid: client connected from 15351[0:0] 
Nov 12 17:45:22 Nicodemus kernel: [ 4200.367083] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:45:22 Nicodemus kernel: [ 4200.374942] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:45:22 Nicodemus kernel: [ 4200.374961] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:45:29 Nicodemus pulseaudio[15458]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:45:29 Nicodemus pulseaudio[15460]: pid.c: Stale PID file, overwriting.
Nov 12 17:45:29 Nicodemus pulseaudio[15460]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:45:29 Nicodemus pulseaudio[15460]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:45:29 Nicodemus pulseaudio[15460]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:45:29 Nicodemus pulseaudio[15460]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:45:30 Nicodemus x-session-manager[15397]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:45:40 Nicodemus x-session-manager[15397]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:45:40 Nicodemus pulseaudio[15460]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:45:40 Nicodemus pulseaudio[15460]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:45:41 Nicodemus python: hp-systray(init)[15600]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:45:42 Nicodemus anacron[15688]: Anacron 2.3 started on 2008-11-12
Nov 12 17:45:42 Nicodemus anacron[15688]: Normal exit (0 jobs run)
Nov 12 17:45:42 Nicodemus kernel: [ 4219.957563] CPU0 attaching NULL sched-domain.
Nov 12 17:45:42 Nicodemus kernel: [ 4219.957589] CPU1 attaching NULL sched-domain.
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988127] CPU0 attaching sched-domain:
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988138]  domain 0: span 0-1 level CPU
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988141]   groups: 0 1
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988146]   domain 1: span 0-1 level NODE
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988149]    groups: 0-1
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988155] CPU1 attaching sched-domain:
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988157]  domain 0: span 0-1 level CPU
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988159]   groups: 1 0
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988162]   domain 1: span 0-1 level NODE
Nov 12 17:45:42 Nicodemus kernel: [ 4219.988164]    groups: 0-1
Nov 12 17:46:22 Nicodemus gdm[15336]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:46:22 Nicodemus kernel: [ 4259.503489] compiz.real[15576] trap stack segment ip:41024e sp:7fffacb74920 error:0
Nov 12 17:46:22 Nicodemus bonobo-activation-server (bernard-15785): could not associate with desktop session: Failed to connect to socket /tmp/dbus-eOzrJVHuHp: Connection refused
Nov 12 17:46:24 Nicodemus acpid: client connected from 15815[0:0] 
Nov 12 17:46:25 Nicodemus kernel: [ 4263.152745] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:46:25 Nicodemus kernel: [ 4263.160849] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:46:25 Nicodemus kernel: [ 4263.160867] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:46:37 Nicodemus pulseaudio[15926]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:46:37 Nicodemus pulseaudio[15928]: pid.c: Stale PID file, overwriting.
Nov 12 17:46:37 Nicodemus pulseaudio[15928]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:46:37 Nicodemus pulseaudio[15928]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:46:37 Nicodemus pulseaudio[15928]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:46:37 Nicodemus pulseaudio[15928]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:46:38 Nicodemus x-session-manager[15865]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:46:49 Nicodemus x-session-manager[15865]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:46:49 Nicodemus pulseaudio[15928]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:46:49 Nicodemus pulseaudio[15928]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:46:50 Nicodemus python: hp-systray(init)[16067]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:46:51 Nicodemus anacron[16162]: Anacron 2.3 started on 2008-11-12
Nov 12 17:46:51 Nicodemus anacron[16162]: Normal exit (0 jobs run)
Nov 12 17:46:51 Nicodemus kernel: [ 4288.468581] CPU0 attaching NULL sched-domain.
Nov 12 17:46:51 Nicodemus kernel: [ 4288.468608] CPU1 attaching NULL sched-domain.
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485175] CPU0 attaching sched-domain:
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485189]  domain 0: span 0-1 level CPU
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485193]   groups: 0 1
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485198]   domain 1: span 0-1 level NODE
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485200]    groups: 0-1
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485214] CPU1 attaching sched-domain:
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485216]  domain 0: span 0-1 level CPU
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485219]   groups: 1 0
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485222]   domain 1: span 0-1 level NODE
Nov 12 17:46:51 Nicodemus kernel: [ 4288.485224]    groups: 0-1
Nov 12 17:47:48 Nicodemus kernel: [ 4346.149453] compiz.real[16044] trap stack segment ip:41024e sp:7fff39add890 error:0
Nov 12 17:47:48 Nicodemus gdm[15802]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:47:49 Nicodemus bonobo-activation-server (bernard-16264): could not associate with desktop session: Failed to connect to socket /tmp/dbus-JIaUj8lMl6: Connection refused
Nov 12 17:47:50 Nicodemus acpid: client connected from 16294[0:0] 
Nov 12 17:47:52 Nicodemus kernel: [ 4349.962271] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:47:52 Nicodemus kernel: [ 4349.971717] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:47:52 Nicodemus kernel: [ 4349.971738] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:48:00 Nicodemus pulseaudio[16408]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:48:00 Nicodemus pulseaudio[16410]: pid.c: Stale PID file, overwriting.
Nov 12 17:48:00 Nicodemus pulseaudio[16410]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:48:00 Nicodemus pulseaudio[16410]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:48:00 Nicodemus pulseaudio[16410]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:48:00 Nicodemus pulseaudio[16410]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:48:01 Nicodemus x-session-manager[16347]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:48:11 Nicodemus x-session-manager[16347]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:48:12 Nicodemus pulseaudio[16410]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:48:12 Nicodemus pulseaudio[16410]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:48:13 Nicodemus python: hp-systray(init)[16547]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:48:13 Nicodemus anacron[16625]: Anacron 2.3 started on 2008-11-12
Nov 12 17:48:13 Nicodemus anacron[16625]: Normal exit (0 jobs run)
Nov 12 17:48:13 Nicodemus kernel: [ 4371.008424] CPU0 attaching NULL sched-domain.
Nov 12 17:48:13 Nicodemus kernel: [ 4371.008450] CPU1 attaching NULL sched-domain.
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036144] CPU0 attaching sched-domain:
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036155]  domain 0: span 0-1 level CPU
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036159]   groups: 0 1
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036163]   domain 1: span 0-1 level NODE
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036166]    groups: 0-1
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036172] CPU1 attaching sched-domain:
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036174]  domain 0: span 0-1 level CPU
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036176]   groups: 1 0
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036179]   domain 1: span 0-1 level NODE
Nov 12 17:48:13 Nicodemus kernel: [ 4371.036181]    groups: 0-1
Nov 12 17:50:01 Nicodemus /USR/SBIN/CRON[16832]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov 12 17:50:28 Nicodemus kernel: [ 4506.023972] npviewer.bin[16916]: segfault at ff9d1e4c ip 00000000ff9d1e4c sp 00000000ff9f7dbc error 14
Nov 12 17:51:36 Nicodemus gdm[16280]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 12 17:51:37 Nicodemus kernel: [ 4574.352325] compiz.real[16526]: segfault at 92895 ip 000000000041024e sp 00007fffcfe50c00 error 4 in compiz.real[400000+3b000]
Nov 12 17:51:37 Nicodemus bonobo-activation-server (bernard-17034): could not associate with desktop session: Failed to connect to socket /tmp/dbus-YzRbemlxtp: Connection refused
Nov 12 17:51:39 Nicodemus acpid: client connected from 17066[0:0] 
Nov 12 17:51:40 Nicodemus kernel: [ 4578.160611] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 12 17:51:40 Nicodemus kernel: [ 4578.170374] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 12 17:51:40 Nicodemus kernel: [ 4578.170395] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 12 17:51:57 Nicodemus pulseaudio[17181]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 12 17:51:57 Nicodemus pulseaudio[17183]: pid.c: Stale PID file, overwriting.
Nov 12 17:51:57 Nicodemus pulseaudio[17183]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 12 17:51:57 Nicodemus pulseaudio[17183]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 12 17:51:57 Nicodemus pulseaudio[17183]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Nov 12 17:51:57 Nicodemus pulseaudio[17183]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 12 17:51:58 Nicodemus x-session-manager[17120]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 12 17:52:08 Nicodemus x-session-manager[17120]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 12 17:52:08 Nicodemus pulseaudio[17183]: module-x11-xsmp.c: X11 session manager not running.
Nov 12 17:52:08 Nicodemus pulseaudio[17183]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 12 17:52:09 Nicodemus python: hp-systray(init)[17319]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 12 17:52:10 Nicodemus anacron[17413]: Anacron 2.3 started on 2008-11-12
Nov 12 17:52:10 Nicodemus anacron[17413]: Normal exit (0 jobs run)
Nov 12 17:52:10 Nicodemus kernel: [ 4607.664177] CPU0 attaching NULL sched-domain.
Nov 12 17:52:10 Nicodemus kernel: [ 4607.664207] CPU1 attaching NULL sched-domain.
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681164] CPU0 attaching sched-domain:
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681179]  domain 0: span 0-1 level CPU
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681182]   groups: 0 1
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681187]   domain 1: span 0-1 level NODE
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681190]    groups: 0-1
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681195] CPU1 attaching sched-domain:
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681197]  domain 0: span 0-1 level CPU
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681200]   groups: 1 0
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681203]   domain 1: span 0-1 level NODE
Nov 12 17:52:10 Nicodemus kernel: [ 4607.681205]    groups: 0-1
Nov 12 17:56:43 Nicodemus kernel: [ 4880.664343] npviewer.bin[17718]: segfault at 13 ip 00000000f6fdddb7 sp 00000000ffab1824 error 4 in libflashplayer.so[f6939000+951000]
Nov 12 18:00:01 Nicodemus /USR/SBIN/CRON[17920]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov 12 18:10:01 Nicodemus /USR/SBIN/CRON[18689]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

There was nothing in message.

---

### Post by ecowan on 2008-11-28
I found, through KWifiManager, that my connection speed was somehow defaulted to 1Mbs, only a fraction of the 54Mbs my wifi network was capable of. Putting
[INDENT]iface wlan0 inet static
      ...
      ...
      wpa-conf /etc/wpa_supplicant.conf
      pre-up iwconfig wlan0 rate 54M

allow-hotplug wlan0
[/INDENT]
in /etc/network/interfaces did the trick.

- Erny

---

