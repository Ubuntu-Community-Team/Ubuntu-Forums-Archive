---
title: "X won't start after upgrading RAM?????"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-16
after adding more RAM, ubuntu refuses to launch X. the only thing i can think of that may have caused this was removing the graphics card and then reinstalling it. (it was taken out for other unrelated reasons)

it must be seated in the slot correctly, or else why would anything show up at all when i turn on my computer???

I get this message: 

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
(yes or no)"

i don't even know why the two are related at all. never once have i had problems with the graphical part of an OS after simply adding more RAM. 

anyone have any ideas/suggestions for this absurd error? 



on a second note (just ranting about why i had to buy more RAM):

1. why is swap space stored in a separate partition? this doesnt seem like a bright idea. it makes increasing the swap space impossible without totally reformatting my hard drive. (no, i do not have any unpartitioned space left)  ***i have 1 GB of swap space on my drive***
      in windows, all i have to do is simply right-click on my computer and click properties; go to memory, and adjust the size of the page file. it's a snap. 
with ubuntu, i have to go out and buy more memory, or reformat the entire drive and ***choose more swap space*** during the installation


2. why is it seemingly impossible to adjust the buffer on sound? when i bought this memory, i was praying that the ridiculous stuttering would go away. it was becoming unbearable. 

         :steps that i tried before i resorted to buying RAM:
- yes, i can get decent sound quality *if i completely disable all desktop effects and run metacity*, but i shouldn't have to. i have a nice video card that should easily handle this. 
- i have followed various guides that suggest adding an "asound.conf" file in my home directory. they don't do anything at all, as pulseaudio, ALSA, and OSS completely ignore any configuration file i make; whether it be in the /etc/ folder (for a system setting) OR in the /home/ directory (for a per-user setting). ***(i also checked to make sure the file was "set up" correctly, if anyone wonders)

                   :additional comments regarding sound:
      furthermore, there is no GUI to adjust the sound buffer. (if there is, **please** tell me what it's called :D)
      what's more, why does having compiz enabled affect my sound quality at all??? my graphics options and my sound quality are completely unrelated. both are in separate cards. (don't tell me...it's because my linux hates my ATI card and uses the CPU to do all my graphic computations. ](*,) )
      when i was running a ***slimmed down*** version of windows vista, with the **same 1 GB of RAM**, the sound never stuttered and distorted. ever. i could be running 3 instances of FSX and still have decent sound. linux is clearly not making full use of my hardware. 

3. why does firefox take up 200MB of system RAM? that is ridiculous (or maybe i'm just behind the times ;) )
     ***the above statement (#3) was made using firefox 3.08 with 2 tabs open; wikipedia and google, after letting firefox run for 3 hours on the same pages***

idk, sorry guys if i'm ruining the vibe here, just need to rant a little. 
please don't take this as me criticizing the OS, i just want to know what's going on. maybe some really smart people out there can help me out :D

---

### Post by por100pre1 on 2009-04-17
First, run a Memory Test from an Ubuntu Live CD...

by the way, **please try to be *concise* when posting. The more you write, the less likely you'll get any answer.**

---

### Post by element_G on 2009-04-17
1. IIRC, I think you CAN use a "pagefile" in ubuntu

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) :popcorn:

2. Stuttering sound might be due to pulse audio (esp. if you are running JAUNTY!)
see: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=1084919&page=6](http://ubuntuforums.org/showthread.php?t=1084919&page=6)

3.Firefox is like that, esp. if you have lots of TABS open

as for your misbehaving Xorg, I'm not sure what to do there

---

### Post by asuastrophysics on 2009-04-17
> 1. IIRC, I think you CAN use a "pagefile" in ubuntu

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 
thanks that was what i was looking for ;)

as for my X not starting...

it was just me being stupid, sorry guys ](*,)](*,)](*,)](*,)
the card didn't "click" in all the way. 

that's bizarre though, because it when i turned the power on i could see the startup screen and ubuntu loading. i guess it wasn't enough to launch X. 

i ran memtest86+ and everything looked good. 

maybe i should spend a couple extra minutes first and then make a thread? 

:roll:

---

### Post by LowSky on 2009-04-17
Personally if you have over 2GB of RAM you will bever use it. I have 4 and have never had my system use more than 900MB

heres an awesome screenshot of me doing way too much on my PC, sure having a quad-core helps, but RAM is what is needed to handle the load.

---

