---
title: "accessing my computer from somewhere else"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Zaff on 2008-07-28
So being what I would wall, a growing geek, and having found out that my ISP provides me with a static IP address (yeah !) I have redirected SSH ports to my desktop and can now acces it through SSH.
Now to the next step...

Let's sayI want to watch a video on that desktop or read a comic archive (CBR using Comix) or or listen to music that's on my desktop just do some stuff that need graphical interface or sound or both.
I don't necessarly want to have the whole desktop displayed on the machine I'm accessing from (although I'm guessing it's probably what's gonna happen).

Another thing I'd like to be able to do. Say my girlfriend is at home and wants to watch a video I have on my computer. She doesn't really know how to do it or where the file is and so I'd like tot be able to start the file from where I am. VLC and Mplayer will play the sound but the image won't show (I'm guessing because the display isn't set but I don't know how to tell it to display it at home).

Anyway what are my options ? Accessing my computer through SSH is cool but kinda limited since I only have the command line. 

Can anyone point me towards a tutorial or How TO ?
Thanks.

---

### Post by ilrudie on 2008-07-28
Check out No Machine NX

---

### Post by issih on 2008-07-28
Hmmn lots of options here....

Option 1. 
ssh -X (assuming the remote comuter has an X server) adding the -X option tries to use X11 forwarding, so the graphical component of any applications you start in the ssh session are forwarded to your remote machine. This would work for something like a comic, but for music, the sound would still come out of your server's speakers, as the code is still running there...

Option 2.
(again assuming the remote comp is linux) Use the connect to server option in places, and connect via ssh. This mounts the server's file system on your desktop, and you can then just start those files with local clients and stream them over the network (provided there is enough bandwidth :)).

Option 3
use something like vncserver along with ssh tunnelling to get the full desktop at a remote location

As for starting files on the server from a remote location.

stick a Display=:0.0 before the command you run:

e.g.```
 Display=:0.0 vlc filename
```

I think thats the correct syntax

Hope that helps

---

### Post by Zaff on 2008-07-30
> **issih said:**
> Hmmn lots of options here....

Option 1. 
ssh -X (assuming the remote comuter has an X server) adding the -X option tries to use X11 forwarding, so the graphical component of any applications you start in the ssh session are forwarded to your remote machine. This would work for something like a comic, but for music, the sound would still come out of your server's speakers, as the code is still running there...

Anyway to get the sound to here as well ?

> 
Option 2.
(again assuming the remote comp is linux) Use the connect to server option in places, and connect via ssh. This mounts the server's file system on your desktop, and you can then just start those files with local clients and stream them over the network (provided there is enough bandwidth :)).

Okay, that woooorks. Pretty cool. Kinda slow but it may just be what I need anyway. I didn't know Nautilus could do that ...
> 
Option 3
use something like vncserver along with ssh tunnelling to get the full desktop at a remote location

As for starting files on the server from a remote location.

stick a Display=:0.0 before the command you run:

e.g.```
 Display=:0.0 vlc filename
```

I think thats the correct syntax

Hope that helps
Alright I'll try that later. Thanks a lot, I'll check out vncserver as well.
Thanks again.

Edit : Tried the Display command but vlc says : 
```

$ Display=:0.0 vlc Babylon\ 5/Season\ 3/babylon5.s03e01.dvdrip.xvid-sfm.avi 
VLC media player 0.8.6e Janus
Error: Unable to initialize gtk, is DISPLAY set properly?

```

How do I know which value should go in Display ?
Tom

---

### Post by issih on 2008-07-31
Ah, my mistake, it needs to be DISPLAY=:0.0 

The second umber is the screen so 0.0 is your normal display, 0.1 would be a secondary monitor, etc. You can specify the display as being at a host too, but thats not needed here.

I'm not aware of a way to stream the audio within the X11 forwarding method, it probably can be done somehow, but I'm unaware of how..If you have pulse audio set up at both ends you could try using the networking features of that, but I haven't had much jpy with that yet personally

hope that helps.

EDIT...
[http://www.psc.edu/general/software/packages/general_usage/display_environment.html](http://www.psc.edu/general/software/packages/general_usage/display_environment.html)

That page covers the x display bit pretty thouroughly

---

