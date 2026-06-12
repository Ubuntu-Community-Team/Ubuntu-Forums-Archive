---
title: "JACK server questions from Ubuntu novice"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by dwankan on 2010-01-18
Can someone offer some suggestions for getting the JACK server to work.  I am completely new to this stuff, so type slowly.  When I try to open it, I get a could not connect to jack server error, with the info below in the message box.  
I've tried several different settings to try to configure it the right way, but nothing seems to work. I've looked and found a number of questions and responses to this type of problem, but they are all worded in terms beyond my understanding of the system, which makes it difficult for me to follow them.  
I thought maybe I could find a simple how to for setting up the server and configuring everything.  I just installed the Ubuntu Studio system, and I can't wait to start using it, but there seem to be a whole lot of things I need to configure before everything works, and I haven't been able to find a good step by step guide for a novice like myself.  Any suggestions?  Can anyone see a simple setting problem in the info below?  Thanks.


p, li { white-space: pre-wrap; }  p, li { white-space: pre-wrap; }  [COLOR=#999999]11:52:41.919 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:52:41.944 Statistics reset.[/COLOR]
 [COLOR=#999999]11:52:41.992 Startup script...[/COLOR]
 [COLOR=#990099]11:52:41.992 artsshell -q terminate[/COLOR]
 [COLOR=#66cc99]11:52:41.997 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]11:52:42.432 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]11:52:42.432 JACK is starting...[/COLOR]
 [COLOR=#990099]11:52:42.433 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 [COLOR=#999999]11:52:42.451 JACK was started with PID=4662.[/COLOR]
 cannot lock down memory for jackd (Cannot allocate memory)
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
 cannot load driver module alsa
 [COLOR=#999999]11:52:42.496 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]11:52:42.497 Post-shutdown script...[/COLOR]
 [COLOR=#990099]11:52:42.497 killall jackd[/COLOR]
 [COLOR=#cccc99]11:52:42.635 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]11:52:42.906 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]11:52:44.644 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by patchwork on 2010-01-18
Try suspending pulseaudio (hw:0 is in use, where jack can't access it).  Type: pasuspender qjackctl in the terminal.  This should suspend pulseaudio, start jack, and resume pulseaudio when jack is closed.

---

### Post by lidex on 2010-01-18
You may have to figure some work-arounds for pulse-audio since that is the default sound server for ubuntu.
Have a look at these links and come back with more specific questions if necessary: 
[http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904]("http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904")
[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")
[https://help.ubuntu.com/community/HowToJACKConfiguration]("https://help.ubuntu.com/community/HowToJACKConfiguration")
[https://help.ubuntu.com/community/HowToQjackCtlConnections]("https://help.ubuntu.com/community/HowToQjackCtlConnections")
[http://ubuntuforums.org/showthread.php?t=774581]("http://ubuntuforums.org/showthread.php?t=774581")
[http://ubuntuforums.org/showthread.php?t=444824]("http://ubuntuforums.org/showthread.php?t=444824")

---

### Post by dwankan on 2010-01-18
I may be in over my head with this.  I went through the documents you posted, and now although it seems that jack is running, I have no sound at all.  I guess pulse audio was my sound server, and since I've disabled it, I can't get any audio to work.  
Jack keeps giving me xrun errors and it keeps telling me "cannot lock down memory." 
I'm not sure about the memory lockdown thing.  I followed the instructions on the UbuntuStudio Preparation page when I first installed it, so I think all of the settings for rtkernel and memory lock should be right.  

 p, li { white-space: pre-wrap; }  ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback
 JACK: unable to mlock() port buffers: Cannot allocate memory
 JACK: unable to mlock() port buffers: Cannot allocate memory
 [COLOR=#CCCC99]17:30:32.444 ALSA connection change.[/COLOR]
 [COLOR=#999933]17:30:34.459 Server configuration saved to "/home/ /.jackdrc".[/COLOR]
 [COLOR=#999999]17:30:34.462 Statistics reset.[/COLOR]
 [COLOR=#999999]17:30:34.471 Client activated.[/COLOR]
 [COLOR=#9999CC]17:30:34.477 JACK connection change.[/COLOR]
 [COLOR=#CC9966]17:30:34.489 JACK connection graph change.[/COLOR]
 cannot lock down memory for RT thread (Cannot allocate memory)
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 0.670 msecs[/COLOR]
 [COLOR=#CC66CC]17:30:39.478 XRUN callback (1).[/COLOR]
  p, li { white-space: pre-wrap; }   **** alsa_pcm: [COLOR=#CC0000]xrun of at least 0.687 msecs[/COLOR]
 [COLOR=#CC66CC]17:30:56.054 XRUN callback (2).[/COLOR]
 subgraph starting at qjackctl timed out (subgraph_wait_fd=9, status = 0, state = Triggered, pollret = 0 revents = 0x0)
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 0.102 msecs[/COLOR]
 [COLOR=#CC66CC]17:31:29.091 XRUN callback (3).[/COLOR]
 [COLOR=#CC66CC]subgraph starting at qjackctl timed out (subgraph_wait_fd=9, status = 0, state = Triggered, pollret = 0 revents = 0x0)[/COLOR]
 [COLOR=#CC66CC]subgraph starting at qjackctl timed out (subgraph_wait_fd=9, status = 0, state = Triggered, pollret = 0 revents = 0x0)[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 1.783 msecs[/COLOR]
 [COLOR=#CC66CC]17:31:45.407 XRUN callback (4).[/COLOR]

---

### Post by lidex on 2010-01-18
**Jack can't allocate memory**

[http://ubuntuforums.org/showthread.php?t=955600]("http://ubuntuforums.org/showthread.php?t=955600")


*[COLOR="SlateGray"]Edit: here as well:[/COLOR]*
[http://www.******************/ubuntu-studio-user/136310-cannot-lock-down-memory-rt-thread-cannot-allocate-memory.html]("http://www.******************/ubuntu-studio-user/136310-cannot-lock-down-memory-rt-thread-cannot-allocate-memory.html")

---

### Post by dwankan on 2010-01-18
Yeah, I tried that.  How do I get to   "/etc/security/limits.conf" to change it?

---

### Post by patchwork on 2010-01-18
gksu gedit /etc/security/limits.conf           This will give you super user access to this file (for good or bad).

---

### Post by dwankan on 2010-01-18
Okay, tried that, and now, once again, jack will not load.  


p, li { white-space: pre-wrap;*  [COLOR=Black][COLOR=#FF0000]cannot use real-time scheduling (FIFO at priority 10) [for thread -1217435968, from thread -1217435968] (1: Operation not permitted)[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#FF0000]cannot create engine[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#999999]20:27:28.592 JACK was stopped successfully.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#999999]20:27:28.593 Post-shutdown script...[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#990099]20:27:28.593 killall jackd[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#FF0000]jackd: no process found[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#999999]20:27:29.000 Post-shutdown script terminated with exit status=256.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#FF0000]20:27:30.687 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR][/COLOR]

---

### Post by patchwork on 2010-01-18
Okay,just so we're on the same page....what exactly have you done when trying to get this setup?  Have you added your user to the audio group?  Are you starting jackd through the terminal, or are you relying on qjackctl to start it?

---

### Post by lidex on 2010-01-18
Believe it or not, that is progress:
[http://ubuntuforums.org/showthread.php?t=453486]("http://ubuntuforums.org/showthread.php?t=453486")
[http://ubuntuforums.org/showthread.php?t=600626]("http://ubuntuforums.org/showthread.php?t=600626")
[http://ubuntuforums.org/showthread.php?t=1143784]("http://ubuntuforums.org/showthread.php?t=1143784")
[http://ubuntuforums.org/showthread.php?t=1344669]("http://ubuntuforums.org/showthread.php?t=1344669")

---

### Post by chavafloresv on 2010-01-20
OK guys, I have a very similar problem as dwankan. I did almost every thing in the ubuntu studio preparation page and what i've read in other discussions, 

It must be something about the memory allocation of course, because I do can go real-time (without memory locked down), but the problem comes when I check the "Lock Down Memory" box  (I use the jack control) then when starting jack i got those messages.
I'm already an @audio user, I've added the rtprio 99, added the nice 10 line, added the memlock unlimited, and the problem didn't change.
Then i tried changing the values of those parameters:

@audio memlock 250000
@audio nice 19
@audio rtprio 95

I saw those values on a web about audio and linux, i'm sorry but i don't have the link right here with me, I owe it to you.
memlock is half of my RAM (in KB), and the other values are kind of random.

When I tried them it was different, jackd went zombie. But that's useless too.

The next thing i'm gonna try is changing the text in the limits.conf that says '@audio' for my user. (although i'm in the audio group, i just don't trust that is working very well)

If that doesn't work neither, i will probably just tweak a bit more the values of rtprio, nice, memlock.

Hope you have some help, or had the same problem. I don't think i'm missing something basic.
thanks!

---

