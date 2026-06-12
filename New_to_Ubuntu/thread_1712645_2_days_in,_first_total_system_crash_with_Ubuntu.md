---
title: "2 days in, first total system crash with Ubuntu"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by Alancj05 on 2011-03-23
Hi all, I really like Ubuntu 10.10 so far... I'm new to Linux, and just zeroed out my old Vista install a few days ago. Vista was getting slow and unstable, I was getting some random blue screens of death and restarts.

But then I had the same damn thing happen with Ubuntu (total system freeze), but worse, I had to flip the PSU switch and unplug the entire machine to get it to start up again. This is the first time I've had to go to those lengths to get it to boot. 

The question is... Is this all because of the new ram I installed a couple weeks back? I was running 2 matched 1 gig sticks for years, in dual channel mode, then I decided to add another 2 gigs in the form of a single stick in one of the other 2 empty slots I had. I'm not sure if that's when these blue screens started... but does this even make sense? The system was over-clocked at the time, so maybe adding memory mucked the works? According to my Mobo manual it should support mixed sticks in dual channel mode. I just don't know if that goes for an odd number.

Motherboard: Gigabyte GA-P35-DS3R Rev. 2.0
Memory: Patriot 2 X 1Gig. and Corsair 2 Gig Both DDR2, 800 MHz
CPU Intel E2160 1.8 GHz @ 3.0 GHz. Dual Core
Ubuntu 10.10, installed from live CD, on a single SATA2 drive.

Thanks, Alan

Should I start new threads for the other questions I have? All in Beginner Talk?

---

### Post by samcot on 2011-03-23
Are you saying that the Vista system started crashing and restarting only after you changed the RAM? And now it seems that Ubuntu is doing it? 
 
If that is the case, if you still have the original RAM, can you put it back and try that for a little while, just to see?
 
I'm just a newbie, so maybe someone else has got a better suggestion!

---

### Post by Alancj05 on 2011-03-23
I still have the original ram in it. I just added a stick. So I could remove the new Corsair, and see if I don't get a crash after several days of working on it. Thing is, these were rare when they happened, so... it could take a long time to know for sure.

---

### Post by cascade9 on 2011-03-23
> **Alancj05 said:**
> According to my Mobo manual it should support mixed sticks in dual channel mode. I just don't know if that goes for an odd number.

Odd number of sticks = single channel mode (unless you are running LGA1366 or some of the xeon systems, then 3 sticks can run in triple channel mode). 

Random bluescreens and restarts with vista, and crashing with ubuntu?...its probably a hardware issue. Sick motherbaord/chipset, or CPU, or power supply are the mostly likely causes. 

Thats assuming that you are back running at stock speeds, if you are still overclocked then then you could have a degraded CPU or motherboard. Try going back to stock speeds if you are still overclocking.

---

### Post by samcot on 2011-03-23
Like Cascade said, it could be a hardware issue. But it's so easy to test it for a couple of weeks with the original RAM and without overclocking, and you can always add the memory stick again. You wouldn't have to re-install any software, either.

---

### Post by crispy_420 on 2011-03-23
Could always run memtest for install media to know for sure. In my experience, may not be reflected by all, but Linux seems to put your memory to work. Not sure if that is fact or just my experience.

---

### Post by Alancj05 on 2011-03-23
"but Linux seems to but your memory to work"

What?

I'm running at stock speeds right now, which is sloooow. Never intended to run this bitty CPU at stock. It was cheap and good clocker the forums said in ages past. 

Is there a way to find the Memory FSB speed currently in use in Ubuntu? IIRC under vista after I installed the new stick specy and cpuz told me 400 MHz FSB, which is half the 800 stock speed these memory sticks run at. I have no Idea what it was with just the original 2 1 gig sticks, OCed and dual channel.

I'm really pretty clueless with over-clocking... I just followed some directions and fiddled until my system was sable when I built it Nov. 07. 

I'll run a mem test. I think I know how...
Thanks,

---

### Post by Dutch70 on 2011-03-23
You may also want to check the temperatures of your cpu & your disk & make sure the computer is nice & clean.

---

### Post by mcduck on 2011-03-23
> **Alancj05 said:**
> "but Linux seems to but your memory to work"

What?

I'm running at stock speeds right now, which is sloooow. Never intended to run this bitty CPU at stock. It was cheap and good clocker the forums said in ages past. 

Is there a way to find the Memory FSB speed currently in use in Ubuntu? IIRC under vista after I installed the new stick specy and cpuz told me 400 MHz FSB, which is half the 800 stock speed these memory sticks run at. I have no Idea what it was with just the original 2 1 gig sticks, OCed and dual channel.

I'm really pretty clueless with over-clocking... I just followed some directions and fiddled until my system was sable when I built it Nov. 07. 

I'll run a mem test. I think I know how...
Thanks,
DDR2-800 = FSB 400 MHz = PC2-6400 = memory clock of 200MHz. ;)

I doubt your RAM was running half the stock speed, more likely it's just a question of different way of representing the RAM speed.

And the first step of troubleshooting possibly hardware-related problems on overclocked computer is returning it to stock speed. And of course if the problem occured after adding the new RAM module, removing it would be a decent idea as well. And rnning the memtest, like suggested (remember that running it once is useless, you should let it run at least overnight).

---

### Post by tordeu on 2011-03-23
I suggest running memtest from the install cd as well.

And overclocking can always lead to stability issues, so you need to find out how much you can overclock without the system becoming instable. 

And to test that a certain amount of overclocking is table, it is not enough to see if it boots. You should also run some kind of intense benchmark for as long as you like (I would say that about 10min is a good indicator, but there are people who run those things for hours), because system might be "stable" when idling, but once the cpu etc. is really stressed, it might become instable, as only then problems with overclocking might occur.

---

### Post by crispy_420 on 2011-03-24
memtest will take hours if let run to its full but a failed stick should be found without such an extended period being needed.

And as far as being reported as half speed. That happens:
[http://www.tomshardware.com/forum/244177-30-pc8500-running-half-speed](http://www.tomshardware.com/forum/244177-30-pc8500-running-half-speed)

Let me know if I had any typos here.

---

### Post by Alancj05 on 2011-03-24
Thanks guys. I recently had the box apart when I was wiping the main hard drives (disconnecting the backup drives...) so I also used my air compressor to blow all the dust out. It had been way to long.

I ran two memory tests from the dual boot menu (Grub2?) once at stock speeds and once again at the overclocked settings I was using. This is with the three sticks in the computer. I didn't get any errors. I let it run until it said I had passed, which took about 45-60 minutes.

As far as long term stability and stress testing, I have run the computer pretty hard over the past year when I installed the Boinc client (distributed, volunteer computing). So it's stable at the settings I was using with the two sticks. With three sticks, well, I'm still not 100%
sure if the system got unstable before or after I put it in. I had been wanting to switch to something more stable since this summer.

 I was definitely glad to have the extra memory when I was trying to get Netflix to play in virtualbox under XP or Win7. Not that the playback was any good in any case.

I'll try a find the hardware temps I'm running at and I'll run another memtest from the install disk.

---

