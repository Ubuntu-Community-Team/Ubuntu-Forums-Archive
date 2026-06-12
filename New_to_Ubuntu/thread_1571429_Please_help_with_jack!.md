---
title: "Please help with jack!"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by onmyabs on 2010-09-09
Alright so last week I got ubuntu because i wanted to try out linux (I was told that it's better than linux). Everything I heard about it is true. I am also noticing that there is VERY MUCH more freeware for ubuntu than there is for windows. Of course, being human i decided to take advantage of this and find a freeware for guitar recording. I found this amazing software called "rakarrack" which claims to be everything I'm looking for. But there is one problem, when I try to run it, it says, "Cannot make a jack client, is jackd running?"
So, I reinstalled jack. I tried to test it and it said:

  "Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info."

PLEASE TELL ME WHAT TO DO!

Note: I am a big time N00b.

---

### Post by onmyabs on 2010-09-09
p, li { white-space: pre-wrap; }  [COLOR=#999999]15:56:58.779 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]15:56:58.919 Statistics reset.[/COLOR]
 [COLOR=#66CC99]15:56:58.943 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]15:56:59.283 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:57:06.457 Startup script...[/COLOR]
 [COLOR=#990099]15:57:06.457 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]15:57:06.859 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]15:57:06.859 JACK is starting...[/COLOR]
 [COLOR=#990099]15:57:06.860 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -D -C/dev/audio -Xseq[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 [COLOR=#999999]15:57:06.870 JACK was started with PID=4100.[/COLOR]
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]15:57:06.882 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]15:57:06.883 Post-shutdown script...[/COLOR]
 [COLOR=#990099]15:57:06.883 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]15:57:07.292 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]15:57:08.918 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by transmogrifox on 2010-09-09
This is a simple case of basic jack configuration.

It will be worth the trouble to get jack running properly as this will open the doors not only to Rakarrack, but realtime low-latency usage of many other programs like Hydrogen, Qtractor, Guitarix....just to name a few.  Search Ubuntu forums and you will find many posts about "favorite audio production programs" or something similar where people recommend good programs to try.

Coming from Windows, you're probably used to programs just hooking up to the audio system and working when you launch.  Unfortunately there are a number of things that have to happen for Rakarrack to be able to get audio in and send it back out, and this all depends upon JACK being running, or being possible to launch from default settings. 

Sadly, the defaults probably don't work with your sound card, so here is the drill:
Install qjackctl.  It is a nice little GUI utility to help you configure jack, get it running, and make connections.

Open qjackctl and go into the settings. From there, what you do will depend on your audio interface.  Here is some information to help:
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

Then this is the specific page for jack configuration help:
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

Then you probably want to give your user real time permissions so you can use Rakarrack at a low latency:
Using a text editor, modify /etc/security/limits/limits.d/audio.conf as root...to do it from a command line try this:
```
sudo gedit /etc/security/limits/limits.d/audio.conf
```
and it will open the file in a nice GUI program similar to Notepad under windows.
 
Make sure these lines are present in the file, and they are not commented.  A commented line starts with a hash "#", so delete the hash if these lines exist in the file, else add these lines:
```
@audio - rtprio 99 
@audio - memlock unlimited 
```

A commented line would look like this:
```
#@audio - rtprio 99
```
Then you would want to change it to this:
```
@audio - rtprio 99
```

The two lines above will let your user schedule priority for audio processing so you don't get xruns, which is a term for what happens when jack wants an output from a program, but the program isn't done processing...then it drops whatever frames aren't processed and you get bad glitchy sound.

Anyway, first thing is make it possible for JACK to run, then use qjackctl to start it.  At this point, Rakarrack should start without any problems.  The messages you posted above can be summarized with this:
Rakarrack starts, jack isn't running.
Rakarrack tries to launch jack.
Jack fails to launch because the default settings don't make sense with your hardware.
Without jack running, rakarrack says, "I give up, and quits".

After the first time you launch Rakarrack, you can go into the settings and preferences...under Jack tab, then select the input and output ports you want Rakarrack to connect to when the program launches.  After jack is configured, and Rakarrack is configured to connect to the correct ports by default, then you should be able to click on rakarrack and it will take care of all the details of starting jack and getting connected to the right place.

Once you get Rakarrack working, you may find it of interest to install it from AutoStatic's PPA, as he tracks with current development, which includes bug fixes and new features...I'll leave it to you to search and read about adding and using PPA's, and to search/find AutoStatic.

Here are some videos I have posted with Rakarrack.  Me mostly noodling around to show off a few sounds, but there you go:

[http://www.youtube.com/watch?v=VfWBhNrC2n4&feature=channel](http://www.youtube.com/watch?v=VfWBhNrC2n4&feature=channel)
[http://www.youtube.com/watch?v=tJHmUJVwOKo&feature=channel](http://www.youtube.com/watch?v=tJHmUJVwOKo&feature=channel)
[http://www.youtube.com/watch?v=OKjBJ2Oc5RM&feature=channel](http://www.youtube.com/watch?v=OKjBJ2Oc5RM&feature=channel)
[http://www.youtube.com/watch?v=MQlt9r1011A&feature=channel](http://www.youtube.com/watch?v=MQlt9r1011A&feature=channel)
[http://www.youtube.com/watch?v=cBUXJzsEpcM&feature=channel](http://www.youtube.com/watch?v=cBUXJzsEpcM&feature=channel)
[http://www.youtube.com/watch?v=TvVUYNn1DGI&feature=channel](http://www.youtube.com/watch?v=TvVUYNn1DGI&feature=channel)
[http://www.youtube.com/watch?v=geJQpabZGZQ](http://www.youtube.com/watch?v=geJQpabZGZQ)
Most of them come from current development version, so if you see something you can't do in the Ubuntu version, then try a PPA.

Warning... <RANT>
My own personal rant about the word "freeware"...please don't take offense if it rubs you the wrong way:
To me "freeware" means programs that one can download and install free of monetary cost, but often come with a "gotcha".  Freeware is usually what I equate to spyware or a conduit to sneak trojan horses onto your system.

"Free Software" is what you find on linux (ubuntu), where the motives for developing the software are completely different.  Usually it is a volunteer work, or produced by a non-profit organization or university.  It is free as in freedom.  No strings attached, no hidden gimmicks.  Just software that is common like rocks on the ground ;)

In general the term Free Software settles better with me, but then what more is Freeware, than a concatenation of the two....or is it Free'gotcha'ware, or Free'spy'ware?.  Usually "freeware" is only a Windows and Mac plague.  There is also much truly Free Software available for windows and mac, and you may be surprised at how many programs you will come to love on Ubuntu are also available for Win and Mac
</RANT>

---

