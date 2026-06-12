---
title: "Ubuntu makes computer loud + hot"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by biggiemokey on 2009-01-26
I have a dual boot of Ubuntu 8.10 and XP.  After using Ubuntu, I realized that after restarting a few times, Ubuntu makes my computer louder and makes it blow out more hot air.  I have done 3 fresh installs since to fix the problem - which it does, until about the third time I turn on Ubuntu.  So today it happened again.  I am going to list what I did:

Reformatted /root, left /home as it is.  Computer was fine.
Downloaded Proprietary ATI driver
Installed Kubuntu (kubuntu-desktop)
Turned it back on today, and after it loaded it was perfectly quiet.  After about a minute though, the fan started getting loud.  System Monitor shows that my combined CPU use (I have Hyperthreading, 2 virtual CPUs) is not exceeding 7% at any given time, usually around 3%.  The only running program is Gnome-System-Monitor, everything else is sleeping and using 0% CPU.

I really can't deal with the noise and heat - please someone help me out.  This has been pretty frustrating, and I really want to use Ubuntu/Kubuntu, I had planned on keeping XP for when I absolutely need it.  But now I am always using XP because of this problem.  I do not know what kind of information to post to help, but any help would be greatly appreciated.  I would really like to get this fixed.

---

### Post by blueridgedog on 2009-01-26
You can try turnning off desktop effects:

System -> Preferences -> Appearance -> Visual Effects set to "None".

---

### Post by biggiemokey on 2009-01-26
That doesn't seem to make any difference :(

---

### Post by biggiemokey on 2009-01-27
*bump* I would really appreciate help with this if anyone has information/tips

---

### Post by stchman on 2009-01-27
> **biggiemokey said:**
> I have a dual boot of Ubuntu 8.10 and XP.  After using Ubuntu, I realized that after restarting a few times, Ubuntu makes my computer louder and makes it blow out more hot air.  I have done 3 fresh installs since to fix the problem - which it does, until about the third time I turn on Ubuntu.  So today it happened again.  I am going to list what I did:

Reformatted /root, left /home as it is.  Computer was fine.
Downloaded Proprietary ATI driver
Installed Kubuntu (kubuntu-desktop)
Turned it back on today, and after it loaded it was perfectly quiet.  After about a minute though, the fan started getting loud.  System Monitor shows that my combined CPU use (I have Hyperthreading, 2 virtual CPUs) is not exceeding 7% at any given time, usually around 3%.  The only running program is Gnome-System-Monitor, everything else is sleeping and using 0% CPU.

I really can't deal with the noise and heat - please someone help me out.  This has been pretty frustrating, and I really want to use Ubuntu/Kubuntu, I had planned on keeping XP for when I absolutely need it.  But now I am always using XP because of this problem.  I do not know what kind of information to post to help, but any help would be greatly appreciated.  I would really like to get this fixed.

Is this a laptop or desktop?  What make/model?

Thanks.

---

### Post by biggiemokey on 2009-01-27
It's a desktop, Dell XPS Gen 3 I believe.  Pentium 4 2.6 GHz with (Extreme) Hyper-Threading Technology, 2.00 GB RAM.  Video card is ATI Radeon X800 XT.  Thank you for the interest, hope this information helps shed some light on the problem.

---

### Post by biggiemokey on 2009-01-28
I have some more information that might help - Kubuntu has the same problem, although the fan was less loud at first.  After some Firefox browsing it got louder and then semi-quiet in intervals, not constantly loud like in Ubuntu.  After a while, though, it just got plain loud.

---

### Post by FAMUgolfer on 2009-01-28
I also have this issue on an Acer 4530 laptop, nvidia 9100m, and i'm also dual booting XP and 8.10.  My CPU usage is way low, below 10% yet my core temperature is always between 60-70C even when no programs are running. This issue is not resolved when I turn off desktop effects, screenlets, or cairo-dock.  The fan just stays on and my back panel is extremely hot!!

We need a solution!!!! Thank You!!!

---

### Post by Ben Page on 2009-01-28
I believe this could be cool'n'quiet issue (or equivalent for Intel). Are you doing something, or running some apps in background when its loud? Try adding the CPU scaling applet to your taskbar to see on what freq your CPU is running in. Ubuntu has something thats called powernowd (its giving me a headeake too), that scales your CPU freq according to OS needs, maybe its stuck, or not scaling properly, thus its holding your freq at max all the time, so your CPU is generating more heat, so it needs to be cooled more (increasing fan speed lowers the CPU temp).

