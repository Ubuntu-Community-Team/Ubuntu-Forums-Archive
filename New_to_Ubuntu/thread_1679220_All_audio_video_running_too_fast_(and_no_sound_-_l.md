---
title: "All audio/ video running too fast (and no sound - let me explain)"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by CaptainJamie on 2011-01-31
Hello there! Another mundane question:
When on YouTube watching a video or on VLC or movie player or rhythmbox there is no sound and the video plays at 2x or more speed. It was working before I restarted my computer so that must mean that one of the changes I made between then caused it, so:
I have messed about trying to install and remove desktop art plugin for rhythmbox, which, by the way, still isn't working so as an encore you could fix that for bonus points :)
I have also installed Compiz recently with the extras and something called subversion, which I apparently needed for the plugin...
If you need any more information then please ask and I shall set about finding it!
Thanks, Jamie

---

### Post by CaptainJamie on 2011-02-02
Bump - sorry still have the same problem and it's getting tedious. It's after a fresh install now, reinstalling worked but only until I updated. Can anyone narrow down what is causing the problem. Something to do with what plays media (and controls the speed it plays) that was updated since 10.10.

---

### Post by CaptainJamie on 2011-02-03
Well, I booted Ubuntu today and it's working fine. It's hardly a fix as I haven't fixed anything. Strange...

---

### Post by praneel raja on 2011-02-13
[I]Its a pulseaudio problem, I had the same issue. Try messing around with the sound options, in system->preferences->sound 
 
well this is what i did,   system->preferences->sound -> hardware                                                                           and disabled Manhattan HDMI audio 
and every thing fell into  place 
[/I]

---

### Post by intelectoall on 2011-04-03
It has worked perfectly for me!!! Thanks praneel.

---

### Post by stewieX on 2011-10-11
I've had this problem for over a month in 11.04. It came with no warning. Thanks, that solved my issue!


[SIZE="1"]Just some key words for people searching on Google (because I had trouble finding this page):
My audio does not work and is playing too fast.
No sound on my computer and running too quick.
Media playing too fast on my Ubuntu computer and no sound.[/SIZE]

---

### Post by whizsper on 2011-11-07
Good find.
Works aswell in 11.10.

---

### Post by sagar13 on 2012-06-02
same problem in 12.04. How to find pulseaudio settings or hardware settings??

---

### Post by Xplorer4x4 on 2012-06-15
Soprry to bump this but..I am using Kubuntu and just wanted to share a possible fix for Kubuntu KDE users. For me the problem came when playing with my device settings in Amarok. It affected nothing outside of Amarok though. The problem seemed to be that "Phonon" kept trying to redirect audio to the HDMI out on my video card. Even when I tried to change back to my on board "Built in Audio" device, it reverted back to my video card. I finally had to go in and select the video card as my out put device and then disable it. After this it reverted back to using my built in sound and everything works great now!

---

### Post by sahilgrover1988 on 2012-06-30
If you cannot find pulseaudio settings or hardware settings do following steps :

1. Open terminal (Alt + Ctrl +T).

2. Type pulseaudio -k


Now you are good to go cheers !!

---

### Post by Przedzmirski on 2012-09-04
sahilgrover1988 Thanks man!!!!! That's what i call a magic command, solved my problem in 2 ms. heheh :p

---

### Post by skewray on 2013-01-19
None of the above solutions worked for me.  Instead, I deleted all of the files in ~/.pulse.

---

### Post by receivet on 2013-05-02
Today i have install fresh version of linux mint. And everything went well but when I watch the you tube video or any other video site it went too fast also with no sound.


NOTE
 
(This is what worked for me, i hope this works for you too)


After a bit messing around I found the solution of this problem




Go to your system - Preference - Sound 
Watch this video for more info
[http://www.youtube.com/watch?v=wSBshbZxfdU](http://www.youtube.com/watch?v=wSBshbZxfdU)

---

### Post by oldos2er on 2013-05-02
Old thread closed.

---

