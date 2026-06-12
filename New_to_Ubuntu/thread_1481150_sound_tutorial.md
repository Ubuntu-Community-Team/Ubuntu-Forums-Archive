---
title: "sound tutorial"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by senorian on 2010-05-12
9.10 to 10.04
I was using 9.10 but messed up(lost) the sound. This just happened so I decided to upgrade to 10.04 in the hope that it would fix my sound. 
NO go
Everything except sound seems to be OK
When using 9.10 I somehow managed to get xine working to receive an internet station(radio.zvezdelin.net) BUT could not then get rid of xine.
It still, on 10.04, continues (but nosound)
Thanks

---

### Post by themusicalduck on 2010-05-12
If the problem occurred because of changing something on 9.10 then that change will probably have been carried over to 10.04 if you did an upgrade. (If you did a fresh install then there must be another problem).

If you tell us what you did in the first place for you to lose sound, or link to a tutorial or something if you followed one then it might be fixable, otherwise a fresh install might be a good idea (but testing it on a liveCD first).

---

### Post by lidex on 2010-05-12
> **themusicalduck said:**
> If the problem occurred because of changing something on 9.10 then that change will probably have been carried over to 10.04 if you did an upgrade. (If you did a fresh install then there must be another problem).

If you tell us what you did in the first place for you to lose sound, or link to a tutorial or something if you followed one then it might be fixable, otherwise a fresh install might be a good idea (but testing it on a liveCD first).

I'm inclined to agree with that assessment. Do "Part A" here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Logout/in. 

Now post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by senorian on 2010-05-13
Thank you for your replies 
I apologize for not making myself clear
I said "upgrade" and, while I know the difference between "upgrade" and "fresh install", I do not know how many variations of "upgrade" there are.
The Ubuntu Update manager advised me that I could upgrade to 10.04, so I pushed the button.
With 9.10 I at first had Mplayer caching forever and in my attempts to listen to the online radio I got Xine working. The only problem was that the whole screen was filled by the word "xine"
With my previous OS I  got a small window giving me the name of the song and a few other details.
I tried to get rid of Xine using synaptic but failed.
I have no idea what I did to lose the sound.
Perhaps I should have titled my inquiry:
sound tutorial WANTED
Although the old adage about being careful about what you wish for --you might get more than you want! seems applicable here
There is no question that the command line is a very powerful tool. But not, perhaps, in the hands of an "absolute beginner"
I will keep your guidance on file and in the event that I am unable to find an OS that delivers sound "out of the box" I will attempt to follow your advice
Thank you

EDIT
call me an idiot. I just phoned my son and he told me he turned the amplifier way down the last time he visited.
I still want to get rid of xine
Very sorry to have wasted your time

---

