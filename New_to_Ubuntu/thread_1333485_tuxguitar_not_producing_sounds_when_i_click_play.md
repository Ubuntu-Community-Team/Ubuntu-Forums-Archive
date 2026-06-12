---
title: "tuxguitar: not producing sounds when i click play"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by exilio3000 on 2009-11-21
Hi, I'm running jaunty with gnome and I've got all the media codecs for multimedia. I just installed tuxguitar and I can't get the program to play sound. I haven't created anything, but when I try to play the default "guitar tuner" notes, it cycles through the notes, but I get no sound. I have no other sound issues with other programs, by the way.

**To the poster below me (daz101) - I already have Timidity installed. 
One solution that worked for someone else, not me, was to pull up a terminal screen and enter:
```

aoss tuxguitar

```

This person was running ubuntu jaunty as well. aoss from the manpage:

aoss  -  Wrapper script to facilitate use of the ALSA OSS compatibility
       library.

Like I said, this solution failed to work for me, maybe I'm missing some step though.


The solution I found to fix the sound problem was by calling timidity on the command line, I'm pasting the solution that worked for me:

```
timidity -iA -Os
```

Next, start tuxguitar and work through the menus - tools -> settings -> sounds. select a timidity port - you might have to try several before you find one that works though. i have to use timidity port 0[129:0]. **Note, I used port 0[129:0] as well, and if you peruse the scrolling info after entering the timidity command above, you should see which ports it opens up that will be available to use by tuxguitar. you should see a line that reads:
```

Opening sequencer port: 129:0 129:1 129:2 129:3

```
or something similar (the port numbers could vary, the ones listed on your screen are the ones you want to enable).


you will have to put that command in a terminal each time you want to run tuxguitar, unless you add timidity to your start-up sessions.

just click system->preferences->sessions->add session and put that command in there.


There is a link at the bottom of the post is where i found these solutions, btw. 

The last solution mentioned is the following:


What solved it for me was installing package tuxguitar-jsa (available through Synaptic).

Then:
1. open Tuxguitar and go to Tools -> Plugins
2. disable "ALSA output plugin" and "OSS output plugin" (if you have them)
3. enable (if it isn't yet) "Java Sound Api plugin"
4. restart Tuxguitar

That did it for me, I hope this helps someone else out there.

Finally, here are links to the solutions posts i found:

[http://ubuntuforums.org/showthread.php?t=1001563&highlight=tuxguitar]("http://ubuntuforums.org/showthread.php?t=1001563&highlight=tuxguitar")

aoss solution page:
[http://ubuntuforums.org/showthread.php?t=1001563&highlight=tuxguitar]("http://ubuntuforums.org/showthread.php?t=1001563&highlight=tuxguitar")

---

### Post by daz101 on 2009-11-21
You'll need to install a midi player. I use timidity, available thru the repository. Then go to the tools tab and hit settings. Under "sound" you'll be able to select timidity port 0 #1. That should see ya right.
Regards 
D

---

### Post by Zoot7 on 2009-11-21
Another thing I find is handy to do is to suspend Pulseaudio when I start Tuxguitar.
```
pasuspender tuxguitar
```
That way Pulse is suspended when Tuxguitar is started so it has full access to the Alsa driver, and it's brought back to life once that app quits.
I'm currently using it for some Games, Wine installed stuff and Tuxguitar.

---

