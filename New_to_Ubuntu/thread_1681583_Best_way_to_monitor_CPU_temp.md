---
title: "Best way to monitor CPU temp?"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-02-04
I'm running 10.10 on a Dell Inspiron 1520 and am getting some discrepancies when i try to check the CPU temps.

Conky lists 82 C and i8kmon lists 67 C.

What is the best way to check the temp?

---

### Post by pqwoerituytrueiwoq on 2011-02-04
sudo apt-get install sensors-applet
sudo sensors-detect
then add it to the the gnome panel
[IMG]http://i54.tinypic.com/aaymp2.jpg[/IMG]

---

### Post by cloyd on 2011-02-04
I am doing a little checking, and it really looks like i8kmon is specific for dell, and may be much better than the acerhdf that I have acess too. I found the info here if you haven't looked at it . . .

[http://linux.die.net/man/1/i8kmon](http://linux.die.net/man/1/i8kmon)

It looks like there are lots of options for setting up the fan, which should help you if it really is running that hot.  I'm really interested in what the panel apt or sensors command may say. I do know that my conky (I'm really not fluent with conky, but I have it and like it and have modified it a _little_) uses the sensors command to reprort the temperatures. 

i8kmon sounds like a pretty good thing with more options than acerhdf.

---

### Post by Dutch70 on 2011-02-04
Looks like you've got some good answers here. I just want to add that you can also check the temp by going to System > Admin > Disk Utility and check the smart data/run self test on your hard disk. 

Edit: Sorry, that's for the hdd.

---

### Post by cloyd on 2011-02-04
Does the disk utility give the _processor _temp, or the _hard drive_ temp?  On my machine, there is a considerable difference between disk utility temp and what is reported by sensors.

