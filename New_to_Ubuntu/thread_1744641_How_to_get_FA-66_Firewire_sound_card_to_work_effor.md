---
title: "How to get FA-66 Firewire sound card to work effortlessly"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by egervari on 2011-04-30
I really struggled to get my FA-66 working yesterday. I eventually did, but then I rebooted and now I can't make it work anymore. I must have just accidently stumbled on the solution or something... because trying the same things is no longer working.

How can I set this up so that when I reboot, it just works? I just want it to work like Windows.

I don't need it to do any music production - just firefox/movies. If I need to do music stuff, I'll just go back into Windows. I use Linux for programming in Ruby, and I'd like to have sound to listen to audiobooks or music while I work. That's it.

I got jackd, pulseaudio, linux-low-latency, etc. installed. I followed all the documentation. But now, pulse audio just won't load, and qjackctl is no longer working. 

I can't say I fully understood it before, but I'm definitely at a loss now. Please help?

```

$ /usr/bin/jackd -dfirewire -r48000 -p1024 -n3

jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
libffado 2.999.0- built Mar 28 2011 17:49:18
firewire ERR: FFADO: Error creating virtual device
Cannot attach audio driver
JackServer::Open() failed with -1
no message buffer overruns
Failed to start server


```If I open up the ffado mixer, I get this error:

```

[COLOR=#ff0000]12:15:36 logginghandler: Could not communicate with the FFADO DBus service...[/COLOR]

```This is not what I got yesterday :(

So, let's try and start the dbus server:

```

$ ffado-dbus-server
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

 Discovering devices...
02343623030: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
02343623057: Error (ffado-dbus-server.cpp)[ 277] main: Could not initialize device manager
no message buffer overruns

```

Well, that's odd... there is supposed to be ports.

---