---

### Post by sproaty on 2009-01-28
I've experienced the same, on Windows XP which I've minimised running services etc, it runs cooler than Ubunutu. lm-sensors on Ubunutu reports higher temperatures than Smartguardian did on XP

---

### Post by Kellemora on 2009-01-28
Hi BM

Since you brought this up, I thought I would chime in also.

I installed Ubuntu on one of my older machines just to test things on before I used them on the rest of the machines.

Ever since I installed Ubuntu on that machine, it will overheat to the point it just flat out turns itself off.  It has no sensors or things on it to check things and I just figured the computer was going bad on me.

I had an XP machines completely die on me, so took this older machine and loaded XP back onto it, it ran fine, no problems, in fact running a program continuously it hasn't died again since.
It was set up as dual boot, so when I needed to try something out I rebooted into Ubuntu and sure enough 2 hours later it died again and it was doing nothing, just on an idle.

So I began playing with it again, rebooted into XP after it cooled back down and it ran three days before I rebooted back to Ubuntu again.  Same thing, takes about two hours and it just shuts off.  If I run something like Firefox on it, it will shut down in under an hour, hotter than blue blazes.

But it doesn't seem to affect any of my other computers at all, in fact the HP machine runs cooler with Ubuntu than with XP running.

But your heads up sorta let me know it wasn't the computer, since it works on XP just fine, so I'll just leave that one that way and take another machine to use for my Ubuntu experiments.

TTUL
Gary

---

### Post by blueridgedog on 2009-01-28
> **Kellemora said:**
> 

Ever since I installed Ubuntu on that machine, it will overheat to the point it just flat out turns itself off.  It has no sensors or things on it to check things and I just figured the computer was going bad on me.



Have you tried turning off the CPU frequency Manager and manually setting the frequency as mentioned earlier in this thread?

---

### Post by biggiemokey on 2009-01-29
@ Ben Page:  I am assuming that the CPU Frequency Scaling Monitor applet that can be added to the panels is what you're talking about.  When I tried to add it I got the error message:
> You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.
I also tried this, thinking it might help:
```
sudo apt-get install lm-sensors
sudo sensors-detect
```
doesn't find any sensors.
```
Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
http://www.lm-sensors.org/wiki/FAQ/Chapter3 for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```
I have a Dell XPS (Gen 3?) desktop and I do not think Dell includes heat sensors on desktops.

@ Kellemora:  So you're saying that my computer might just not like Ubuntu?  Ugh.

Thanks everyone for the help, I really appreciate it because this is the one major thing that's keeping me from switching almost completely to Ubuntu.  And to other people who have this problem I feel your pain.  If I did something wrong, as in the information that I put up in this post, please bear with me as I'm not experienced with Linux.

---

### Post by biggiemokey on 2009-01-31
This seems kind of interesting...I downloaded GKrellM (system monitor) to see if that would give me any insight into my problem.  CPU0 and CPU1 (I have Hyperthreading, 2 virtual CPU) flickered between 0% and 1%.  However, "Procs" said 210 Processes (Running I'm assuming) and 1 user.  In Gnome System Monitor, there were about 43 processes listed, all of which were sleeping (including GKrellM - is that normal?) except for the System Monitor itself.  Does this mean things are running in the background that I don't know about?

---

### Post by Ben Page on 2009-01-31
biggiemonkey, are you sure that you did not disable "speed step" in bios, or done any configuration of CPU related features in bios? This message means, just what it says, you don't have support for scailing, or you miss configured the machine...Reconfigure your bios (if you know what are you doing, or just set the optimized defaults). "Sleeping" processes are normal. Download sysinfo tool, and try reinstalling powernowd(if the bios configuration doesen't help).

