---
title: "Sound"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Fhallax on 2009-07-11
Hi again UF. It's me, again. This time it's sound. The login sound is fine and crystal clear upon startup, but after an hour or so, audio playback doesn't work anymore. I can hear everything, but it's all slow and bitty. Help!

---

### Post by earthpigg on 2009-07-11
**_while_** your sound is acting up and being choppy, please run the following command and show us the output:
> 
free -m

again, i want to emphasise that we need to troubleshoot this **_while_** your sound is being choppy.

run this and look at %CPU and see if something silly is taking up your processor power:

> top

---

### Post by Fhallax on 2009-07-11
jack@Fhallax:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          1002        983         19          0          9        165
-/+ buffers/cache:        808        194
Swap:         2933        134       2799
jack@Fhallax:~$ 






cpu usage is low 20-30%

---

### Post by earthpigg on 2009-07-11
bingo :P

you are out of RAM, and thus relying on swap space... swap space is needed for when you run out of ram, but since it is on your hard drive it goes much sloooowwweeeer. slow enough to make music sound chopped up.


to much stuff running at once for the amount of ram you have.

type 'top' at a terminal, make the terminal window long so you can see everything it has to show you.

look at the "%MEM" column.

what is using up all your memmory?

---

### Post by Fhallax on 2009-07-12
Nothing seems to be srsly eating up my RAM. I may have diagnosed the actual problem, if not the solution. It's whenever I view a video file, anything, from Megavideo OL, to a visualization in Rythmnbox on my HDD. It seems to permanently **** my sound even after the video has closed. 

Still confused,
Fhallax

---

