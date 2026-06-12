---
title: "resume from suspend"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by nwadams on 2009-07-17
hi

when I resume from suspend it often kicks me back out to the GDM login screen instead of the lock screen. So when i have to log back in i lose all my open windows.

I have a dell xps m1330, am using jaunty default with upgrades. Its only been happening for the past few weeks. I'm not sure whether i screwed up the configuration files or something. Can someone help me troubleshoot and possibly purge the config files back to a jaunty default.

Thanks for any help.

---

### Post by earthpigg on 2009-07-17
hi nwadams,

can you please show the output of this command in a terminal?

> free -m

wrap it on [ CODE ] and [ /CODE ] to make it easier to read, please. (take the spaces out of [C ODE] to make it work.)

the result should look something like this:

```
ep@ep-9:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3895       3715        180          0        197       2642
-/+ buffers/cache:        875       3020
Swap:         1592          0       1592
ep@ep-9:~$ 
```

---

### Post by nwadams on 2009-07-17
```

nwadams@nwadams-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2974       1394       1580          0        105        679
-/+ buffers/cache:        609       2365
Swap:         3914          0       3914

```

sorry, i realized it as soon as i posted that it needed to be fixed

---

### Post by earthpigg on 2009-07-17
yer columns are off by one cuz you added the code tag after the fact :P

this is how it looks in your terminal, with columns lined up properly:
```
------------->total       used       free     shared    buffers     cached
Mem:          2974       1664       1310          0         97        779
-/+ buffers/cache:        _787_       _2187_
Swap:         3914          0       3914
```

take a look at the relationship between 'free' and 'used' memmory in the +/- buffers/cache line.

you want free to be a bigger number than used if you are going to expect suspend to work reliably. i bet right now you could suspend just fine. 

with a bunch of memmory-intensive applications open, however, that relationship will soon change and that may no longer be the case. observe the relationship between 'free' and 'used' in the +/- cache line, and find a pattern between that and suspend failing on your machine.

_hibernate_, on the other hand, uses swap space. with 4 gigs of swap space free, you should be able to hibernate peachy keen... as long as mem and swap 'used' together do not add up to a greater number than 4 gigs.


its all about memory - stuff must get stored somewhere!

---

### Post by nwadams on 2009-07-17
hmm, thanks. and yes i tried suspend and it worked properly :P. 
so I see how its failing...possibly..because it still suspends normally, just crashes on resume...which makes sense that there's not enough ram. So i'm content with that. 

Can you recommend something that I can do that will help me improve the consistancy of my suspend/resume?

---

### Post by earthpigg on 2009-07-17
if you want to free up some memmory, you need to find out out what is using it all. some programs are horrible memmorry hogs that eat up more and more memmory the longer they are left running -- firefox is one of these. even if you restart it keeping the same tabs open, it will often use less memmory if you close it and open it right back up.

gnome-system-monitor is good to check that. right click on panel -> add to panel -> system monitor -> click to open it -> 'processes' tab -> sort by memmory. 

in my case, i have firefox, rhythmbox, compiz, and pidgin at the top of my list. right now, firefox is at 120mb. leaving ff running for days/weeks at a time without closing it and opening it back up, _i have seen it use 1,200mb_. that right there is enough to kill a sucessfull suspend.

not only will keeping memory hog applications in check make suspend more reliable, but it will make your system snappier as more space will be available for cache and buffers.

---

### Post by nwadams on 2009-07-17
yes, ff is a memory hog. Thanks a lot though. I will to check and see what is using most of my memory, then i can adjust accordingly and hopefully will be able to get better suspends. 

Its strange though because i've never had this problem before a couple weeks ago.

---

### Post by earthpigg on 2009-07-17
what other software do you commonly use that may be memory intensive? thats what you need to figure out.

3d rendering software? virtual machines? 5000 large pdf files open at once?

edit:

> Its strange though because i've never had this problem before a couple weeks ago.

a software update could have updated something you frequently use.... if you weren't taking notes on how much memory things where using prior to the update (and who does?), it'll be very difficult to track it down.

---

### Post by nwadams on 2009-07-17
lol, normally just firefox, pidgin, banshee, and a few OOo documents normally. I do use virtual machines but i do not suspend with them running normally.

EDIT: well thanks a lot for your help. I think this is solved now.

---

### Post by nwadams on 2009-07-18
this is going to sound strange, but i still wasn't getting any correlation between the ratio and successful suspends. So I disabled compiz and suspends are working properly now...100% of the time, even with huge ram usages and virtualizations running

---