Also, I did some search, it is posible that you don't have speed step at all, but it is supported, although, you have to add it manually, check this thread for info about adding speedstep module to pentium 4>
[http://ubuntuforums.org/archive/index.php/t-190921.html](http://ubuntuforums.org/archive/index.php/t-190921.html)

---

### Post by Gotaro on 2009-01-31
I don't know about the rest of you, but my CPU temps are normal and I don't notice the CPU fan noise.  However, my video card is BLARING and pouring out hot air.  Maybe you guys are having heating problems because your video cards are dumping the hot air and making your case temps go way up?

For me, I'm pretty sure I can confirm that it isn't just a fan issue; The GPU is just plain getting HOT.  In Windows or BIOS, I don't even hear the GPU fan.  As SOON as Ubuntu starts up?  Train horn..  I can seriously hear it from my bathroom with the door shut lol.  I am SURE I'm shortening the life of my video card by using Ubuntu..  It's an old card, though, so I guess I don't mind the sacrifice..

Also:
GFX: Sapphire Radeon x800 XL
Driver: 8.552-0ubuntu0.1

---

### Post by biggiemokey on 2009-02-01
@ Ben Page - thank you for this information, it sounds promising, although I have not changed my BIOS in any major way.  I have not seen an option for "speed step", so maybe adding it will fix this problem.  The only thing that seems weird is that when I first installed Ubuntu, and when I first start it up even now, the fan isn't loud.  That leads me to think it's more of an Ubuntu problem and less of my BIOS.  But I will try it out, thank you for the link.

@ Gotaro - thanks for the info, but disabling video effects does not help me.  But yes, in BIOS and Windows, my computer is near silent.  I will try disabling the video drivers to see if that improves my situation.

---

### Post by Gotaro on 2009-02-01
> **biggiemokey said:**
> @ Gotaro - thanks for the info, but disabling video effects does not help me.  But yes, in BIOS and Windows, my computer is near silent.  I will try disabling the video drivers to see if that improves my situation.
Disabling video effects doesn't help me, either.  What I meant was that *anything* in Ubuntu makes my GPU very hot, even in normal, idle situations.  I *shouldn't* be stressing my video card, so I think either Ubuntu or the drivers are poorly written.  In the beginning, if I went into window switching mode, sometimes the GPU temp would drop and the fan would slow down..  Most of the time that doesn't work.  Turning off the display doesn't lower GPU fan speed, and neither does turning on any screensaver, and neither does logging out and letting the PC sit at the login screen.

---

### Post by biggiemokey on 2009-02-01
Deactivating the video driver made my computer quieter - but not quiet.  That seems weird, because since Ubuntu is quiet at startup, I figured it wasn't a video problem.  p4_clockwhatever didn't seem to help - I downloaded cpufreqd to try and change stuff but I can't find it - does anyone know the location (As in System>Preferences>...)?  I edited modules to make p4 start up when Ubuntu starts up, but I don't know if that's all I'm supposed to do.  Again, it didn't seem to make a difference.  I just reactivated video drivers and I'll see how it goes tomorrow after a restart.

---

### Post by kansasnoob on 2009-02-01
Flash 10 in Linux just works the piss out of a cpu!

Install flashblock 1.5.7.1!

---

### Post by biggiemokey on 2009-02-03
I do have Flashblock installed, so I don't think that is the problem, but thank you for the suggestion.

Can anyone tell me how to use powernowd/cpufreqd to try and solve my problem?  I have cpufreqd installed but I can't even figure out where it is to open it, forget using it properly.  Help is greatly appreciated.

---

### Post by biggiemokey on 2009-02-04
*bump* please help

---

### Post by boof1988 on 2009-02-04
> **biggiemokey said:**
> *bump* please help

Don't know if it'll help any... But here's a link to a ["How To"](http://ubuntuforums.org/showthread.php?t=394911) and also (if you haven't tried it yet) maybe try:

```
man cpufreqd
```

I haven't used any of this yet so I can't really add any more ideas.  Hope this helps a little.

---

### Post by biggiemokey on 2009-02-05
Thank you, I checked google for a good guide but didn't find anything that was detailed or easy to understand.  I appreciate the help.

---

