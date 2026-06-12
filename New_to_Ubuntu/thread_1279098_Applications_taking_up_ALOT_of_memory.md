---
title: "Applications taking up ALOT of memory?"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by mlthmp on 2009-09-30
I noticed the other day that when my computer slows down that its always the same 2 programs.

I've seen Firefox using 1.6GB of my memory before (out of 3GB total) and Pidgin messenger has used up to 1GB before when it locks up. 

These two programs are just sucking down TONS of my PC's memory. Is this something I've done wrong during the install process, or is this a normal thing? Seems to me like whenever my system shows down one of these 2 programs us causing it.

Anything I can try to solve this, or is it natural for these programs?

Using Ubuntu 8.10 if that helps / matters.

Thanks!
Mike,

---

### Post by scragar on 2009-09-30
Mind me asking what you are doing using them? I've never seen firefox using that much ram before(well, except when I do it on purpose :p), and as far as I'm aware pidgins footprint isn't really that large at all.

---

### Post by howefield on 2009-09-30
> **mlthmp said:**
> I've seen Firefox using 1.6GB of my memory before (out of 3GB total) and Pidgin messenger has used up to 1GB before when it locks up.

Fairly natural that they would use the available memory. Funny that..  :)

Firefox uses a ton of memory especially when using flash, in my experience. Not so sure about pidgin though, what are you using it for ? Are you pushing a lot of data through irc, for instance ?

---

### Post by LewRockwell on 2009-09-30
something isn't right

.

---

### Post by mlthmp on 2009-09-30
When Firefox bogs down, I usually have 3 windows open. One for instance is an Oasiz chatroom. I try to keep the second on my search page most of the time, and the third is whatever im doing ATM.. Browsing forums, etc. I rarely ever go on sites with flash, but when I do I always close down all but that window.

