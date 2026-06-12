---
title: "Heat problem"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by avalanche-870 on 2010-07-15
So i am dual booting windows 7 and ubuntu on my laptop (Fujitsu siemens esprimo mobile v6545) and on ubuntu it gets really hot.
I've searched the internet but i can't find a solution, everyone is talking about monitoring the temperature but no one said how to put it down, and i really need to do something about that cause i like ubuntu but i can't afford to lose this laptop now. 

I found this way to know the temperature on the forum and here it is and i am not doing anything on the laptop:

avalanche@ubuntu:~$ acpi -V
Adapter 0: on-line
Thermal 0: ok, 47.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 97.0 degrees C
Thermal 1: ok, 47.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 97.0 degrees C
Thermal 1: trip point 1 switches to mode passive at temperature 94.0 degrees C
Cooling 0: LCD 0 of 15
Cooling 1: Processor 0 of 0
avalanche@ubuntu:~$

---

### Post by avalanche-870 on 2010-07-15
avalanche@ubuntu:~$ top

top - 23:41:47 up  1:15,  2 users,  load average: 0.49, 0.68, 0.98
Tasks: 146 total,   1 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.0%us,  2.3%sy,  0.0%ni, 92.1%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:   2056940k total,  1994496k used,    62444k free,   559224k buffers
Swap:   261112k total,        0k used,   261112k free,   640980k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2135 avalanch  20   0  275m  59m  25m S  3.0  3.0   3:59.92 chrome             
  971 root      20   0  141m  91m  26m S  1.7  4.6  10:45.69 Xorg               
 1349 avalanch   9 -11  156m 5508 4396 S  1.3  0.3   0:50.43 pulseaudio         
 1346 avalanch  20   0 31488  21m 6948 S  0.3  1.1   0:15.23 compiz             
 2230 avalanch  20   0 50108  13m  10m S  0.3  0.7   0:01.30 gnome-terminal     
 2265 avalanch  20   0  2544 1216  924 R  0.3  0.1   0:00.02 top                
    1 root      20   0  2796 1644 1200 S  0.0  0.1   0:00.33 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.05 events/0           
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm

---

### Post by bumanie on 2010-07-15
The temperature readout from acpi -V looks fine - go [here]("http://www.columbia.edu/~ariel/acpi/acpi_howto.txt") to read up about acpi

---

### Post by Yarui on 2010-07-15
In my experience most laptops get extremely hot regardless of the OS.  Any time you are running anything processor intensive it will lead to a lot of heat and laptops' ability to dissipate that heat is limited.

The only ways I know of to help cool laptops are to make sure they are resting on a hard surface so that none of the air vents are blocked and maybe get a cooling dock, but I have never tried those out so I can't say whether or not they work very effectively.  Other than that the only thing I know to do is to avoid overusing anything that is processor intensive.

---

### Post by emoguitarist06 on 2010-07-15
[QUOTE=Yarui;9594693]In my experience most laptops get extremely hot regardless of the OS.  Any time you are running anything processor intensive it will lead to a lot of heat and laptops' ability to dissipate that heat is limited.QUOTE]

I've personally experienced my Compaqs and Vaios I'ved owned that they did tend to get a lot hotter under Windows as opposed to Ubuntu. Actually I had a Compaq that had a drive that was failing and the graphics failed and after like 1 minute of being booted into Windows it would shut down and it felt extemely hot! But under Ubuntu never had the problem so I got couple more months out of it before it HDD finally went to SH** :twisted:

---

### Post by cloyd on 2010-07-15
47 C really isn't hot. There are applets for panel that will monitor you cpu in C or F. You acpi says critical is at  97.  Mine says critical at 100.  I've never seen mine hotter than 65, though I usually start shutting down a video or something like that when I see this happen.  I've been told that things are really fine until about 75 or 80.  If things the machine starts acting funny, or display acts up, or such, I'd shut things down. I very much understand your concern . . . I feel the same way. But I wouldn't even think of worrying if temps stay in the 60's C.

---

