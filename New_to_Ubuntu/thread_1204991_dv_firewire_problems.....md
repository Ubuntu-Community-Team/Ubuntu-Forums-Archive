---
title: "dv firewire problems...."
date: 2009-07-05
forum: New to Ubuntu
---

### Post by Bansai1979 on 2009-07-05
Hello, 

Could someone help me out with my firewire / dv ?

I&#472;e been reading a lot, installed some modules etc. but no succes yet....

I got rid of the error msgs in kino, but the av/c device in 1394 preferences is blank.
So I tried to use kdenlive for my capturing, but it doesnt want to connect to my device neither.
So something in me says it had to do something with my firewire, although i don't get error on dev1394 and raw1394 anymore.
when I do lspci I see my card aswell.

Does anybody know how i can check my firewire? Or can anybody help me out with this problem?
thanks already!

p.s. I'm running ubuntu 9.04

Greetings,

Marco

---

### Post by cariboo on 2009-07-05
The only problem I have run into, is that you have to run applications that use firewire as root. Press ALt-F2 and type:

```
gksu kino
```

to run kino

I found this [page]("https://help.ubuntu.com/community/Firewire") to be helpful.

---

### Post by kellemes on 2009-07-05
You should be part of the video-group, no need for being root.

Connect your device, set it in the correct mode (if needed) and run from terminal..
```
dvgrab -i
```
If you're camera is not detected it'll tell you.. (and you'll need to visit the link as given my cariboo907)
If you're camera is detected you'll come in the dvgrab-commandmode from where you can grab your dv-recordings. Type ? for help.

Kino and KDEnlive never grabbed my dv-video, eventhough they make use of dvgrab (as far as I know), grabbing from commandline always worked for me..

My magical dvgrab-command is..
```
dvgrab -i --autosplit --format dv2 --timestamp myvideo
```

[man dvgrab]("http://linux.die.net/man/1/dvgrab")

---

### Post by Bansai1979 on 2009-07-05
I tried those things already.... dvgrab doesn't reconize/see my camera.....
I know the firewire page, tried those things already, it helped me to get rid of my error msgs....
but now in kino av/c field is blank and in kdenlive it can't connect neither......
I tried as root and I&#472;e edited the prev. of /dev/raw1394 and changed root allowences to my username.
So I as a newbee to Linux think the problem must be somewhere in the firewire

does anyone know how to check if the modules raw1394 and dev1394 are working? or is there a way to test if the firewire card is working correctly?


many thanks already!

---

### Post by geoffree on 2009-10-23
> **Bansai1979 said:**
> I tried those things already.... dvgrab doesn't reconize/see my camera.....
I know the firewire page, tried those things already, it helped me to get rid of my error msgs....
but now in kino av/c field is blank and in kdenlive it can't connect neither......
I tried as root and I&#472;e edited the prev. of /dev/raw1394 and changed root allowences to my username.
So I as a newbee to Linux think the problem must be somewhere in the firewire

does anyone know how to check if the modules raw1394 and dev1394 are working? or is there a way to test if the firewire card is working correctly?


many thanks already!



This is a reply to the July post as above:  I have a similar problem about recognition. The Panasonic camcorder isn't listed in the AV/C field. The Sony t-150 does appear in that field.  Neither survives a request to capture or replay what I got using dvgrab; they crash without a peep.  Did you get anywhere with your situation?

Geoffrey  "geoffree"
[email]zeno@empire.net[/email]

---