### Post by biggiemokey on 2009-02-08
well, I was able to do Steps 1, 2, and 5.
```
neal@neal-XPS:~$ cat /proc/cpuinfo                             
processor       : 0                                            
vendor_id       : GenuineIntel                                 
cpu family      : 15                                           
model           : 3                                            
model name      : Intel(R) Pentium(R) 4 CPU 3.60GHz            
stepping        : 4                                            
cpu MHz         : 3600.000                                     
cache size      : 1024 KB                                      
physical id     : 0                                            
siblings        : 2                                            
core id         : 0                                            
cpu cores       : 1                                            
apicid          : 0                                            
initial apicid  : 0                                            
fdiv_bug        : no                                           
hlt_bug         : no                                           
f00f_bug        : no                                           
coma_bug        : no                                           
fpu             : yes                                          
fpu_exception   : yes                                          
cpuid level     : 3                                            
wp              : yes                                          
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni monitor ds_cpl cid xtpr                                                     
bogomips        : 7181.85                                                       
clflush size    : 64                                                            
power management:                                                               

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15          
model           : 3           
model name      : Intel(R) Pentium(R) 4 CPU 3.60GHz
stepping        : 4                                
cpu MHz         : 3600.000                         
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmovpat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs btspni monitor ds_cpl cid xtpr
bogomips        : 7181.92
clflush size    : 64
power management:

neal@neal-XPS:~$ sudo modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
neal@neal-XPS:~$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy
neal@neal-XPS:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
performance
neal@neal-XPS:~$ sudo modprobe cpufreq_ondemand
neal@neal-XPS:~$ sudo modprobe cpufreq_performance
FATAL: Module cpufreq_performance not found.

```
That's after doing Step 1 + 2.
Step 5 only gave me performance, and the ondemand module wasn't found.  How do I get it so I can add it to etc/modules?  I think that's what I need.  Here's something else I tried:
```
neal@neal-XPS:~$ sudo -s
root@neal-XPS:~# echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
root@neal-XPS:~#

```
Now my computer is making a funny noise and running slower.
Tried to fix it:
```
root@neal-XPS:~# echo perfomance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: echo: write error: Invalid argument
```
Uh oh.  Please help.

---

### Post by Gotaro on 2009-02-08
You misspelled "performance".  I don't know if that's the problem or not ^^;

---

### Post by biggiemokey on 2009-02-08
Oh...that's embarrassing.  I have to try that again with proper spelling.  Thanks!

---

### Post by DonaldJ on 2009-02-08
Off the top, could this be "overclocking..  and/or that you need to format-C, and pull the battery for about ten minutes, before the install..?

---

### Post by khelben1979 on 2009-02-08
> **kansasnoob said:**
> Flash 10 in Linux just works the piss out of a cpu!

Install flashblock 1.5.7.1!

From my own experience: if gnash is used as a flash player this is true, but if I use the player from Adobe it's definitely not the case.

---

### Post by biggiemokey on 2009-02-08
Would having Gnash installed and not using it affect performance?  I will remove it next time I boot into Ubuntu.  Also I'm running a Dell desktop - no overclocking, no battery.

Typing ```
echo perfomance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
gave me no response (in the terminal), but the weird noise stopped.  How can I make it do ondemand CPU frequency all the time?  I think that is what I need.

---

### Post by biggiemokey on 2009-02-14
Well Gnash was not the problem.  I am still trying to figure out how to install the "ondemand" frequency scaling option, it doesn't seem to be on my computer since when I do:
```
neal@neal-XPS:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
performance
neal@neal-XPS:~$ sudo modprobe cpufreq_ondemand
```
apparently the only governor available is "performance" and trying to use ondemand gives me no output or notable difference in computer loudness.

I also don't know if speedstep is enabled.  I have a 3.6 GHz Pentium 4 from 2005, but
```
neal@neal-XPS:~$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy
neal@neal-XPS:~$ sudo modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

