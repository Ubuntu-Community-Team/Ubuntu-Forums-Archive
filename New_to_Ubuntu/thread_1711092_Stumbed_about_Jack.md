---
title: "Stumbed about Jack"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by Kirbster Barbecue on 2011-03-20
p, li { white-space: pre-wrap; } [COLOR=#999999]I am extremely green at this Linux lingo,  I just redid a computer with Windows XP and I put Ubunto Studio 10.10 Maverick Meerkat on it.  I love to fiddle with synthetic music and I was set unto this by some geek squad friends of mine.  so far I can not get Jack up and running.
[/COLOR]
[COLOR=#999999]
[/COLOR]
[COLOR=#999999]19:18:12.257 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:18:12.390 Statistics reset.[/COLOR]
 [COLOR=#999999]19:18:12.769 Startup script...[/COLOR]
 [COLOR=#990099]19:18:12.788 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]19:18:12.920 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]19:18:13.875 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:18:13.878 JACK is starting...[/COLOR]
 [COLOR=#990099]19:18:13.881 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]19:18:13.902 JACK was started with PID=2939.[/COLOR]
 no message buffer overruns
 [COLOR=#cccc99]19:18:14.093 ALSA connection change.[/COLOR]
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 Cannot lock down memory area (Cannot allocate memory)
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Using ALSA driver ICH4 running on card 0 - Intel 82801DB-ICH4 with AD1981A at irq 17
 the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]19:18:14.670 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]19:18:14.673 Post-shutdown script...[/COLOR]
 [COLOR=#990099]19:18:14.714 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]19:18:15.176 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]19:18:16.208 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#ff0000]19:18:21.525 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#ff0000]19:18:30.513 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]

---

### Post by ventrical on 2011-03-20
try removing Ubuntu Studio using Synpatic Package Manager (or Ubuntu One) and then re-install it and see if that helps.

---

### Post by sandyd on 2011-03-20
> **Kirbster Barbecue said:**
> p, li { white-space: pre-wrap; } [COLOR=#999999]I am extremely green at this Linux lingo,  I just redid a computer with Windows XP and I put Ubunto Studio 10.10 Maverick Meerkat on it.  I love to fiddle with synthetic music and I was set unto this by some geek squad friends of mine.  so far I can not get Jack up and running.
[/COLOR]
[COLOR=#999999]
[/COLOR]
[COLOR=#999999]19:18:12.257 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:18:12.390 Statistics reset.[/COLOR]
 [COLOR=#999999]19:18:12.769 Startup script...[/COLOR]
 [COLOR=#990099]19:18:12.788 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]19:18:12.920 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]19:18:13.875 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:18:13.878 JACK is starting...[/COLOR]
 [COLOR=#990099]19:18:13.881 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]19:18:13.902 JACK was started with PID=2939.[/COLOR]
 no message buffer overruns
 [COLOR=#cccc99]19:18:14.093 ALSA connection change.[/COLOR]
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 Cannot lock down memory area (Cannot allocate memory)
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Using ALSA driver ICH4 running on card 0 - Intel 82801DB-ICH4 with AD1981A at irq 17
 **the playback device "hw:0" is already in use. Please stop the application using it and run JACK again**
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]19:18:14.670 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]19:18:14.673 Post-shutdown script...[/COLOR]
 [COLOR=#990099]19:18:14.714 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]19:18:15.176 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]19:18:16.208 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#ff0000]19:18:21.525 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#ff0000]19:18:30.513 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
hint bolded.
Only one program can use the sound output at a time. see which application is hogging it by running
```

lsof | grep /dev/shm

```

---

