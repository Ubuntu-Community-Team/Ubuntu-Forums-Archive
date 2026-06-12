---
title: "Control CPU Fan"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by CJWW1989 on 2010-02-06
I've been looking for a solution to this but haven't found one. I'd like to control when/how fast my CPU fan runs. It constantly runs when it doesn't need to and honestly I don't want to pay 30 USD for someone to clean it. Can anyone help?

---

### Post by tgalati4 on 2010-02-06
apt-cache search tpfan

---

### Post by CJWW1989 on 2010-02-06
Okay, so how do I get this?

---

### Post by tgalati4 on 2010-02-06
In a terminal:


sudo apt-get install tpfan-admin tpfand tpfand-profiles

It works with thinkpad laptops.  Don't know what kind of laptop you have as you didn't tell us.

Try loading the following module and report what it says:

sudo modprobe thinkpad-acpi

---

### Post by wojox on 2010-02-06
Ave a look at this as well: [http://www.howtoforge.com/cpu_frequency_scaling_ubuntu](http://www.howtoforge.com/cpu_frequency_scaling_ubuntu)

---

### Post by l-x-l on 2010-02-06
I use I8kmon for my Dell. There's also Dellfand.

---

### Post by CJWW1989 on 2010-02-06
I don't have a thinkpad so it doesn't work. What does the CPU scaling do?

---

### Post by admiralspark on 2010-02-06
Well, CPU scaling controls what frequency your core runs at. For example:
I have a 2.0GHz Sempron single core. When it runs at the full 2.0GHz (even when not under load) it generates a lot of heat, enough so that my cpu fan is on half the time (awesome Compaq!). But, if I use CPUFreq (a cpu frequency scaling program), I can place the core in OnDemand mode, which allows it to run at 800MHz (or 40%) unless my computer needs higher speeds. Because it can then adjust itself, you'll never notice that it's slowing itself down, but you WILL notice the fan not being on as often.
HOWEVER!
That doesn't answer your question about fan control at all. I assume you're looking for a program like what Speedfan is for Windows?

---

### Post by CJWW1989 on 2010-02-07
> **admiralspark said:**
> 
That doesn't answer your question about fan control at all. I assume you're looking for a program like what Speedfan is for Windows?
Yes, something like that. It's just the thing runs constantly sometimes. Just when I have a browser open. If it matters, it usually runs high when exe is high, ie: when I close out exe (which may be using anywhere from 50 - 100% of the juice) the fan gets quiet.

---

### Post by Mark Phelps on 2010-02-07
> **CJWW1989 said:**
> Yes, something like that. It's just the thing runs constantly sometimes. Just when I have a browser open. If it matters, it usually runs high when exe is high, ie: when I close out exe (which may be using anywhere from 50 - 100% of the juice) the fan gets quiet.

This is what it is SUPPOSED to do!  Looks like you have a CPU that adjusts its cycles based on workload demand.  The faster it runs, the hotter it gets -- forcing the ran to run faster to keep it cool.

If you manually slow down the fan, you will burn out your CPU.

So, best thing to do is leave it alone.

---

### Post by CJWW1989 on 2010-02-08
> **Mark Phelps said:**
> This is what it is SUPPOSED to do!  Looks like you have a CPU that adjusts its cycles based on workload demand.  The faster it runs, the hotter it gets -- forcing the ran to run faster to keep it cool.

If you manually slow down the fan, you will burn out your CPU.

So, best thing to do is leave it alone.

That doesn't really help my cause. Maybe cutting down my workload would be better. But mine just runs hot too fast. I either need to clean it out or get a cooling fan. Oh well.

---

### Post by MrMacman2u on 2010-03-19
tgalati4, that 'tpfan' may be exactly what I am looking for.

I am unhappy... no, not unhappy... just mildly annoyed with the default fan control that Ubuntu has implemented since 7.10

My T42 Thinkpad system fan turns on about 5-15 minutes from a cold boot and it WILL NOT shut off until I shut down the system no matter how cool the system gets short of "extreme" temperatures (slapping the system in the FRIDGE will cool it to the point the fan will turn off)

Prior to 8.04, when the system was put under load or every 5-10 minutes if it was completely idle, at about 45C the fan would turn on and run, adjusting it's speed in relation to the load (and hence the thermal load) but when the system (the GPU was also factored in) cooled back down to about 40C (I think lol) the fan would SHUT OFF and hence be silent for another few minutes.

I want this behavior back.

Since 8.04, all the way up to my current install of 9.10, once it turns on, my Thinkpad's fan simply will not shut off unless the system is ABSURDLY cool (<35C).

I have been casually looking for weeks for something that would allow me to change the "default" behavior of the Ubuntu ACPI (ibm-acpi) subsystems that controls the fan so I can change how Ubuntu operates the fan so I could tell it to turn off the fan at a certain point (say 40C).

I'm not looking to manually control it (I already know how to do that) or for separate fan control scripts per-se, I'm looking to modify how the fan is controlled (on/off trip points, speed increase temps, etc...) at the system/OS level, which the tpfan program appears to possibly offer. 

I would love to try the tpfan program and did a search via apt-get and had zero results returned. Is there something special I need to do in order use the package manager to install this program?

Just to set minds at ease; I'm well versed in computer hardware, my Thinkpad is in tip top shape and is 100% dust free, I know the thermal operational ranges and limits of all the major heat producing components of my laptop and I have and use temperature monitoring utilities. In short, I'm not going to fry anything due to my own incompetence ;)