```
speedstep_centrino just doesn't work (I guess that's for Pentium M but I don't even know what Pentium M is) and acpi_cpufreq says the device is busy...

If anyone can help me getting "ondemand" working I would really appreciate it.

---

### Post by DonaldJ on 2009-02-15
Off the top..  It seems that the hd is way too obsolete to handle the new softwares...

Garage sales are coming up soon...  I'm sure you could get an 80-gig hd in a tower for about $2 to $20...  Try this little trick I use when I'm dickering prices at garage sales...  I walk up to the seller, and offer a dollar for an item that has a $500 price tag.. like a motor-bike or snowmobile or snowblower or rider mower or pentium-3 PC complete...  I say "Will you take a couple bucks for the wrecked snowmobile?"..  Or, on a tower priced at $150, I ask "Will you take 5-bucks for the wrecked tower?"..  and sometimes I get it for my asking price, even if it was advertised at a $100..  is how I get good towers and notebooks for 2 to 10 bucks, and $100 item collector 45's, in prime, for just pennies, like last year I stumbled upon the original "Peggy Sue" 45 in prime cond." for just $1.50...

Me thinks you need to replace that old hd with at least a year-2002 model with at least 50-gigs... 

There's another option to get a better hd...  Check out the city's "Computer library", where they lend PC's to the poor for one year durations...  People drop off their scrap electronics to those recycle places, and if you are friendly with them, and offer some of your time to assist them in recycling stuff, you will be able to acquire dozens of free hd's...
A couple years ago, when scrap metal yards were still taking computers, I could get a box-full of drives for just 5-bucks...
Thing about negotiating scrap-metal yards, is to always take each step in you head before to physically take each step...  Those places are full of wicked sharp metal scattered everywhere...  Those who don't take their steps in their head when roaming around junk metal-yards generally end up in the hospital with cuts to the bone...

Get a real hard drive...

---

### Post by biggiemokey on 2009-02-16
@ DonaldJ - So you're saying my hard drive is the problem?  I have a 160 GB WDC WD1600JD-75HBB0 (I think that's a Western Digital hard disk), and I bought the computer in 2004 or 2005 (either way, it's after 2002).  What made you think my hard drive was the problem?  Thanks anyway for the suggestion, and if my hard drive could be the problem please tell me how I would know for sure.

I still want to know how to enable "ondemand"...please help me if you know how.

---

### Post by Vico Vicario on 2009-02-16
1. Install powertop package and run 'sudo powertop'. It is a very cool app for Intel based computers that analyzes your power consumption and gives you advice on how to save energy.

2. Don't know Ubuntu, but Kubuntu with kde 4.2 has a wonderful power management applet that lets you define user profiles to set the cpu profile and speedstep. Maybe you can try new KDE.

V.

---

### Post by DonaldJ on 2009-02-16
Oops!  I thought I read "1995 hd"...

---

### Post by biggiemokey on 2009-02-17
@Vico - Will do next time I'm in Ubuntu.  I have Kubuntu installed as well, so I'll try both options - I'm assuming changes I make in KDE will take effect even if I use GNOME normally.  Thanks for the powertop tip, what I see on the website might help me since it shows the frequencies.

@DonaldJ - Thanks anyway for the advice.

If anyone knows how to install the "ondemand" frequency scaling governor for cpufreqd I would really appreciate some help.  For now I am going to try KDE's Power Manager.

---

### Post by biggiemokey on 2009-02-26
powertop:
```

< Detailed C-state information is not P-states (frequencies)
                                        3.60 Ghz   100.0%
                                        1350 Mhz     0.0%
                                         900 Mhz     0.0%
                                         450 Mhz     0.0%


Wakeups-from-idle per second : 213.1    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  37.5% ( 83.2)          knotify4 : schedule_timeout (process_timeout)
  27.8% ( 61.8)              kwin : schedule_timeout (process_timeout)
   8.5% ( 18.8)           firefox : futex_wait (hrtimer_wakeup)
   7.6% ( 16.8)       <interrupt> : ata_piix
   7.3% ( 16.2)      <kernel IPI> : Rescheduling interrupts
   1.8% (  4.0)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func)
   1.5% (  3.4)       <interrupt> : uhci_hcd:usb3, ohci1394
   1.4% (  3.2)   USB device  3-2 : Microsoft Wireless Optical Mouse .0A (Micros
   0.9% (  2.0)     <kernel core> : clocksource_check_watchdog (clocksource_watc
   0.6% (  1.4)         scsi_eh_0 : blk_plug_device (blk_unplug_timeout)
   0.5% (  1.2)              Xorg : schedule_timeout (process_timeout)
   0.5% (  1.0)       <interrupt> : ohci1394, fglrx[0]@PCI:1:0:0, eth0
   0.5% (  1.0)    NetworkManager : tg3_open (tg3_timer)
   0.5% (  1.0)        atieventsd : schedule_timeout (process_timeout)
   0.5% (  1.0)           klipper : schedule_timeout (process_timeout)
   0.4% (  0.8)           konsole : schedule_timeout (process_timeout)
   0.4% (  0.8)   hald-addon-stor : schedule_timeout (process_timeout)
   0.3% (  0.6)             kded4 : schedule_timeout (process_timeout)

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config


```

Thanks for the Powertop tip!  See, it runs 100% at highest frequency, I guess Speedstep is not working.  To reiterate, I tried p4_clockmod (I have a Pentium 4) but I would really like to know how to use "ondemand" frequency scaling with the cpufreqd program.  I enabled it through powertop, but my computer is making that static noise that it did before and I don't see any notable difference.  I also keep getting suggestions that I should suspend the USB devices Microsoft keyboard and Microsoft mouse as they are active near 100% of the time.  I don't really know what that means, but it didn't seem to make a difference.  I also killed hal-addon-storage, it said that had something to do with autoreading CDs, and I have noticed my CD drive acts funny in Ubuntu.

EDIT:  I got ondemand working, even though it still makes a noise.  My CPU now runs primarily at 450 MHz, but my fan is still loud!  Ugh.

---