For anyone looking at this thread, it was started here:    [http://ubuntuforums.org/showthread.php?t=1680547&page=2]("http://ubuntuforums.org/showthread.php?t=1680547&page=2We")        
We moved it thinking we were hijacking someone else's thread. There is some more background here.

---

### Post by GrouchyGaijin on 2011-02-04
> **cloyd said:**
> Does the disk utility give the _processor _temp, or the _hard drive_ temp?  On my machine, there is a considerable difference between disk utility temp and what is reported by sensors.


Well, that is a good question.  I installed the sensors and the applet for them.  I thought the sensors were already installed since I went through the same list of probing questions when I set up sensors for Conky to use.

In any case, now when I look at the panel I have 5 sensors with different temps.

[IMG]http://www.jfniendorf.org/sensor-applet.png[/IMG]
[IMG]http://www.jfniendorf.org/sensor-prefs.png[/IMG]

I don't understand what the differences are between Temp 1 Core 0 and Core 1.  I thought that the cores were the CPUs.  There are two on this machine so OK I get that.  What does Temp 1 refer to?

Then again under i8k temp 1 is called CPU.

I don't know what acpi with the sub-heading THM means either.

Under i8k I see two boxes for fans.  Checking either or both adds an rpm number to the panel.  I thought based on the i8k monitor I installed earlier that there was only one fan on this system.

I'm pretty confused now.

---

### Post by cloyd on 2011-02-04
I'd sure welcome it if someone who really knows what they are talking about could jump in here. I really don't want to mislead anybody. 

We have different systems, and we get different readouts and different output for the same apt. 

Just to give you an idea, my Computer Temp Monitor  in the panel reads 50 c now.  If I hover the mouse over it, it displays THRM: 50 C.

sensors in terminal gives

Adapter: Virtual device
temp1:       +51.0°C  (crit = +100.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +45.0°C                                    
Core1 Temp:  -49.0°C       

and conky reads
thermal 0 ok: 50 C

My conky uses the terminal command acpi -t to get its display.

I suspect your cpu is at 70 .   I'm trusting (assuming) that temp1 and acpi both give the cpu temp. I have looked at core0 and core 1, and though on my system they can be slightly different from temp1, they are usually within a few degrees apart. 

Anybody else have any input? Think I may go to a reference book.

---

### Post by GrouchyGaijin on 2011-02-04
Hmmmm I'm still confused.  I have such a huge range of temps and I'm not sure what each one refers to.

I just tried to run acpi -t and had to install acpi.  Hmmmm

After I did I see:
```

Thermal 0: ok, 63.5 degrees C
```

Sensors returns this:

```

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +67.5°C  (crit = +87.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +82.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +84.0°C  (high = +100.0°C, crit = +100.0°C)  

```

Thanks for the help by the way I really do appreciate it.

---

### Post by djyoung4 on 2011-02-04
or you could try [conky]("http://conky.sourceforge.net/")
```
sudo apt-get install conky-all
```

---

### Post by cloyd on 2011-02-04
I don't know how much help I am now. However, I simply type "sensors" in the terminal. I get slightly diffrerent output, but usually close with "acpi -t". Don't type the quotes.  These readings have been close enough that I hadn't worried about the differences between them. 

If you get a "command not found" or the like from the "sensors" command, then try

sudo apt-get install sensors

However, if the command is not there, the terminal often gives a suggestion on how to get the command, and any suggestion that is different from mine will probably be better.

Just checked my reference books. They didn't do me much good. I've been looking at Ubuntu Community documentation. . . and haven't found anything that explains the 11 degree spread you are getting.

---

### Post by cloyd on 2011-02-04
I'm going away for a while . . . a few things I should do . . . I will check back.

---

### Post by GrouchyGaijin on 2011-02-04
> **djyoung4 said:**
> or you could try conky


Thanks.  That is how this started back on another thread.  I noticed that the temps displayed in my conky were much higher than what other people were reporting.

---

### Post by djyoung4 on 2011-02-04
o i see.  i kinda skipped over some of the responses and just posted
Maybe i can be of some help.  Are you asking what is the best way to differentiate between all the sensors you have because as far as I can tell you have 4 or 5 temp sensors and a 2 fan sensors.

---

### Post by JayKay3OOO on 2011-02-04
I looks to me like (from left to right in your pic)

Libsensors:

tmp1 - cpu (70 oc)
Core 0 - Core 0 (81 oc)
Core 1 - Core 1 (81 oc)

i8k:

temp 1 - cpu (69 oc)

acpi:

thm - cpu (70 oc)

So we can tell acpi and libsensors are giving the same readings for the cpu even though libsensors is not calling it cpu(i'm guess it is though). i8k may be more sensitive *shrugs*.

You could re-boot into the bios and see which cpu sensor is the closest to what the bios says because it should be given that info.

Duel fans could be just that there may be a second fan header and it's picking that up as a sensor but as you say, there may not be a fan plugged in at all. 

You often get this with speedfan in windows, it reads null values because there are sensors with nothing attached.

---

### Post by GrouchyGaijin on 2011-02-04
> **djyoung4 said:**
> o i see.  i kinda skipped over some of the responses and just posted
Maybe i can be of some help.  Are you asking what is the best way to differentiate between all the sensors you have because as far as I can tell you have 4 or 5 temp sensors and a 2 fan sensors.

Yes, actually that would be helpful.

[IMG]http://www.jfniendorf.org/sensor-prefs.png[/IMG]

I can match these preferences up with the sensor displayed in the shot below, but I don't understand what they actually mean.

[IMG]http://www.jfniendorf.org/sensor-applet.png[/IMG]

What does libsensors mean by temp 1 and how is that different from the temps of the cores?  I thought that the cores were the CPUs.  

Then i8k lists a temp 1 and calls it CPU, but there is only one of them.

I don't know what acpi Thermal means either.

If I run the sensors command in the terminal I get this:
```


acpitz-virtual-0
Adapter: Virtual device
temp1:       +65.5°C  (crit = +87.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +83.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +83.0°C  (high = +100.0°C, crit = +100.0°C)  

```

These numbers are different from the screen shot numbers because I took the screen shots earlier and I just ran the sensors command. 

Are the ** +65.5°C  (crit = +87.0°C)** and **(high = +100.0°C, crit = +100.0°C)** notices actual notices for my hardware or simply default notices that appear with any setup unless you manually change them?

---

### Post by pqwoerituytrueiwoq on 2011-02-04
in the applet they are set manually as to what is high/low
look up your processer/gpu/hdd on the net 
http:/www.google.com

---

### Post by JayKay3OOO on 2011-02-04
This might help.

(**A**dvanced **C**onfiguration and **P**ower **I**nterface)   A power management specification developed by Intel, Toshiba and  Microsoft that makes hardware status information available to the  operating system.

**Definition: ****i8kutils**:  Dell Inspiron and Latitude laptop  utilities This is a collection of utilities to control Dell Inspiron and  Latitude laptops. It includes programs to turn the fan on and off, to  read fan status, CPU temperature, BIOS version and to handle the volume  buttons and Fn-keys. The package includes also a small Tk applet,  designed to be swallowed in the gnome panel, which monitors the CPU  temperature and comtrols automatically the fans accordingly to user  defined thresholds. The programs require the kernel module i8k.o which  can be compiled from the package sources or found in Linux kernel 2.4.14  and later versions. The kernel module has been tested only on Inspiron  8000 laptops but it should work on any Inspiron and Latitude laptops.


If you have one cpu with a duel core processor then each core might give a temp reading. Although on my 965 quad core it does not.

---

### Post by cloyd on 2011-02-04
I'm not sure what you cpu temp is, but the 80's just sounds high. I'd really want to google my processor and find what its real desired operating temperatures are. If you don't know any details about your processor, in terminal type "lscpu" and you'll probably learn more than you really want to know.  Then google the processor by brand and model . . . and you'll probably find something there that helps.

I know processors are different, but everything I've seen says healthy temps are most often 30's (I suppose you couldn't get them much lower, even at idle) to 70's.  70's seem like high when under a load. All are different. My little AMD athlon lists 100 as critical. The processor on my larger machine (forgot what model at the moment) lists critical as in the 90's.  (It is a more powerful machine and in general runs cooler).  Someone, I'm not sure who --told me that a healthy temp didn't stay much over 75% of critical value for long periods of time.  

Working with cd's and dvd's has usually used quite a bit of cpu . . . and ran temps up a bit . . . that  and Flash video. 

Again, I am not an authority, just a user who likes his Ubuntu, trying to learn as I go along.

---

### Post by GrouchyGaijin on 2011-02-05
I get this information when I run the command.
```

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              13
CPU MHz:               1000.000
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K

```

It sounds stupid, but I'm not sure how to find the temp information in Google.  I've tried searching several different ways including going to Intel's website.  I keep getting hits for things other than what I'm looking for.  (I must not be searching correctly.)

---

### Post by cloyd on 2011-02-05
Well, I thought it would be easy, but as I tried, I found that definitely identifying the processor and going to a table was not as easy as it sounded. I've found tables with max temps listed, but . . . it has been pretty hard to identify your processor exactly, even after looking at the output form lscpu and then going to the dell page on your computer. The Dell page lists these Intel processors for your machine: Pentium t2310 or a core 2 t5250 or (Core 2 from here on) or t 54450 or t7250 or t7500. Then, I am not finding these models explicitly listed in the tables I've found, 

However
What I did see in searching is that _most_ intel processors designed for laptops have a max rated temp of 100 C. Other advice on pages I found said that they really should run at least 20 degrees cooler most of the time.  That pretty well matches what I was told . . . that they should run about 75% of the max temp most of the time . . . though he 20 degree figure allows it to be just a bit higher.

As yet, no one has told us why 65 to 83 reading and the differences between the two. My guess is that your processor is at 65 . . .  though I don't really know.



83 degrees C is hot. Here in the US, we are stuck in the dark ages with F scale, but I would think that 83 degrees would make for a very hot computer, or some very hot air coming out of the vents when the fan is on.

Right now, if no one can help us on this, I'd suggest contacting Dell. I don't know how good their customer service is now, especially under Ubuntu though I know they sell machine with Ubuntu. I had a Dell a few years ago, and they were generally helpful with my old Inspiron 2650 and Windows XP. I don't know what they are like now.

If anybody else has better advice, I'd sure like to hear it.

EDIT:  I just looked at something else . . .    [http://www.cpu-world.com/CPUs/Core_2/TYPE-Core%202%20Duo%20Mobile.html](http://www.cpu-world.com/CPUs/Core_2/TYPE-Core%202%20Duo%20Mobile.html)
2 other pages help confirm this.          [http://www.pantherproducts.co.uk/Articles/CPU/CPU%20Temperatures.shtml](http://www.pantherproducts.co.uk/Articles/CPU/CPU%20Temperatures.shtml)
and                                                  [http://techstroke.com/recommended-maximum-cpu-temperature-list-for-intel-and-amd-processors.html](http://techstroke.com/recommended-maximum-cpu-temperature-list-for-intel-and-amd-processors.html)
These seem to confirm that the critical temp is 100 C.


this definitely identifies your intel processor as classified as "moblie". So again, I think the case is max is 100 C.

---

### Post by GrouchyGaijin on 2011-02-05
@Cloyd - Thank you!  I really appreciate the help.

I logged into my Dell account and found that the processor is a 
T5250.

I have been unable to find anything about maximum / critical temperature for this chip.  I'll check the links you posted.

On the forum I did find one other guy with the same chip in a similar situation.  Except his machine has been shutting down on him because its too hot. [http://ubuntuforums.org/showthread.php?t=1243720](http://ubuntuforums.org/showthread.php?t=1243720). 

I still don't understand the difference between the libsensors temp 1 and the core temperatures.  However the libsensors temp 1 seems to be very close (could be updating at a different rate) to what I see from i8kmon.

---

### Post by BigZ1981 on 2013-04-21
I know this is an older thread, but I cam across it while looking for a temp sensor app to use for Ubuntu (I just installed LinuxMint, and forgot I switched over to it, but oh well...still experimenting with different flavors).  I can't even see these pics anymore, so I don't know everything that's going on with the screens & temps...
With temps being up in the 80's, I have to ask: are you overclocking, and if not, are you running your laptop under a load when measuring temps?  It's easy for your CPU to get into the 80s with a laptop because of the lack of proper airflow, everything close together generating heat, etc, and those vents can get dusty and blocked fast & easy.

As for the different temps, it sounds to me like they're using different sensors.  The last post with the results from just typing sensors in the terminal suggests to me that the other temp is a reading on the GPU core.

---

### Post by wildmanne39 on 2013-04-21
Thread closed. Please do not post in old threads.

---