I'm just looking for a quieter user experience that I had once before.

When my Thinkpad is idle and the HD is spun down, I would love to hear blissful silence once again!

I appreciate any help in advance! Cheers!

---

### Post by proxess on 2010-03-19
Check your bios, see where the thermal limits are. If it's not in your bios, it's somewhere in your sensors anyway.

---

### Post by kleskjr on 2010-03-19
there is a default program in Ubuntu- cpu scaling monitor. you can add it in your panel with right click

---

### Post by 3rdalbum on 2010-03-19
Ubuntu does not have ONE SINGLE LINE OF CODE for doing anything with your fan.

Your BIOS controls your fan speed, and it controls it better than any human can.

Or, if you have fan speed control turned off in your BIOS, then there will be no control and the fan will run flat-out.

If there are any changes in fan behaviour between distributions, it's the result of programs putting load (or not putting load) on your CPU. If the fan is running fast, check whether any of your programs are pushing the CPU. If they're not, then you might need to reapply thermal interface paste to your CPU, or clean out your CPU fan and cooler.

I'd recommend getting rid of the problem completely by buying a Noctua CPU cooler - they are so quiet you can run them 'uncontrolled' (at full speed) and they'll still be quieter and cooler than the Intel or AMD stock coolers.

---

### Post by MrMacman2u on 2010-03-19
To kick things off, thanks to those that replied, I really DO appreciate the effort you took to provide some great answers.

However, I am afraid I must do a "point-counterpoint" now ;)

proxess, I know precisely what you are talking about, however, the T42 Thinkpad BIOS does not list thermal limits, nor does it provide any form of "sensor monitor" in the BIOS configuration that many modern BIOS/motherboard combinations provide. I'd be delighted if it did, this would be an absolute non-issue and I'd have configured a more preferable fan behavior model quite some time ago.

kleskjr, I do love the CPU scaling monitor, it's been the first thing I add to my gnome panel since I installed Ubuntu for the very first time :) It is wonderful for monitoring how fast my CPU is currently running at, locking it at a set frequency, and even changing the frequency scaling aggressiveness. Unfortunately, I don't see what it would have to do with fan control outside of locking the CPU at a lower frequency or setting it to a more conservative scaling method. Which WOULD reduce the heat output of the CPU, however, as I stated in my original post, the fan will not shut down until the cpu reaches about 32C... positively frigid as far as CPU temps go.

