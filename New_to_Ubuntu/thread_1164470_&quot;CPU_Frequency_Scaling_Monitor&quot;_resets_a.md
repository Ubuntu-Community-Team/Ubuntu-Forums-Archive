---
title: "&quot;CPU Frequency Scaling Monitor&quot; resets at boot"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by zcacogp on 2009-05-19
Chaps, 

Some of you will have read my "Ubuntu - very slow" thread, and thanks for your answers on there. 

It turned out that the reason the machine was so slow was because the CPU speed was throttled back to 1.0Gig (it's a 2 x 2.9Gig processor), and I only found this out by playing around with entries on the toolbar at the top and finding the "CPU Frequency Scaling Monitor". 

While this allows me to set the CPU speed to whatever I like, it always resets to "On Demand" whenever the machine reboots, which doesn't actually work - it just makes the CPU's run at 34% almost all the time. Setting this back to "Performance" is not a problem, but it's a pain to have to do it each time you boot the machine. 

How can I set this so that it stays on "Performance" all the time? 

Thanks, in advance, for any help. 


Oli.

---

### Post by oOarthurOo on 2009-05-19
While looking through sysyconfig the other day I noticed a service called 'ondemand', perhaps disabling that service will help.

```
sudo apt-get install sysvconfig
sudo sysvconfig
```

You have to finish and save changes before quitting. Be careful with the tool, and remember if you break the machine you get to keep both parts.

---

### Post by zcacogp on 2009-05-20
oOarthurOo, 

Thanks ... just done as suggested. I'll see what happens next time I reboot ... 


Oli.

---

### Post by mcduck on 2009-05-20
Using the OnDemand governor is not going to slow your system down at all. it simply means that the CPU frequency will be throttled when you don't need much CPU performance, but as soon as running on higher frequency would help the speed should jump to full speed. 

This happens so quickly that the performance impact of having to wait for some fraction of a second before the CPU changes to full speed is meaningless. (this fact also makes any other power governor than OnDemand pretty much pointless on modern CPU's apart from some special cases).

In other words, OnDemand should give you exactly the same performance as running always at max frequency would. Although with less heat & noise and longer battery life when you don't need the full speed.

---

### Post by zcacogp on 2009-05-20
mcduck, 

Yes, I agree with all that you say, but it simply doesn't work ... if the setting is "On demand" then the CPU speed never moves up from 34% and the machine is correspondingly sluggish. (I have read elsewhere that this is a known bug.)

The point about less heat and power consumption is a smidge less relevant as the machine in question is a desktop; had it been on a laptop it would be key. 


Oli.

---

### Post by mcduck on 2009-05-20
> **zcacogp said:**
> mcduck, 

Yes, I agree with all that you say, but it simply doesn't work ... if the setting is "On demand" then the CPU speed never moves up from 34% and the machine is correspondingly sluggish. (I have read elsewhere that this is a known bug.)

The point about less heat and power consumption is a smidge less relevant as the machine in question is a desktop; had it been on a laptop it would be key. 


Oli.

Do you mean that when you start an app that really does use all the CPU power it can get (as in CPU usage jumping to 100%) the frequency still doesn't change?

In that case you indeed have some problem with CPU scaling, although such problem should also mean that none of the other governors would work either. If that's the case I recommend just trying to find out what's the problem with frequency scaling not working correctly, and fixing that.. ;)

---

### Post by zcacogp on 2009-05-20
mcduck, 

Good question - I hadn't actually tested it. 

Having now done so, if the setting is "On demand", and I run a number of applications (screensaver, help-for-screensaver, open the OpenOffice word processor etc all at the same time), the CPU usage can get up to 100% and a good second or so later, the CPU performance moves up to 62% and then 78% and then 100%, but it is very slow to react. This doesn't feel like it is as it should be; as you said "This happens so quickly that the performance impact of having to wait for some fraction of a second before the CPU changes to full speed is meaningless" (from your post, but as I would hope it should be.) 

My original concern arose from the fact that if the setting is "On Demand", the system is much more sluggish to respond to inputs, even while the processor usage is low (<50%). By 'sluggish', I mean that the response to buttons (such as the "Quick Reply" button on this forum) is slow, the response to pressing keys can be slow, the action when a window is minimised or maximised is slow. If the Setting is "Performance", the machine feels a LOT crisper to use, despite the CPU usage not being that high. 

Did that make sense? 


Oli.

---

### Post by mcduck on 2009-05-20
Yes, that makes sense (at least kind of..). Clearly the frequency scaling does work, but not correctly, as it shouldn't be slow. OnDemand should give immediate switching between lowest/highest available speed.

It's also strange that the low speed causes sluggishness in the user interface, as none of the things you mentioned are in any way CPU intensive tasks, and should react quickly even on lowest available CPU frequencies (really, my laptop runs at 996MHz most of the time and everything is just as snappy as it would be on full speed). Perhaps your haven't got the correct graphics drivers installed and the system uses CPU for graphics rendering as well? That could explain the low CPU frequency resulting in sluggish user interface..

---

### Post by zcacogp on 2009-05-20
mcduck, 

I know that I don't have an ideal graphics set-up. When I first installed Ubuntu on this machine it ran like a dog. The problem was eventually narrowed down to the graphics card I have (AMD/ATI, on-board, on a gigabyte motherboard). Various things made little improvements; re-flashing the BIOS, turning off compiz, updating to 9.04 JJ (I was on 8.10 II), but the really big improvement came when I discovered the Frequency Scaling Monitor app that lives on the top pane, and moved the performance up to "Performance". That made the machine run crisply - as crisply as it ran XP, at least - and I was at last happy with Ubuntu (yes, I am a beginner as you will have already realised!)

I am hoping for some better graphics drivers to appear in the future - I am told that ATI are making their driver code available so there should be improvements to come. 

I agree - it sounds like the frequency scaling isn't working as it should, as it shouldn't respond so slowly. (I didn't realise it responded at all until you suggested I should test it, so thanks!) 

Thanks for your help. I've yet to reboot to see what happens to the aforementioned setting, after the suggestion from oOarthurOo. 


Oli.

---

### Post by mcduck on 2009-05-20
> **zcacogp said:**
> mcduck, 

I know that I don't have an ideal graphics set-up. When I first installed Ubuntu on this machine it ran like a dog. The problem was eventually narrowed down to the graphics card I have (AMD/ATI, on-board, on a gigabyte motherboard). Various things made little improvements; re-flashing the BIOS, turning off compiz, updating to 9.04 JJ (I was on 8.10 II), but the really big improvement came when I discovered the Frequency Scaling Monitor app that lives on the top pane, and moved the performance up to "Performance". That made the machine run crisply - as crisply as it ran XP, at least - and I was at last happy with Ubuntu (yes, I am a beginner as you will have already realised!)

I am hoping for some better graphics drivers to appear in the future - I am told that ATI are making their driver code available so there should be improvements to come. 

I agree - it sounds like the frequency scaling isn't working as it should, as it shouldn't respond so slowly. (I didn't realise it responded at all until you suggested I should test it, so thanks!) 

Thanks for your help. I've yet to reboot to see what happens to the aforementioned setting, after the suggestion from oOarthurOo. 


Oli.
Graphics cards can be a bit tricky on Linux. Sadly. (on the other hand Linux drivers can sometimes be even better than Windows ones, at least in some things. My laptop's graphics drivers have always had problems with suspending the computer, with Ati's Windows drivers it only wakes up about 90% of the time. Latest open-source Linux drivers however don't have that problem..)

Anyway, if you can't find out what's the problem with scaling not working correctly then disabling the scaling completely should at least remove the symptoms, even though it doesn't solve the actual problem. At least that's something and better than sluggish system, I agree on that one.. :)

If you just want to get rid of the scaling you might have option for that in BIOS.

From system services, AMD CPUs should use powernowd for frequency scaling, while Intel/Via CPUs use cpufrequtils/cpufreqd. (this might have changed in 9.04, last time I played with CPU frequency settings was with 8.10). Anyway, if you don't have the setting in BIOS then disabling those services should do the trick as well.

---

### Post by zcacogp on 2009-05-20
OK, the changes suggested earlier on haven't made the CPU speed persistent over a re-boot ... I'll try tinkering with the BIOS as suggested; thanks mcduck. 


Oli.

---

### Post by oOarthurOo on 2009-05-20
Let's try a few things in the terminal:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```
Should spit out what governors are available to you to use. If it doesn't show something like:
> conservative ondemand userspace powersave performance 
Then we've got problems. Assuming it's ok, let's try:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```
which should give something like:
> 1600000 1333000 1067000 800000
If you just see one number, big problems. More than one is ok. Now do:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
This should tell you your current governor. Mine is ondemand. We can check the current speed by doing this:
```
cat /proc/cpuinfo | grep M
```
For me it spits out
> cpu MHz		: 800.000
cpu MHz		: 800.000
If I do it a few times, chances are one of them might be 1600 (max), because something is taxing the cpu. This is because it shows you the current speed. Now we try changing it to performance (assuming you saw it in available governors in the step above):
```
echo performance | sudo tee -a /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
```
You'll have to reproduce the line for each processor you have. I have two, so I have to repeat it for each, cpu0 and cpu1. This should give you their names and let modify my commands to reflect your situation:
```
cd /sys/devices/system/cpu && ls
```
Now check the current performance, and cpu speed:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /proc/cpuinfo | grep M
```
Assuming everything has gone well so far, the surest way to fix this, it's a bit hackish, but it should work, is if you add those two commands to /etc/rc.local, but since that commands in that file should be run as root (not via sudo) the easiest way would be with this command:
```
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
Just open the file /etc/rc.local and add the commands in there, again making sure to add one for each processor you have and using the correct names.

Truthfully, I've taken all this from my debian experience. I'm not too sure where Ubuntu is providing the ondemand info to the system. There should be a more elegant way to achieve this, but hopefully this does the trick until someone a little more Ubuntufied chimes in.

---

### Post by zcacogp on 2009-05-26
oOArthurOo, 

Thanks for that detailed post. It was helpful. Everything was as you said it would be (although I'm not sure that I followed everything you said 100%).

However, I didn't manage to put those two new lines into rc.local at the end 'cos when I did so (I opened the file from the gui as I don't know the command to open a file from the terminal) it wouldn't let me save the changes to the file as I didn't have permission. (It wouldn't let me save anything into that folder for the same reason.) 

Typing this has probably revealed exactly how much of a beginner I am here, but how do I save the changes to the file? 

Thanks again. 'Twas a helpful post, and I am probably now just an ace away from solving the problem. 


Oli.

---

### Post by oOarthurOo on 2009-05-26
This will open up the file in way that let's you add the lines.
```
gksudo gedit /etc/rc.local
```
Put them just above exit 0. Save, restart, then use the commands I gave above to check the current governor. 

The reason I say this is a bit hackish, is /etc/rc.local is run once at boot. If you switch users, or suspend / resume, it may default back to ondemand. If that's the case, we'll have to try one or two other hacks, or find out how to do it properly. :)

---

### Post by zcacogp on 2009-05-28
oOArthurOo, 

Success! 

Did as you suggested, rebooted, and all is well. Performance is at 100% all the time! 

I'm chuffed. Thanks. My only slight regret is that I didn't understand what I did, and am realising how long the path of learning Ubuntu is. >Gulp<

Thanks again. 


Oli.

---

### Post by oOarthurOo on 2009-05-28
The command 'cat', just means spit out the contents of the file you name. If you did cat /home/readme.txt, it would print that files contents in the terminal. 

We did 'cat' to read the contents of some files in the /sys directory, which is where Ubuntu stores information about your hardware. We also did 'cat' on some files in the /proc directory, which is where Ubuntu stores information about the system as it is currently running. The handy-dandy system information tool you can find in the gui, for examples, is just reading files in /proc, and when you setup a new printer, for example, it looks for information on attached printers in /sys

As for the sudo / gksudo, that goes to the way that Ubuntu handles security. As a normal user you aren't allowed to mess with the system at all, so you have to becomes a super user to do stuff. Think of sudo as "super user do". Sudo is best for the terminal though, stuff like sudo cat filename. If you want to work with gui programs as the super user it's a better idea to user gksudo, and you can think of that as... uhh... gui krap super user do. 

Glad that worked out for you. Keep an eye on it for a while to make sure those corner case problems I mentioned don't arise. And keep trouble-shooting your problems, you'll be a masterbunter in no time. Though, there's always more to learn. I've got a few questions open on the forums myself :)

---

### Post by zcacogp on 2009-05-28
oOarthurOo, 

Thanks for the explanation. I had worked out that sudo was something to do with permissions, but was vexed by gksudo. And didn't know cat at all. 

I guess the answer is to carry on looking at these forums, and carry on trying things. (Snag is my last "trying thing" escapade has just ruined my lappie! I've just started a thread on here about that particular *faux pas *... ) 

Thanks again. 


Oli.

---

### Post by zcacogp on 2009-07-26
OK, dragging this one back from beyond the grave ... the problem has re-appeared. With a story attached. 

The machine I tried this on worked fine, as described in the post. 

I trashed it, and rebuilt it. (Tried to upgrade the kernel, it didn't work. I rebuilt it.) I re-applied the fix described in this thread to the re-built machine and it ran at "Performance" on the Frequency Scaling Monitor every time it booted. Everyone was happy .... :D

I put the new kernel on the rebuilt machine, and then upgraded the screen driver. This caused it to break, again. But this time, I realised what was happening and removed the screen driver, downgraded the kernel and then re-installed the screen driver. 

It works. BUT the Frequency Scaling Monitor *doesn't* stay at "performance" whenever it boots any more. It feels as if it is set at "performance" but is pushed back to "Ondemand" a few seconds after it has booted, as the monitor says "2.90Ghz" for a good few seconds, but then goes back to "1.0Ghz". Almost as if there is some other script somewhere that is over-riding the additions made to the rc.local file. (And, yes, I have checked - those lines are still in the rc.local file.) 

So ... any ideas? Ideas as to a) Why the change has occured and b) how to solve it? I guess some kind of idea as to what happens when it boots so that I can see what is being done and chase the problem would help. Is it possible to boot in such a way as to display this? I am also aware that I don't actually know what *happens *when Ubuntu boots, and where the rc.local file fits in to everything. 

All suggestions welcome, and gratefully recieved. 


Oli.

---

### Post by ProDigit on 2010-04-22
Quick note,
The CPU frequency scaler works very well on Ubuntu 10.4.
I don't know why they have added the conservative though, because it's always better to run the CPU at the lowest speed unless a task requires CPU horsepower, then it is best to get the full CPU horse power.
That's why I think the conservative setting is pretty useless.
I use ondemand all times, as it is the best setting,
however,
everytime I reboot, the system sets the CPU to 'performance'.
Is there a way to set it permanently to 'ondemand'? Or perhaps a setting that will automatically set the scaler to ondemand after boot?

---

### Post by mbsnr on 2010-08-29
I just followed the logic for performance as in the thread above but put this in /etc/rc.local for ondemand instead at boot. Not sure why ondemand *isn't* the default anyhow - especially for battery based devices like my netbook.

```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

---

### Post by sergioadh on 2010-09-22
I still have this problem, I just want to set the CPU Frequency Scaling Monitor to Performance everytime I boot. How can this be accomplished? I'm using ubuntu 10.04 and CPU Frequency Scaling Monitor 2.30.0

Thanks

---

### Post by melbo on 2010-09-25
```
sudo nautilus
```

enter password

go into /etc/init.d/ and delete or move the ondemand file

then in terminal type:
```
sudo apt-get install sysfsutils
```

once installed, type in terminal:
```
sudo gedit /etc/sysfs.conf
```

and add this line:
```
devices/system/cpu/cpu0/cpufreq/scaling_governor = performance
```
save, close and reboot

Skip the delete 'ondemand' step and replace 'performance' with ondemand in the sysfs.conf if you are having the reverse problem of always starting in performance yet you want ondemand.

Solution originally found here: [http://forum.eeebuntu.org/viewtopic.php?f=45&t=3071&start=0](http://forum.eeebuntu.org/viewtopic.php?f=45&t=3071&start=0)

---

