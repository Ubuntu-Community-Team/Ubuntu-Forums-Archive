---
title: "pSX sound underrun problem!"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by 7G Operator on 2010-04-11
After struggling for many a time with pSX and the sound underrun problems i was consistently having, and trying various sound related things to remedy the situation, including but not limited to, pulseaudio killage, running as root, researching sound card, even installing a RT kernel (which might i add is well worth doing if you plan to start utilizing audio capabilities on ubuntu ;) close to zero latency, yes please! ;) and so on and so forth, i happened to accidentally stumble across the solution to my dillemma. 

When using pSX in a small window it appeared everything ran perfectly well no sound skipping slowing down of game e.t.c. And then having read various articles about how pSX faithfully emulates and does not improve upon the playstation model it suddenly came to my attention...what is the maximum resolution for playsation? low and behold around 480x600 resolution. Changed the display settings on my computer temporarily to 480x600 and bingo bango problem solved. Runs fine, full speed with no sound problems (thus far) i haven't tried reducing the latency right down, as i was keen to post my experience on here to any one who still might be suffering with pSX, but with the real-time kernel on board, perhaps i will be able to get latency down to a good level ;). One other thing i did was to slightly edit some configuration settings after installing the real-time kernel (although im seriously thinking it now has very/little nothing to do with the kernel and everything to do with resolution;) This involved editing the security/limits.conf file as to allocate a certain amount of memory and cpu usage/priorities to the "audio" group, which i then added myself to. 

If this helps at least one other person, having similar issues with pSX then it was well worth the research/effort ;). 

For reference i am using a samsung n130 netbook, 9.10NBR and now that i have ascertained the problem it seems to be fine using pulseaudio, (no need to disable it;) and not having to  do much other than temporarily adjusting the display resolution. 

Happy gaming dudes/dudettes

- 7G operator ;)

---

### Post by 7G Operator on 2010-04-12
I just tried a couple more things, to ascertain exactly what it was that was causing my version of pSX to work properly. Firstly i tried my usual kernel for every day usage 31.-20. I then set the display to 480x600.....

*I tried first running pSX without disabling pulseaudio, full screen. FFVII. The video quality was o.k but the sound did skip very very slightly a number of times both during the intro FMV and for the first few bits of dialgoue box. (*No where near like the choppyness of running at a higher screen res though.) General Sound quality did seem slightly poorer than to be expected.

*I then tried the same but disabling pulse audio with the pulseaudio -k switch (after disabling autospawn a long time back:wink:. Tihs warranted a perceived improvement in general sound quality, very very slight lapses in sound quality occured.

I then rebooted by comp (Which is For the purpose of diagnosing, and not boasting :wink: *Samsung N130 netbook, 
UNR 9.10, 
1.6 GHZ atom, 
1GB RAM, 
some probably fairly crappy generic onboard intel sounddoolally ALC269 i think) 

and selected the 2.6.31-9-rt Kernel from the grub booter. (This is a Real-Time kernel allowing for potentially low latency sound mitigation in recording/sound engineering scenarios, (it's the sorta shizz i like to mess with, being interested in the sound bizniss and all, although i've only just migrated to it having been a keen proponent of Cubase in the past, but deciding to try out some Linux stuff:wink: it is i believe one of the kernels used by ubuntu studio, although rather than install "ubuntu studio" i instead decided to just pick the tasty bits from it :wink: and install only the audio apps i feel i might want to experiment with. Anyways i installed that kernel, and tweaked a bit. Now i think it was perhaps this tweaking which has in fact increased pSX's efficiency, although i have done a test with kernel tweaks on the R-T kernel, i have not actually just tweaked the kernel of the latest kernel edition. (If you get me:wink: Basically the kernel tweak is.....Well i'll find it but it involves adding a couple of simple parameters to your e.t.c/security/limits.conf file...
[FONT=monospace]
[/FONT]*(Unless you wish to engage/experiment with audio production/mastering stuff e.t.c, then skip down to "Real-Time Support".)

[https://help.ubuntu.com/community/Ub...dioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation") - For the source material.

sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
 sudo adduser <username> audio


You may want to research this part independantly as i was told about a "nice - 10" command, and came to the conclusion (which upon further research appeared somewhat 50/50 shared/debateable, that if you award memlock - unlimited, if there is a problem/bug in your program you are essentially awarding full memory rights to that program, which im thinking might possibly cause a crash. *shrugs So i instead assigned half my ram 512000. 
(*Although i'm sure i'll probably up that at a latter date if Cubase and general RAM neccessities for DAW programs are anything to go by :wink: 

Anyways Basically upon reading that page it says nowhere about the specific kernel so im thinking the kernel tweaks may be all you need :wink:. 

Anyways loaded Real-time kernel (*tweaked:wink:, set display 480x600, tried pSX with pulseaudio running, perhaps one extremely slight happening with the sound, when first box of dialogue appears.

Killed pulseaudio, and reloaded pSX and finally no problemos!!. Again FFVII was the benchmark game i used for testing. 

Hope this helps some dudes/dudettes =)

Dan - 7G Operator

---