3rdalbum, excellent reply! And while your assertation that Ubuntu does not have one line of code to control the CPU fan may be true for desktops and the majority of laptops, there IS a fairly extensive control system for a Thinkpad's fans in "ibm-acpi". These abilities have recently been rolled into new kernel releases and provide the ability to override the Thinkpad's internal thermal control systems to a limited extent. I'm simply looking for some way to exploit these features.

The rest of your advice was solid,  cpu load, dirty coolers, failed/ineffective thermal paste or insufficient coolers CAN cause a racing cpu fan and replacing a stock cooler with something beefier and quieter is usually the easiest solution... for a desktop. I have a laptop ;) Also, I'm a certified IBM laptop (and desktop/workstation) technician and this Thinkpad is meticulously cared for and cleaned, internally and externally. In fact, I practically coddle it. It's my baby, what can I say? Thinkpads rock my socks!

Regardless, thanks all for your time and effort, but it appears my "issue" is deeper seated than I initially believed. 

I delved deeper into HOW Thinkpads operate last night and got some interesting answers.

Ironically, the BIOS does not actually control the fan for the T42 unlike 99.9% of other cpu fans, instead the embedded controller does. It CAN be overridden to a certain point (it will kick on the fan at a critical temperature (85C or 90C for the GPU) regardless) but rarely is.

Lo, I dug into my firmware update records and surely enough, I had updated the embedded controller the SAME day I updated to 8.04. Checking into Lenovo's embedded controller's change log, I found a minor reference that stated: "Updated fan control behavior to resolve high speed pulsing issue"... Looking into THAT, it turns out that many people were annoyed with the fan behavior I PREFERRED!

I guess a fan's constant, unrelenting, unending droning is better than short low speed bursts of noise to some(most?) people....

So all that is left is the possibility of using the software control method offered by "tpfan", however thus far I have been unable to locate the exact package that tgalati4 mentioned. Any idea's?

Again, thanks for those who replied, I do greatly appreciate your efforts!

---

### Post by razorseal on 2010-03-19
That's pure bs about the BIOS controlling the CPU only, and OS has nothing to do with it.... if that's thse case how is my CPU fan at full speed running at 800mhz right now (full is 1.8) when in Windows 7 it doesn't act this way at all?

---

### Post by razorseal on 2010-03-19
I just downloaded toshiba utilities.... where the hell is it? I can't find it lol

---

### Post by QIII on 2010-03-19
Toshiba, for some inexplicable reason, does use OS to control fan speed, which can be a problem in OSes other than Windows.

Toshiba defers fan control to Windows.

---

### Post by no2498 on 2010-03-19
im on a desk top dell 6400 910 karmic
all i had to do was
open a terminal type, gstreamer-properties click enter
click video set the plugin to, x window system (no xv)
write  what its set to first so you can set it back if it does not work for you
i did have to restart the computer
but just turning on the computer was running hot fan was 100 mph
hope this helps

---

### Post by MrMacman2u on 2010-03-23
I dug through a few of my older laptops and booted 3 different toshiba's from a Ubuntu LiveCD, sure enough they exhibited the same symptoms other toshiba owners were describing under linux, but not windows... 

There does seem to be an "emergency override" though at extremely high temperatures fortunately.

Strange....

Oh well. I guess this is another reason I no longer like Toshiba's ;)

no2498, gstreamer settings are not the issue and have been tweaked to take advantage of the video processor on this machine even though this laptop very rarely used for viewing/listening to media. Thanks for the suggestion however!

A bit of dinkering around on my part and building off the fan control scripts that other Thinkpad owners have written, I've definitely improved on how my laptop's fan is controlled. It averages a few degree's warmer now, but it's soooooo much quieter when it's idle!

Oh, and no, the higher temps are not an issue, I'm more than 30C from even being NEAR any danger zone... (~80C) besides, the embedded controller overrides software at around 45C for the cpu and 50C for the gpu.

So I suppose I built my own answer lol!

---