### Post by Yarui on 2010-07-15
> **emoguitarist06 said:**
> I've personally experienced my Compaqs and Vaios I'ved owned that they did tend to get a lot hotter under Windows as opposed to Ubuntu. Actually I had a Compaq that had a drive that was failing and the graphics failed and after like 1 minute of being booted into Windows it would shut down and it felt extemely hot! But under Ubuntu never had the problem so I got couple more months out of it before it HDD finally went to SH** :twisted:
I wasn't trying to say that all OSs use the processor equally.  I just meant that in my experience laptops tend to get hot if you are doing much on them.  Since every OS has different processes running that put a different load on the processor, it makes sense that while idling one would be hotter than another.  I just feel that laptops generally get hot on any OS if you are actually using them.

---

### Post by avalanche-870 on 2010-07-16
I know that 47 Celsius isn't that bad for the machine but it is bad for my lap, that temperature was when my system was not running anything, so it's expected to get much higher and the system doesn't get that hot under windows. I want to keep temperature as it was under windows if possible.
As i was searching this forum and other sites I read things about removing the drivers for graphics card (ATI Rodeon HD 3450 in my case) and changing the Kernel (i don't know  what that is), will that help????

---

### Post by mastablasta on 2010-07-16
you also have graphic effects turned off? no wireless card?
 
Sometimes temp can increase because of high outside temperature. other times something is maybe not cleaned (puff of air could solve this).
 
You say it never gets so hot in windows, then how hot does it get there? did you use a temp monitor to see the real temperature? 
 
also what is the optimum temperature for your processor. maybe the OS is keeping it "warm" for later work.

---

### Post by avalanche-870 on 2010-07-16
effects are set to "extra" but no compiz or anything like that, wireless card is not active but sure I'll need it sometime (which will add to heat), it has nothing to do with how hot it is here or dust in laptop cause things go smooth under windows, about windows temperature: never measured it but it must have been significantly lower cause the difference is very apparent(laptop now heats my lap and fingers in an annoying way). as for my processor i don't know the optimum temperature but it is a celeron 2.1 GHz single core (I know it is old but i like it). so is there anything i can do?? anywords on the graphics card driver or the kernel or any other thing?? help I'm desperate...

---

### Post by avalanche-870 on 2010-07-17
nobody got a solution????

---

### Post by linux18 on 2010-07-17
```
 cpufreq -f 1 
```set your CPU to its lowest speed setting

---

### Post by avalanche-870 on 2010-07-17
avalanche@ubuntu:~$  cpufreq -f 1
No command 'cpufreq' found, did you mean:
 Command 'cpufreqd' from package 'cpufreqd' (universe)
cpufreq: command not found



what to do???

---

### Post by yossell on 2010-07-17
> **avalanche-870 said:**
> effects are set to "extra" but no compiz or anything like that

I believe setting effects to "extra" *is* running compiz.

The drivers for your card can make a difference to temperatures; certainly, in my case, the nvidia driver seems to make use of power-saving features which cool the computer down.

Downclocking the chips also makes a big difference. I'm not sure of the command line, but from the panel you can add and enable cpu frequency scaling monitor applet, to run your cores slowly. I don't know if this is just a gui way of running linux18's commands though.

Finally, installing and running the program powertop can help you further analyse what drawing power and will give suggestions for killing processes or enabling features that improve battery life and lower temps.

---

### Post by avalanche-870 on 2010-07-17
i removed the linux install (through wubi) installed it again and this time i didn't install ATI drivers and didn't set effects to extra (system is as clean as Canonical created it). yet i still get high temperature i tried to put the cpu frequency scaling to the panel and i got this:

CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.


after that scale appears in the panel displaying 2.16(100%) and says unsupported (taking in consideration that i installed acpi, don't know if that would be an information of use or not but i'm just an end user and don't get this stuff )

so what should I do???

---

### Post by Windows Nerd on 2010-07-17
47 degrees C is NOT very hot. Most desktops will run at this temp or above (due to poor case design and crappy stock coolers). My laptop that I am using at this moment to post this reply runs at ~55C idle and at 65C when running a heavy application or after the laptop has been running for a couple days straight in the middle of the summer. I have been using this laptop for 4 years now and the hardware still runs great. 

Laptops typically run hot, and unless the heat causes some problems with your computer (like random shutdowns), I would not worry about it. 

Scott

---

### Post by avalanche-870 on 2010-07-17
it's not just the hardware that bugs me, this heat (that i don't experience in windows) is bad for my thighs upon which I place the laptop and my fingers (touch pad is really hot), and since the device is cooler in windows I believe that its not the norm for my hardware and that lowering temperature can be achieved in ubuntu, just when the right guy with the right knowledge sees this post

so ""right guy"" where are you???

---

### Post by yossell on 2010-07-17
Yeah, I'm with you - on all my default installs with Ubuntu, my computer has run hotter than under windows. It's taken some effort and tweaking to get temps down to parity.

---

### Post by avalanche-870 on 2010-07-17
effort is no problem, i'll do what it takes to bring the temperature down

---

### Post by techunit on 2010-07-17
It is under a sticky on the general help forum... What you have to do is install the karmic kernal and it doesn't get as hot... I thought mine was getting hot but 90 degrees is nearly twice as hot as I was at.

[Link..]("http://ubuntuforums.org/showthread.php?t=1469475")

---

### Post by 2hot6ft2 on 2010-07-17
I don't do wubi's but right click on the top panel and select Add to panel. Select CPU Frequency Monitor, click Add then Close.
Left click on the new applet in the top panel and set it to Powersave.
I don't know if it will work right with a wubi, but in Karmic it was set to Powersave by default and in Lucid it's set to On Demand by default which runs hotter.

Might have better luck with a real install.
:popcorn:

---

### Post by yossell on 2010-07-18
> **avalanche-870 said:**
> effort is no problem, i'll do what it takes to bring the temperature down

Glad to hear it - but I haven't heard what happened when or went wrong when or even if you tried the suggestions of my first post.

---

### Post by S.R on 2010-07-18
When your laptop is getting hot is the fan running slower then it does  in windows or about the same?

There is a DIY for controlling fan speed at  [http://wiki.archlinux.org/index.php/Fan_Speed_Control](http://wiki.archlinux.org/index.php/Fan_Speed_Control) .... best of luck.

Never mind forgot you were running in WUBI.

---

### Post by cloyd on 2010-07-19
I have one other suggestion. Really, whenever possible, I use a lap desk of something flat (a cool pad -- even if the fans in the cool pad don't work.)  Cool pad cost more than they should, and my experience is that the fans go out because of bad power connections, but some kind of lap desk helps. Cool pads DO help when they work. One, you don't feel the heat directly. Two, by using a lap desk, you make sure that you do not obstruct cooling vents.  I wish you luck on your quest, but it sounds like you'd like to keep your computer down in the 40's when it is running under a load, and I think that just may not even be possible. Probably your best bet is to to buy a cooling pad with fans to help cool your machine. If the fans go out, use the pad as a lap desk anyway, and it will help protect you from the heat and do a little to keep the machine cool.

---

### Post by avalanche-870 on 2010-07-19
> **cloyd said:**
> I have one other suggestion. Really, whenever possible, I use a lap desk of something flat (a cool pad -- even if the fans in the cool pad don't work.)  Cool pad cost more than they should, and my experience is that the fans go out because of bad power connections, but some kind of lap desk helps. Cool pads DO help when they work. One, you don't feel the heat directly. Two, by using a lap desk, you make sure that you do not obstruct cooling vents.  I wish you luck on your quest, but it sounds like you'd like to keep your computer down in the 40's when it is running under a load, and I think that just may not even be possible. Probably your best bet is to to buy a cooling pad with fans to help cool your machine. If the fans go out, use the pad as a lap desk anyway, and it will help protect you from the heat and do a little to keep the machine cool.


I am actually using one and it is still running in 50s and I don't want it to run 40s as you said, I want it to run 30s :D... just kidding
I just want it to run at a temperature that was like in windows (dunno how much was that but i can feel it with my hands)

---

### Post by avalanche-870 on 2010-07-19
> **yossell said:**
> Glad to hear it - but I haven't heard what happened when or went wrong when or even if you tried the suggestions of my first post.


About the graphics card: I reinstalled ubuntu and this time did not install the graphics driver and still temperature is high, and there was nothing in the graphics driver that says anything about power saving.

About the cpu frequency scaling monitor applet: it gives me an error that says (CPU frequency scaling unsupported:You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.) then the app apears in panel showing that the processor is running at 2.16(100%)

About powertop: I installed it but i can't find it to run it (like i said i am not a linux expert)

One more thing: when i removed the ubuntu i tried another distro: Linuxmint, it looks minty and refreshing but still the heat and the CPU frequency scaling problems persist.

Thanks for caring and for help

---

### Post by yossell on 2010-07-19
you can run powertop by opening a terminal and typing 

sudo powertop

followed by your password BUT if you can't downclock your chip then I'm afraid I don't think it's going to make a great deal of difference. I don't know why cpu frequency scaling is unsupported - that seems unusual - but it may well be because it's a wubi install.

---

### Post by debjit_bis08 on 2010-07-19
Try cleaning the fan if you have not already tried it. My laptop used to shutdown due to high temperatures and too much dust blocking the vents was the problem.

Cheers !!

---

### Post by colin.p on 2010-07-19
> **avalanche-870 said:**
> 
About the cpu frequency scaling monitor applet: it gives me an error that says (CPU frequency scaling unsupported:You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.) then the app apears in panel showing that the processor is running at 2.16(100%)


If you click on the freq monitor, does it allow you to change the speed?
Mine alway defaults to "Performance", on boot up, then I manually change it.
BTW, on my Dell 1545, my temps are into the low sixties, about 5-10 degrees higher than win 7. I find the fans don't run quite as long as in 7, but still nothing to get too concerned about. However, my laptop isn't used as a laptop, it sits on a desk with a small piece of door casing wedged under the back to lift it up. Quite a bit cheaper than a pre-made laptop cooler.

Colin

---

### Post by avalanche-870 on 2010-07-21
> **yossell said:**
> you can run powertop by opening a terminal and typing 

sudo powertop

followed by your password BUT if you can't downclock your chip then I'm afraid I don't think it's going to make a great deal of difference. I don't know why cpu frequency scaling is unsupported - that seems unusual - but it may well be because it's a wubi install.

here is what came out:



Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (33.3%)
polling           7.8ms ( 0.1%)
C1 mwait          0.0ms ( 0.0%)
C2 mwait          0.1ms ( 0.0%)
C3 mwait          2.9ms (66.6%)

Wakeups-from-idle per second : 228.8    interval: 15.0s
Power usage (ACPI estimate): 29.6W (0.6 hours) (long term: 29.7W,/0.6h)

Top causes for wakeups:
  46.5% (174.7)   PS/2 keyboard/mouse/touchpad interrupt
  24.4% ( 91.8)   [kernel scheduler] Load balancing tick
   5.0% ( 18.9)D  gwibber-service
   5.3% ( 19.9)   desktopcouch-se
   3.0% ( 11.3)   [ahci] <interrupt>
   2.7% ( 10.3)   [eth0] <interrupt>

Suggestion: Disable the unused WIFI radio by setting the interface down:
 ifconfig wlan0 down

-------------------------------------------------------------------------------------------------------------------------------
so what does this mean??? can I scale down the cpu or not????

By the way, I found my temperature under windows it is around 40 give or take one. that means that my ubuntu is 10 to 15 degrees Celsius higher.

---

### Post by avalanche-870 on 2010-07-21
> **colin.p said:**
> If you click on the freq monitor, does it allow you to change the speed?
Mine alway defaults to "Performance", on boot up, then I manually change it.
BTW, on my Dell 1545, my temps are into the low sixties, about 5-10 degrees higher than win 7. I find the fans don't run quite as long as in 7, but still nothing to get too concerned about. However, my laptop isn't used as a laptop, it sits on a desk with a small piece of door casing wedged under the back to lift it up. Quite a bit cheaper than a pre-made laptop cooler.

Colin


No it does not. it doesn't give me anything when i press it and when i move the cursor over it, it displays (frequency scaling unsupported 2.16GHz (100%)  )

---

### Post by avalanche-870 on 2010-07-27
No word about changing the kernel????

---

