---
title: "start-up problems/firefox eats CPU"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-08-19
Well, I wouldn't consider this absolute beginner talk, but I need an answer in beginner talk. Or, really, just an answer, since no one is paying attention to me in general help, and this board has helped me successfully before. 

I have two problems. The first is that when trying to boot up, ubuntu either crashes or glitches or something. But it doesn't start. It just turns my monitor off, and NO this is NOT a hardware issue. I have seen other people having start-up difficulties today on this very forum, I found (old and unresolved) threads in which people were having similar issues, and nothing remotely like this ever happened before I got ubuntu. The old threads seemed to indicate it might have something to do with ubuntu changing or messing up the video signal at start-up, which makes sense because a couple of times instead of just turning off, the monitor has auto-adjusted or turned off and hung for a few moments, but then come back when ubuntu managed to right itself and boot. Now, this is a real problem because not only can I not shut down safely, I can't even use the power button on the tower to communicate to the machine. I have to turn it off at the power-bar, and I suspect that that is really not good for it.

The second problem is that firefox is devouring all my CPU (like, as high as 90%), and running like dial-up. It's especially bad when using youtube or other video players and the play is so choppy sometimes it's almost impossible to watch. Now this is something other people were getting help for, but the help was in essentially another language. I'm really ubuntu-stupid, and couldn't even figure out how to download and install things, and have actually just given up on ever getting a new program onto this computer. I can download music torrents. That's about all I can figure out. So I'll need any instructions in total toddler language. 

Thanks in advance, and I'm sorry in advance if I have difficulty with instructions.

---

### Post by magneze on 2009-08-19
If you're using Firefox 3.5 then make sure you're not using the Skype plugin. It screws things up big time on facebook, gmail and probably other sites too.

---

### Post by LewRockwell on 2009-08-19
> **rahrahmah said:**
> Well, I wouldn't consider this absolute beginner talk, but I need an answer in beginner talk. Or, really, just an answer, since no one is paying attention to me in general help, and this board has helped me successfully before.

 You might find a more receptive audience if you included more specific details regarding your equipment, operating system(s), and/or any peripherals that might or might not be related or at issue. Seemingly unimportant details to the uninitiated might well be very important to the audience you hope to gain the support of.

> **rahrahmah said:**
> I have two problems. The first is that when trying to boot up, ubuntu either crashes or glitches or something. But it doesn't start. It just turns my monitor off, and NO this is NOT a hardware issue. I have seen other people having start-up difficulties today on this very forum, I found (old and unresolved) threads in which people were having similar issues, and nothing remotely like this ever happened before I got ubuntu. The old threads seemed to indicate it might have something to do with ubuntu changing or messing up the video signal at start-up, which makes sense because a couple of times instead of just turning off, the monitor has auto-adjusted or turned off and hung for a few moments, but then come back when ubuntu managed to right itself and boot. Now, this is a real problem because not only can I not shut down safely, I can't even use the power button on the tower to communicate to the machine. I have to turn it off at the power-bar, and I suspect that that is really not good for it.

Are you referencing this behavior while attempting to operate your equipment via booting from the LiveCD

or

Is this behavior occurring after installation and before a post-installation boot-up...or after one or more successful boot-ups after initial successful hardware testing via the LiveCD

and/or

Is this behavior a likely result of a recent update and/or upgrade

> **rahrahmah said:**
> The second problem is that firefox is devouring all my CPU (like, as high as 90%), and running like dial-up. It's especially bad when using youtube or other video players and the play is so choppy sometimes it's almost impossible to watch. Now this is something other people were getting help for, but the help was in essentially another language. I'm really ubuntu-stupid, and couldn't even figure out how to download and install things, and have actually just given up on ever getting a new program onto this computer. I can download music torrents. That's about all I can figure out. So I'll need any instructions in total toddler language.

Browsers, including Firefox, consume a percentage of your CPU even while open but idle, when running even one browser window with significant content/audio/video/etc it is not unusual to see a high CPU usage

Without knowing your specific equipment and operating system(s) setup it will be difficult for anyone to offer any more insight as to the probable cause of your noted trouble-call

.

---

### Post by rahrahmah on 2009-08-19
"Seemingly unimportant details to the uninitiated might well be very important to the audience you hope to gain the support of."

Well, since I'm uninitiated, I'd consider them unimportant and not think to include them, wouldn't I? It's a pentium 4 2.93 Ghz. The name of the brand is emachines, I don't know if that's important. The monitor is a Dell. it's, like, three years old. It's the newest ubuntu. 

Since it's something that's happened more than once, but not every time, I would assume it was obvious it was just a normal start up (unless I should be booting from a CD every time? I really don't know, ubuntu is confusing). It COULD be the result of an update, but I wouldn't know which one, since I seem to get a little package of stuff to add every other day, and I don't know what any of it is.

And as for CPU, people who seem more computer accomplished than me seem to be complaining about this sort of thing on the boards and receiving help for it (just in language I don't speak), it appears to be a familiar bug, not just being told it's normal. I really don't think it is. It runs like garbage. When I was running windows my CPU usage never went even remotely this high while running just one program.

I hope I've included all the necessary information, and if I haven't, I'm sorry. I'm not trying to be difficult. I just really don't know what to include.

---

### Post by LewRockwell on 2009-08-19
we've had that same Pentium 4 emachine(2.93Ghz) in the past

emachine replaced two power supplies and two motherboards on that one machine

given our personal and professional experience with that equipment you should always consider hardware failure when trouble-shooting any issues that might potentially be hardware related

.

---

### Post by rahrahmah on 2009-08-19
Yeah, it was a Christmas present from a room mate, and I was only 20 at the time, so that should give you an idea of how much was spent on it. I've also never heard of emachines in my life, except for this computer. It's been pretty good to me, though, except for the part where it came with no way to reinstall it's OS after an infection (hence why I'm on ubuntu now). 

I didn't think it was hardware because of similar problems on old threads (and new ones), and the timing was so coincidental. It looks like the fault may be my own, however. I got a good reply in the previous thread which suggested overheating, and since I had never dusted the inside of my tower (I had no idea I should! But the fan certainly seemed to need it.) this seems a probable candidate for the monitor issues. I know the fan sounds a lot healthier now, at least.

This hasn't helped my firefox problem though, which I still think is very much a problem. It can run as high as 100% if youtube is in fullscreen mode, and I feel like 60% of the memory being used is also kind of high (though I'm less familiar with this than CPU). Someone in another thread seemed to imply that the swap memory being used at all was a bad thing, and mine is sitting around 7%.

---

### Post by mike555 on 2009-08-19
What version of Firefox ? also have you tried running from the live cd and see if it has the same result? (of course it will be a lot slower). there is an hardware monitor applet you can get and it will show you how hard your cpu is working ... or of course you can just go to System>Admin. >system monitor

---

### Post by rahrahmah on 2009-08-20
I have no idea what version of firefox. I assume the newest one? Or else wouldn't it prompt me to update? If it's an older version of firefox would that make it run like this? 

The system monitor is how I was figuring out how hard my CPU was working already. Does the applet do something better? Like, more stats? Is it worth getting or should I just try running firefox from the CD without it?

---