Pidgin.. Heck, it does it whenever it wants to =( If it'll help next time I catch it I'll try and take a screenshot of my resource manager when FF acts up. Usually I only have 1 or 2 windows open. I rarely ever open more than 3.

---

### Post by wobin77 on 2009-09-30
Don't compare *nix with Windows. 
*nix uses most of RAM available, when it needs more it will clean some up. 
Does the mem usage uses a swap or only the RAM? 

what does this code output?
```
free
```

---

### Post by XCan on 2009-09-30
Well, for me Pidgin randomly starts to eat memory until it crashes, all plugins and unneeded crap turned off, perhaps the OP is running into that bug with Pidgin? Regarding, firefox, I've had now FF running for 11 days and it's using RSS 342 MB with 5 tabs open.

---

### Post by mlthmp on 2009-10-01
[http://img41.imageshack.us/img41/542/screenshot1do.png](http://img41.imageshack.us/img41/542/screenshot1do.png)

Well, I got a screenshot of my resource manager showing FireFox using 1.1GB of memory just now. 

Also, while it was bogging down I used the free command as suggested above, this was the readout

             total       used       free     shared    buffers     cached
Mem:       3102348    2904012     198336          0      77544     851004
-/+ buffers/cache:    1975464    1126884
Swap:      1646620     315020    1331600

---

### Post by wobin77 on 2009-10-02
I know FF is a mem eater, but 1.1Gig seems alot to me. 
Also i find it strange that your system uses your Swap file alot more than the actual RAM. 
Seems there s some kind of memoryleak. 
What version of FF are you running? 

I m not sure about this all. Hopefully a more experienced user will have an answer.

---

### Post by freak42 on 2009-10-02
does simply closing firefox (all instances) and restarting it help?
For how long do you keep firefox open? (hours or days?)

---

### Post by t0p on 2009-10-02
That statement "Linux will use all available memory" is a crock.  I've got 2 gigs memory on this machine and usage hasn't even got to half of that yet.

The programs that the OP identifies as being the resource hogs are both internet apps.  I suggest using a tool like netstat to see if there's any unusual net activity going on when the RAM usage spikes.  Check if the computer is "phoning home" or setting up multiple connections or something.

---

### Post by Paqman on 2009-10-02
> **t0p said:**
> That statement "Linux will use all available memory" is a crock.  I've got 2 gigs memory on this machine and usage hasn't even got to half of that yet.


It's *sort of* right. The system will use any available memory for caching, which is a good thing. But an app itself will eat as much memory as it is actually using. If it's gobbling your memory, all is not well. >1GB for Firefox or Pidgin ain't right.

---

### Post by wobin77 on 2009-10-02
[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by mlthmp on 2009-10-02
> **wobin77 said:**
> I know FF is a mem eater, but 1.1Gig seems alot to me. 
Also i find it strange that your system uses your Swap file alot more than the actual RAM. 
Seems there s some kind of memoryleak. 
What version of FF are you running? 

I m not sure about this all. Hopefully a more experienced user will have an answer.

I'm using 3.0.14 currently.

> **freak42 said:**
> does simply closing firefox (all instances) and restarting it help?
For how long do you keep firefox open? (hours or days?)

Closing it and reopening it doesn't help. What I have to do, is open my resource manager, and physically kill the process and then reopen FF. Doing that  does free the memory back up, but just closing FF from the browser and reopening doesn't. Also, nah I don't leave FF open for long at all. I try to keep my computer "sessions" to around 2 hours at max at a time. Sometimes its longer, but usually right around 2 hours or so.

I will also look into "netstat" as tOp suggested. 


I appreciate all the responses guys. Maybe sooner or later this will get "under control" abit. 1.1-1.6GB just seems like ALOT more than normal to me. 

Mike,__[]("http://ubuntuforums.org/member.php?u=380385")

---

### Post by LowSky on 2009-10-02
It way beyond normal. Are you using any plug-ins with firefox?
 also try this
[http://www.simplehelp.net/2006/07/11/how-to-lower-the-amount-of-memory-that-firefox-uses/](http://www.simplehelp.net/2006/07/11/how-to-lower-the-amount-of-memory-that-firefox-uses/)

---

### Post by relay_man on 2009-10-02
FF can and does eat much memory depending on many variables.

Look here:   [http://kb.mozillazine.org/Reducing_memory_usage_(Firefox](http://kb.mozillazine.org/Reducing_memory_usage_(Firefox))

and here:  [http://kb.mozillazine.org/Standard_diagnostic_(Firefox](http://kb.mozillazine.org/Standard_diagnostic_(Firefox))

---

### Post by mlthmp on 2009-10-04
I've tried the above with FF, so far its still doing the same =(

Also, here is a screen shot of Pidgin acting up. I grabbed this shot while it was using 1.6gb. I also right clicked on it in my upper task bar just to show you guys what it does when it happens. It totally freezes.

[http://img29.imageshack.us/img29/4795/screenshot1ni.png](http://img29.imageshack.us/img29/4795/screenshot1ni.png)

This time, I didn't close the program. I let it sit there to see what it did. When I took this SS it was at 1.6gb. It rose to 2.0 and the application crashed and my system resources were released.

Opened the program back up, and its working like normal.

---

### Post by mlthmp on 2009-10-06
> **mlthmp said:**
> I've tried the above with FF, so far its still doing the same =(

Also, here is a screen shot of Pidgin acting up. I grabbed this shot while it was using 1.6gb. I also right clicked on it in my upper task bar just to show you guys what it does when it happens. It totally freezes.

[http://img29.imageshack.us/img29/4795/screenshot1ni.png](http://img29.imageshack.us/img29/4795/screenshot1ni.png)

This time, I didn't close the program. I let it sit there to see what it did. When I took this SS it was at 1.6gb. It rose to 2.0 and the application crashed and my system resources were released.

Opened the program back up, and its working like normal.


Any ideas or suggestions on this one? =(

---

