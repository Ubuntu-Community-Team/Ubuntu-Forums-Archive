---
title: "[HELP] jaunty randomly freezing..."
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Darkoblivion2 on 2009-07-15
specs:

intel core 2 quad 9550
geforce gtx 260
1tb western digital hdd
8gb of kingston ram
jaunty 9.04 64bit

so every once and awhile, my ubuntu will freeze, but, i will be able to move the mouse pointer on screen a lil bit every 5 secs or so after the initial "lock up"

and it isnt just one thing that causes this... i have had it happen to me multiple times in firefox, and wow. and sometimes while im just doing some file management...

anyone experiencing these symptoms as well?

most of what i have googled, and searched on these forums says that its just jaunty...
is this true?

or is my problem more specific?

any replies would be appreciated!

thanx in advance!

ps...

direct rendering: Yes

sata hdd: yes

and yes its a hard lockup, i cant use the keyboard, and requires me to push the restart button

---

### Post by daimaru on 2009-07-15
i had similar thing on 32bit version just reinstalled 64bit to see if its any better. 
it happend durring video playback for me , it froze comp could not exit fullscreen video and it started flimmering sometimes i could see desktop sometimes video.  but video wasnt playing anymore.

same thing happend durring file copy (large , or many files) all windows on desktop were greyed out and my mouse was moving for a very short time (1sec) every 10-15 seconds. couldnt shutdown (no ctrl+alt+backspace) or print+alt + reisub working either. hand to kill with reset switch. 

havent had this problem yet using 64bit version, but I just installed yesterday, so maybe i was just lucky till now.

---

### Post by Imperator1928 on 2009-07-15
I was just about to post a similar issue. I started experiencing weird freezes couple of days ago when I switched to Jaunty (32 bit). I also replaced my old hdd with a new one (sata II) and I suspected some glitch in the hardware. Then I ran some smartmon test and there is no indication of any hdd health problems so I started suspecting Jaunty.

 Freezes occur randomly. When they occur, everything on the display ceases to move and music stops playing. To unfreez the beast it's enough to move the mouse and everything seems well until the next freez. The funny thing is that when the freez occurs and the music stops playing, things seem to work in the background. I mean there is no outer indication of any sort of ongoing processes but when I unfreez the computer the music does not continue playing from the point it freezed but it seems to have been playing all the time it was freezed. In other words, music is playing but I can't here it neither I can see any progress on Rhythmbox. Well, everything looked cool till I realised my downloads time out after some longer freezes.

It drives me mad :O  Does anyone else experience this sort of ****? But what's more important, does anybody have any cluse how to fix it? :]

Regards

---

### Post by super kim on 2009-07-15
Oh i had that exact same problem. i found a tread with a custom kernel that fixes that problem, then i had a new problem that the kernel headers were missing. then a nice chap helped me find the missing headers, then i had the problem again.
While the headers were missing i couldn't use my Nvidia drivers and it didn't crash, so i selected an older driver (works just as well) and it has not crashed once since then! Thats about a month with no crashes.

This might me helpfull

my thread I'd read it all to save the same problems i had
[http://ubuntuforums.org/showthread.php?p=7472533#post7472533](http://ubuntuforums.org/showthread.php?p=7472533#post7472533)

the custom kernel that fixes the freezing bug
[http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29)

I hope this works for you too.

---

