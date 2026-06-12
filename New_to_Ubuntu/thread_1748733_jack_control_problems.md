---
title: "jack control problems"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by joshcanfield on 2011-05-03
ok, so i play bass guitar and would love to use my computer to record/play music on it. i heard about using rakarrack along with audacity and jack control i installed all and i ran in to trouble with the jack control when i tried to start up jack control it gave a message saying that it could not connect to jack server as client. i dont know  what this means. it gave an info window that said this...


p, li { white-space: pre-wrap; } [COLOR=#999999]20:56:45.412 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]20:56:45.494 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]20:56:45.517 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]20:56:45.826 ALSA connection change.[/COLOR]
 [COLOR=#999999]20:57:00.709 Startup script...[/COLOR]
 [COLOR=#990099]20:57:00.709 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]20:57:01.113 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]20:57:01.114 JACK is starting...[/COLOR]
 [COLOR=#990099]20:57:01.114 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]20:57:01.118 JACK was started with PID=7617.[/COLOR]
 Cannot create thread 1 Operation not permitted
 Cannot create thread 1 Operation not permitted
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
 Using ALSA driver HDA-Intel running on card 0 - HDA SIS966 at 0xfdff0000 irq 18
 the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]20:57:01.314 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]20:57:01.314 Post-shutdown script...[/COLOR]
 [COLOR=#990099]20:57:01.315 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]20:57:01.730 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]20:57:03.283 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#ff0000]20:58:41.482 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#ff0000]20:58:52.647 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#ff0000]20:59:11.341 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

 can any one help me

also i disabled the realtime option. i read a that on a different forum. but it still does the same thing

---

### Post by ehsaniszko on 2011-05-05
i have the same problem , if something new so , pleas help :P

---

### Post by crustydusty on 2011-06-27
Have you tried adding your self to the audio group?

Open up a terminal  by going to Applications>Accessories>terminal  and type the following code

```
sudo adduser <username> audio
```Be sure to replace <username> with your actual username. 

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")
I found this information in the above link from the community documentation.

---

### Post by crustydusty on 2011-06-29
Any luck guys? If this helped mark this thread as solved by going to "Thread Tools>Mark As Solved"

---

### Post by gbd on 2011-07-13
I've had very similar problems. After re-installing, purging configuration files, identifying and killing applications using the sound server, and trying every other method I could find, nothing worked. Qjackctl wouldn't start no matter what settings I used. Neither would Ardour. Same error messages, cannot connect to server, default server already active, cannot connect to server socket etc. Very frustrating, considering it had all been running perfectly a few days previously. Now, nothing.

Until I plugged my guitar in.

Seriously folks. I had unplugged the adapter (mono guitar jack to mini-stereo jack) to take to a gig, and hadn't plugged it back in to the back of the computer. A quick rummage in my adapter bag and hey presto! All in perfect working order.

What made the realization dawn? "Cannot connect to server socket err = No such file or directory."

This may not be your problem, but it may help somebody searching the forums late at night considering computercide.

---

