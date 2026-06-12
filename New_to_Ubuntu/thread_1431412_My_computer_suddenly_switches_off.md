---
title: "My computer suddenly switches off"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Tony.B on 2010-03-16
Good evening, everyone.

There appears to have been several posts about computers suddenly shutting down while running Ubuntu.  Mostly these seem to have been attributed to overheating.

From what I've read, this isn't confined to one operating system, but 9.04 Jaunty &  9.10 Karmic seem to be more prone to causing problems, nor to one particular make of computer, although laptops (and in particular Acer Aspire, Dell & Toshiba) seem to be more vulnerable.

But it does appear that the problem lies somewhere within Ubuntu, since there are several references to things working smoothly in other Ubuntu releases or, dare I say it, in Windows.

Several people claim to have fixes, too.  But this is an Absolute Beginners Forum  and, unless instructions are given literally step-by-step, I have no hope of understanding the instructions for the proposed remedies.  Maybe I'm the only one, but I tell myself that my advanced age and non-technological background gives me an excuse.

So this, then is my problem...
[INDENT]1.  After I have switched on my computer from cold, it suddenly shuts down for no apparent reason, usually after running for about half-an-hour;
2.  More often than not, whenever I restart (from warm) I can carry on running it all day without problems;
3.  Eventually I found out how to install the thermometer sensors, but they don't appear to work very well – usually the temperatures shown when I switch on (typically CPU 40°C & Temp1 40°C) remain unaltered while I work;
4.  But my computer still unexpectedly packs up;
5.  I have noticed, though, that when I switch back on after my unscheduled shut-down, the temperature sensors suddenly agree on a new total of 85°C;
6.  Now that I have this information, my instinct is to panic and immediately manually shut down again and wait at least an hour before restarting.  But this has caused further problems, because now I'm starting from cold, so the computer will then automatically switch off after approx 25 mins.[/Indent]

So I concur that the sudden shut-down appears to be heat related.  I'm a bit deaf (old age) so I can't hear whether or not the fan is working, which probably doesn't help diagnosis.  In fact I didn't even know a computer had a fan until I read it on this forum.

I have also read that I can fix things by using an older kernel, but I need much more detailed help than that.

Has anybody any ideas what to do to solve the problem, with step-by-step instructions, please.

With many thanks,
Tony.

---

### Post by undecim on 2010-03-16
Maybe your heat sensors are messed up. Your computer watches the heat sensors and will automatically turn off if you reach a certain temperature (usally 85°C). If your heat sensors are bad, then this will happen even when it's not supposed to.

If you want to try an older kernel, hold down shift before grub loads (i.e. right after you see your manufacturer's logo when you turn your computer on). You should get a list of kernels versions installed on your computer. Pick one (just avoid the "(recovery mode)" options)

---

### Post by Tony.B on 2010-03-16
Hi, undecim.  Thanks for the reply.
> **undecim said:**
> If you want to try an older kernel, hold down shift before grub loads (i.e. right after you see your manufacturer's logo when you turn your computer on). You should get a list of kernels versions installed on your computer. Pick one (just avoid the "(recovery mode)" options)
I need some help here:
[indent]- Would I be on the right track to try an older kernel?
- How would I know which older kernel to use?[/indent]
If I choose an older kernel, wouldn't I be losing some improvements to my system? I am somewhat confused.

Cheers,
Tony

---

### Post by J V on 2010-03-16
> **undecim said:**
> Maybe your heat sensors are messed up. Your computer watches the heat sensors and will automatically turn off if you reach a certain temperature (usally 85°C). If your heat sensors are bad, then this will happen even when it's not supposed to.I disagree, it seems the sensors are checking once but not again, so it checks on boot, slowly gets hotter, but the display doesn't register it.

Then on reboot the display is updated and it shows the temperature as 85 degrees (Which is when the computer is shutting down)

Kernels usually include security fixes, bug fixes, new drivers... if your system is working it shouldn't be entirely necessary to use a new one, but it is still a temporary solution...

We'll google some and find the answer :)

Also, you can check the fan by looking at the back of the computer (And the internal one by opening it up, its not hard, just look for the big spinning thing)

---

### Post by audiomick on 2010-03-16
Hi Tony,
yes, 85°C is a bit high. I notice on my desktop that the values go pretty constantly up and down a couple of degrees, so if you are seeing no movement at all, then I think that is a bit suspect, as is, of course, the jump after the re-start.

If the computer is as hot as you say, then you should be easily able to feel the warm air coming out. Look for a grill either on the sides towards the back or on the back under the monitor. You can very often see a copper heat sink or cooling fins behind the grill. There should be warm air coming out there if the fan is working hard to keep the machine cool. Another possibility is a match that you have just blown out, or a bit of paper set alight and blown out so it smokes, held where you think there should be air coming out. The draught should be strong enough to be easily visible.

Good luck!!

---

### Post by Tony.B on 2010-03-16
Hello Michael.
Nice of you to offer help (again!)
> **audiomick said:**
> ...If the computer is as hot as you say, then you should be easily able to feel the warm air coming out. 
It's a laptop, so it mostly gets hot underneath. Before someone asks, it has **never** been on a bed - always on a table (without a tablecloth). 

I'm constantly checking the heat with my hand, but it seems to get hot suddenly rather than gradually. I'm not sure if this is relevant - it could indicate that the fan (which I can't hear) starts and then stops, but it could also easily be that I'm mistaken.

In any event, the fact remains that I **don't** get the problem from a "warm" start.

Cheers,
Tony

---

### Post by 2hot6ft2 on 2010-03-16
What graphics driver are you using?
If it's NVIDIA you can go to
System > Administration > NVIDIA X Server Settings
Choose X Server Information on the left and on the right it will show something like 
NVIDIA Driver Version: 195.30
If it shows NVIDIA 195.36 or 196.75 then read on.

I have seen threads where it may be caused by NVIDIA driver 195.36.08 HERE:
[Do not update to 195.36.08! - nvidia]("http://ubuntuforums.org/showthread.php?t=1422970")
And here's the 196.75 mentioned as well:
[new nvidia drivers causing overheating?]("http://ubuntuforums.org/showthread.php?t=1422939")

[More Graphics Driver Overheating search results]("http://ubuntuforums.org/search.php?searchid=71000734")

So if you have one of those drivers downgrade to the next lower version in:
System > Administration > Hardware Drivers

---

### Post by Tony.B on 2010-03-16
Hello JV. Thanks for joining in
> **J V said:**
> Kernels usually include security fixes, bug fixes, new drivers... if your system is working it shouldn't be entirely necessary to use a new one...
This is exactly what worries me about using an old kernel.

> **J V said:**
> Also, you can check the fan by looking at the back of the computer (And the internal one by opening it up, its not hard, just look for the big spinning thing)
Are there **two** fans, then?  Like a helicopter?  But, seriously, what do I need to "check"?

Thanks,
Tony

---

### Post by Tony.B on 2010-03-16
Hi 2hot6ft2
> **2hot6ft2 said:**
> What graphics driver are you using?
I'm sorry - that's far too technical for me. Please tell me what a graphics driver is.  I went to **System > Admin** but there is no option labelled **NVIDIA X Server Settings**.

Does that help?

Cheers,
Tony

---

### Post by 2hot6ft2 on 2010-03-16
> **Tony.B said:**
> Hi 2hot6ft2

I'm sorry - that's far too technical for me. Please tell me what a graphics driver is.  I went to **System > Admin** but there is no option labelled **NVIDIA X Server Settings**.

Does that help?

Cheers,
Tony
A graphics driver is what controls your graphics card and makes it work.
Then you most likely don't have an NVIDIA graphics card or you don't have the proprietary driver installed. See what you have in:
System > Administration > Hardware Drivers

---

### Post by Tony.B on 2010-03-16
I'm sorry to appear so stupid: this is a huge learning curve for me.  Thanks to you helpful people on this forum I'm getting a lot better.  Certainly much better than my peer group who have never even heard of any alternative to Internet Explorer!

But I'm very conscious of the fact that I'm a total plonker compared to you computer whizz-kids.

> **2hot6ft2 said:**
> See what you have in:
System > Administration > Hardware Drivers

You're not going to like this.  I've received a message stating:
[indent]**No proprietary drivers are in use on this system**[/indent]

Cheers,
Tony

---

### Post by 2hot6ft2 on 2010-03-16
If it shows drivers available.

Choose the bottom one in the top section, it will say (recommended) next to it.
Then click on Activate Driver at the bottom and it will download the driver and install it.
You will have to reboot when it finishes.

There are none in use but are there any available is the question?

---

### Post by Tony.B on 2010-03-16
> **2hot6ft2 said:**
> If it shows drivers available...
Sorry. Our messages crossed.

---

### Post by 2hot6ft2 on 2010-03-16
> **Tony.B said:**
> Sorry. Our messages crossed.
No problem. If there are drivers available you want to activate one since they manage the graphics card better than the default driver that is installed.

---

### Post by Tony.B on 2010-03-16
> **2hot6ft2 said:**
> If there are drivers available you want to activate one since they manage the graphics card better than the default driver that is installed.
It doesn't show any drivers available either. Apart from the stark heading **No proprietary drivers are in use on this system**, it's a completely blank page.

How would I find out what drivers are available?

And, forgive my asking, but how does this affect the shutting-down problem?

Thanks
Tony

---

### Post by 2hot6ft2 on 2010-03-16
> **Tony.B said:**
> It doesn't show any drivers available either. Apart from the stark heading **No proprietary drivers are in use on this system**, it's a completely blank page.

How would I find out what drivers are available?

And, forgive my asking, but how does this affect the shutting-down problem?

Thanks
Tony
Well if it showed drivers as being available then installing the correct proprietary driver may have solved your overheating problem if that's what the issue is. But since there aren't any available that rules that out.
That is how you find out if drivers are available.
So if you made sure the fans are working then I'm not sure what the problem is at this point but I'll give it some thought while others give some more options.
Overheating causes shutdowns.

---

### Post by Tony.B on 2010-03-16
Thank you, 2hot6ft2, for all that info.

And for the offer of help too - much appreciated.

Cheers,
Tony

---

### Post by 2hot6ft2 on 2010-03-16
> **Tony.B said:**
> Thank you, 2hot6ft2, for all that info.

And for the offer of help too - much appreciated.

Cheers,
Tony
You're welcome.

---

### Post by audiomick on 2010-03-16
Hi Tony.
On the subject of drivers: I don't know how relevant it might be, but you can see what graphics card is in there fairly easily.
do
```
lspci
```in the terminal (that is all lower case letters, no numbers) and post the output here. There should be something in there that is called something like "VGA graphics adapter".

As 2hot6ft2 has already pointed out, if the "hardware drivers" thingy is not offering you anything, then it is probably not an issue. On the other hand, graphics cards can run hot, so it isn't a bad idea to know what is in there.

---

### Post by Tony.B on 2010-03-17
> **audiomick said:**
> Hi Tony.
On the subject of drivers: I don't know how relevant it might be, but you can see what graphics card is in there fairly easily.
do
```
lspci
```in the terminal (that is all lower case letters, no numbers) and post the output here. There should be something in there that is called something like "VGA graphics adapter".

As 2hot6ft2 has already pointed out, if the "hardware drivers" thingy is not offering you anything, then it is probably not an issue. On the other hand, graphics cards can run hot, so it isn't a bad idea to know what is in there.

Thanks for that, Michael. The output I got is:
```
tony@tony-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
```
To me, it's as clear as mud.

Cheers, Tony

---

### Post by audiomick on 2010-03-17
Hi.
So you have Intel graphics in there. As far as I know, they are taken care of by the in-built drivers, i.e. no proprietary drivers needed, which is why the "hardware driver" tool is not offering any.
I also haven't come across anything here that would indicate overheating problems with them specifically. That's not to say that is definitely out of the question, but I haven't heard of anything in that direction.

I reckon there might be something in this

[QUOTE=J V]I disagree, [COLOR="Red"]it seems the sensors are checking once but not again[/COLOR], so it checks on boot, slowly gets hotter, but the display doesn't register it.

Then on reboot the display is updated and it shows the temperature as 85 degrees (Which is when the computer is shutting down)
[/QUOTE]But is a bit out of my league trying to find out why. It is likely to be a software error somewhere, I guess (you did say somewhere that older Ubuntus and windows didn't have the problem, didn't you?).


Here is a breakdown of that output
```
tony@tony-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: [COLOR="Red"]Intel Corporation Mobile GM965/GL960 [/COLOR]Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```
Graphics card and associated stuff. Model name in red


```
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)

...

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)

```
Your USB ports

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```
Sound card / chip. 

```
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)

```
PCI controller, I think. Deals with the other stuff in this list (sound card, video, usb)

I know you have nothing better to do, so here's something to read:;)
[http://en.wikipedia.org/wiki/Conventional_PCI](http://en.wikipedia.org/wiki/Conventional_PCI)

---

### Post by JKyleOKC on 2010-03-17
This probably isn't the cause of your problem, but I think it's worth adding to the thread: I recently fired up my laptop after leaving it connected to AC but turned off for several months. After only a few minutes, I heard a small "Pop!" from somewhere inside it, and it turned off by itself.

I turned it back on, and the same thing happened again but it took a bit longer before it happened. This went on for several more times before I happened to remember that some laptop batteries suffer damage when left on charge for too long a time -- and mine had been in the charging mode for well over a year with no battery use (because the battery had gone dead that long ago).

I then physically removed the battery, and turned the machine back on. No more problem! Apparently whatever is wrong with that battery takes a while to show up, but when it does it trips an internal breaker that kills the power instantly.

My laptop is an HP model DV8000 so its internals are probably quite different from yours, but if you're running on AC power you might try taking out the battery and see if that makes any difference...

---

### Post by Tony.B on 2010-03-17
> **JKyleOKC said:**
> ......I then physically removed the battery, and turned the machine back on. No more problem! Apparently whatever is wrong with that battery takes a while to show up, but when it does it trips an internal breaker that kills the power instantly.......if you're running on AC power you might try taking out the battery and see if that makes any difference

Thanks very much for the idea, JKyleOKC.  I do usually run the laptop when it's plugged into the mains.  But, on the few occasions when I've had to use battery power alone, the system still cuts out.

Cheers,
Tony

---

### Post by Tony.B on 2010-03-17
> **audiomick said:**
> I know you have nothing better to do, so here's something to read:;)
[http://en.wikipedia.org/wiki/Conventional_PCI](http://en.wikipedia.org/wiki/Conventional_PCI)

Thanks, Michael.  I also had to look up "computer bus" to understand the article.

---

### Post by audiomick on 2010-03-17
> **Tony.B said:**
> Thanks, Michael.  I also had to look up "[COLOR=Red]computer bus[/COLOR]" to understand the article.
That's how computers get to work, isn't it? ;)

---

### Post by buskerjoe on 2010-03-17
hey pal, 
  i am glad to stumble onto this absolute beginners forum. i came to computers late in life & everything's counter-intuitive. nonetheless, i like ubuntu's spirit.
  ** my laptop shuts down, too,** if i leave the cursor inactive for just a few minutes. the only way to re-activate it is to shut it down & re-power, sign in, etc. i replaced the hard drive recently & hoped for some "problem-free" working time. 
    you say you can monitor the internal temp? how? (i doubt this is the problem, but that seems like a good thing to do)

---

### Post by audiomick on 2010-03-17
> **buskerjoe said:**
> ... if i leave the cursor inactive for just a few minutes. the only way to re-activate it is to shut it down & re-power, sign in, etc. ..
Hey Joe (;)),
have you looked at the screen saver / energy management settings?

In system> preferences select them and set them all to not do anything. See if that helps at all. It sounds like your computer is trying to suspend when there is no activity and getting hung up.

---

### Post by Tony.B on 2010-03-17
There we go!  It's just happened again.  I happened to be looking at the temperature sensors when, POW, the screen went black and the computer shut down.

So I can positively state that the temp gauges were indicating 40°C when everything went wrong, and that they had remained unchanged at 40°C since I switched on from “cold”.

But, when I re-booted, the temp gauges immediately showed 85°C, but dropped within a few seconds to 75°C, and then to 70°C.  Now, a few minutes after my “warm” start, they're down to 55°C.

So it would appear that, after the initial reading on a “cold” start, the temp sensors don't register any  subsequent readings, neither do they switch on the fan (I'm assuming that the fan is thermostatically-controlled).  But, on a “warm” start, everything works as it should: the fan kicks in to reduce the temperature and the gauges register the new readings properly.

- which is EXACTLY what **J V** said in post #4
> I disagree, it seems the sensors are checking once but not again, so it checks on boot, slowly gets hotter, but the display doesn't register it.

Then on reboot the display is updated and it shows the temperature as 85 degrees (Which is when the computer is shutting down).

As I type, the readings have now dropped to 50°C, by the way.

As regards the kernel, the “warm” re-boot was on the latest kernel (the top one on the list) as was the initial “cold” boot.  So I haven't done any thing different there.

And the temp has just dropped to 45°C.
And, as I typed that, it moved back up to 50°C.

Does any of this help?

Thanks in advance for any help you can give,
Regards,
Tony

---

### Post by VernonA on 2010-03-17
Earlier, Jim suggested you run with A/C power attached and battery removed (not A/C power removed and battery attached as your reply said). You should try this as it is a good suggestion and will help us eliminate one potential source of the problem.

(Our posts crossed, and it does look more and more like the problem is temperature-related. However, the test is still worth trying.)

---

### Post by audiomick on 2010-03-17
Hi.
That the (temperature) display didn't change at all up until the crash doesn't sound right. My display /indicators behave more like this:
> As I type, the readings have now dropped to 50°C, by the way.
 ....
 And the temp has just dropped to 45°C.
 And, as I typed that, it moved back up to 50°C.That really does make it look like JV was right, and I would concur with you
> So it would appear that, after the initial reading on a &#8220;cold&#8221; start, the temp sensors don't register any subsequent readings, neither do they switch on the fan (I'm assuming that the fan is thermostatically-controlled). But, on a &#8220;warm&#8221; start, everything works as it should: the fan kicks in to reduce the temperature and the gauges register the new readings properly.

The trick now is to find out why...

PS: yes, the fan is thermostatically controlled. I am not sure, but I assume it uses the same sensors that the task bar displays are supposed to be monitoring.

---

### Post by Tom.Gee on 2010-03-17
> **Tony.B said:**
> There we go!  It's just happened again.  I happened to be looking at the temperature sensors when, POW, the screen went black and the computer shut down.

So I can positively state that the temp gauges were indicating 40°C when everything went wrong, and that they had remained unchanged at 40°C since I switched on from &#8220;cold&#8221;.

But, when I re-booted, the temp gauges immediately showed 85°C, but dropped within a few seconds to 75°C, and then to 70°C.  Now, a few minutes after my &#8220;warm&#8221; start, they're down to 55°C.

So it would appear that, after the initial reading on a &#8220;cold&#8221; start, the temp sensors don't register any  subsequent readings, neither do they switch on the fan (I'm assuming that the fan is thermostatically-controlled).  But, on a &#8220;warm&#8221; start, everything works as it should: the fan kicks in to reduce the temperature and the gauges register the new readings properly.

- which is EXACTLY what **J V** said in post #4


As I type, the readings have now dropped to 50°C, by the way.

As regards the kernel, the &#8220;warm&#8221; re-boot was on the latest kernel (the top one on the list) as was the initial &#8220;cold&#8221; boot.  So I haven't done any thing different there.

And the temp has just dropped to 45°C.
And, as I typed that, it moved back up to 50°C.

Does any of this help?

Thanks in advance for any help you can give,
Regards,
Tony

It seems strange.  I am concerned that your machine seems to warm up noticably fast from a cold start.  

Some laptop fans are CPU controlled, running faster as more cooling is needed.  Since your sensors are failing to indicate a gradual increase in temperature, this perhaps a BIOS fault, the CPU does not know to increase the fan speed.  On warm boot, the stuck sensors are reset and start working, the CPU then knows to speed up the fan as necessary and things gradually cool down.  

From a purely diagnostic standpoint, I would ask this:  What happens if you cold boot, then warm boot about ten minutes into your session? Is the shutdown problem then circumvented?  Warm-booting ten minutes in, do you see some midpoint temperature between 40 and 85?  If this preemptive warm boot does nothing, and at 30 minutes in, the system still shuts off, you may just have a failing system fan that is getting stuck until things fully heat up.  

Most CPU controlled fans will run at full speed upon reboot, until the CPU determines that they can be slowed down.  Once fully warmed, this pulse to full power at warm-boot time might be just the thing to kick it over.  

You might try cold booting with a Live CD from some other operating system and looking for the machine to power off, just to be sure it is a problem specific to Ubuntu, and not simply a hardware problem.  

Good luck!

Tom

---

### Post by audiomick on 2010-03-17
Hallo again.

There are some interesting thoughts in Tom.Gee's post. In particular, the suggestion to pre-empt the crash and warm-boot manually would interest me too.



You might want to have a look at this
[http://ubuntuforums.org/showthread.php?t=1432262](http://ubuntuforums.org/showthread.php?t=1432262)

On the strength of that, I found this in the documentation
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

I followed (blindly and with my fingers crossed) the instructions there, and it more than doubled the number of sensors available to the indicator thing in the panel. For instance, I couldn't get a sensor for the CPU ( the central processor) until I had done all that.

When I do the command that they mention
```
sensors
```I now get this
```
mick@ubuntu-desktop:~$ sensors
f71882fg-isa-0a00
Adapter: ISA adapter
3.3V:        +3.41 V
Vcore:       +1.06 V  (max =  +2.04 V)   
Vdimm:       +1.74 V
Vchip:       +1.28 V
+5V:         +5.08 V
12V:        +14.27 V
5VSB:        +4.79 V
3VSB:        +3.41 V
Battery:     +3.34 V
CPU:        1238 RPM
System:        0 RPM  ALARM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
[COLOR=Blue]CPU:         +37.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
System:      +37.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +39.0°C  (high = +80.0°C, crit = +100.0°C)  [/COLOR]

```The stuff that I have coloured blue would be interesting for you, I think.

---

### Post by 2hot6ft2 on 2010-03-17
> **audiomick said:**
> 
You might want to have a look at this
[http://ubuntuforums.org/showthread.php?t=1432262](http://ubuntuforums.org/showthread.php?t=1432262)

On the strength of that, I found this in the documentation
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

I was just reading that thread myself and setup the applet in the top panel for the sensors and thought of this thread.

You may want to have a look and add the sensor applet to your top panel to keep an eye on your temperatures.

Here's a short version of installing them:
Just open a Terminal (Applications -> Accessories -> Terminal) and type (or copy and paste):

```
sudo apt-get install lm-sensors sensors-applet hddtemp
```

Next, run sensors-detect. Answer YES in CAPS to each one until finished.
> **audiomick said:**
> 
At this point, being lazy, I tried responding with a lower case "y" for "YES" and found that it worked.

```
sudo sensors-detect
```
Finally, restart to load all the sensors (you can choose Logout instead of Restart and it will be much faster). Once back at the desktop, right-click on the top panel and choose "Add to Panel." Select "Hardware Sensors Monitor" and click the "Add" button, then "Close." Right-click on all the sensors applet that appear and choose "Preferences." Click the "Sensors" tab. There you can select/de-select all the relevant sensors and adjust their low and high values as well as set alarms if desired.

Now you can also run
```
sudo hddtemp /dev/sda
```
Where sda is your hard drive.
and it will show the temperature of your hard drive if it can.

All temps. are in Celsius by default.
> **audiomick said:**
> 
In the preferences for the applet you can also choose Fahrenheit or Kelvin.

---

### Post by audiomick on 2010-03-17
@2hot6ft2 : nicely summarised. I have a couple of things to add.

> Next, run sensors-detect. Answer YES in CAPS to each one until finished.
     
     ```
sudo sensors-detect 
```At this point, being lazy, I tried responding with a lower case "y" for "YES" and found that it worked.

> Once back at the desktop, right-click on the top panel and choose "Add to Panel." Select "Hardware Sensors Monitor" and click the "Add" button, then "Close." Right-click on all the sensors applet that appear and choose "Preferences."As far as I know, Tony has the applet installed already.

> All temps. are in Celsius by default.     In the preferences for the applet you can also choose Fahrenheit or Kelvin.

---

### Post by 2hot6ft2 on 2010-03-17
> **audiomick said:**
> @2hot6ft2 : nicely summarised. I have a couple of things to add.

At this point, being lazy, I tried responding with a lower case "y" for "YES" and found that it worked.

As far as I know, Tony has the applet installed already.

In the preferences for the applet you can also choose Fahrenheit or Kelvin.
Thanks audiomick looks like I left that out. I'll quote the relevant parts you added and add it to the instructions I gave above. Sure wish I had tried the y when I did it, I thought the YES that many times was a bit ridiculous.

---

### Post by Tony.B on 2010-03-18
> **Tom.Gee said:**
> From a purely diagnostic standpoint, I would ask this:  What happens if you cold boot, then warm boot about ten minutes into your session? Is the shutdown problem then circumvented?  Warm-booting ten minutes in, do you see some midpoint temperature between 40 and 85?  If this preemptive warm boot does nothing, and at 30 minutes in, the system still shuts off, you may just have a failing system fan that is getting stuck until things fully heat up.
Hello Tom, thanks for that idea. 

I started up my computer from cold, checked email & sent off a couple of messages: temp counters stuck firmly on 40.

Then I shut down & re-started: temp counters still stuck on 40.

Then computer shut down all by itself about 10 minutes later.

When I restarted, temp counters showed 85.
  

> **Tom.Gee said:**
> You might try cold booting with a Live CD from some other operating system and looking for the machine to power off, just to be sure it is a problem specific to Ubuntu, and not simply a hardware problem.
I switched to Windows Vista (sorry for swearing) and had absolutely no problems whatsoever.

Thanks for your thoughts,
Cheers,
Tony

---

### Post by Tony.B on 2010-03-18
OK, audiomick & 2hot6ft2.  Thank you both for all the hard work.

I followed ALL the instructions, and the number of sensors on the top panel has increased from 2 to 3.  They are labelled CPU, Temp1 & Core 0.

Now, when I run **sensors** followed by ** sudo hdd/temp /dev/sda** I get:
```
tony@tony-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +43.0°C  (high = +100.0°C, crit = +100.0°C)  

tony@tony-laptop:~$ sudo hdd/temp /dev/sda
sudo: hdd/temp: command not found
tony@tony-laptop:~$ 

```

Does any of that help?

Regards,
Tony

---

### Post by Tony.B on 2010-03-18
> **moi said:**
> ......I get:
```
tony@tony-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +43.0°C  (high = +100.0°C, crit = +100.0°C)......
```

I've just run that again after switching off & re-starting, with similar results.

Is it significant that this output doesn't mention the CPU temp, even though I've got a little thermometer for it sitting on my top panel?

If I've understood everything correctly (which I doubt!), it would appear that my kernel is forgetting to switch the fan on when I start up my computer from cold.

But when the fail-safe cut-out has shut the system down, re-booting while the laptop is still warm switches on the fan properly.  (Presumably something else is switching it on, because we know the kernel isn't).

Cheers,
Tony

---

### Post by audiomick on 2010-03-18
> **Tony.B said:**
> I've just run that again after switching off & re-starting, with similar results.

Is it significant that this output doesn't mention the CPU temp, even though I've got a little thermometer for it sitting on my top panel?No, I don't think so. I also have a couple of indicators in the panel that don't show up in the "sensors" output. In my case, it is the graphics card and the two drives.

> If I've understood everything correctly (which I doubt!), it would appear that my kernel is forgetting to switch the fan on when I start up my computer from cold.

But when the fail-safe cut-out has shut the system down, re-booting while the laptop is still warm switches on the fan properly.  (Presumably something else is switching it on, because we know the kernel isn't).
That about sums up what the problem _seems_ to be at this stage.
If I have understood everything correctly, the problem only occurs with the Ubuntu that you currently have installed, i.e. not in Vista, and you have no older Kernels on the machine at the moment, right?

---

### Post by Tony.B on 2010-03-18
Good evening, Michael,
> **audiomick said:**
> If I have understood everything correctly, the problem only occurs with the Ubuntu that you currently have installed, i.e. not in Vista, and you have no older Kernels on the machine at the moment, right?

Yes. That's exactly right.

I've had the opportunity to do another cold start, and everything is a bit different now that I have the Core temperature gauge on the top panel.

When I started up from cold, the 3 gauges were reading
[indent]- CPU 40°C
- Temp1 40°C
- Core 40°C[/indent]
but after a few moments the Core temp had risen while the others remain unchanged.

When I logged on to the internet, the Core temp started to increase even more until, after about 20 minutes or so, it reached 90°C and I shut down my computer, before the fail-safe triggered an automatic shut-down.  The other gauges were still stuck on 40°C.

When I re-started (from warm), the three gauges read:
[indent]- CPU 85°C
- Temp1 85°C
- Core 74°C[/indent]

But now presumably the fan has kicked in, because the Core temp has dropped and is hovering around 40°C.  The other two gauges still show 85°C.

Regards,
Tony

---

### Post by Tony.B on 2010-03-18
Thanks to a message from Ubuntu expert **Vince N** I've also tried to read this bug report on Launchpad
[indent][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)[/indent]

It seems to me that there is some patch available to fix this problem, but I can't find out how to use it.

Any ideas?

Thanks in advance,
Tony

---

### Post by audiomick on 2010-03-18
Hi Tony.
I read through that thread and reached the following conclusions:

Yes, there definitely appears to be an issue with newer kernels that specifically affects the Acer Aspire 5315, which you mentioned in the "7 kernels" thread as being your model.

Someone wrote a patch, and apparently there were some .deb files at the address that is linked to a number of times, but they are not there now, as is also mentioned by someone further down the thread.

If there were .deb files available, I would know what to do with them. I have no idea what to do with the .patch files that are there...

Later posts report that the problem reappears after a kernel update, and that for some people didn't work, so it is not a "permanent" fix.

Derived from some later posts in the thread, the problem is not fixed yet. Going by the last post, the developers haven't forgotten about the problem, but don't have a permanent fix yet.

This guy
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337/comments/39](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337/comments/39)
updated his BIOS and said that this fixed the problem. He has a link to a later BIOS in the post. I am still looking into this, but it looks like something that might provide a solution, and might not be that hard to do.
I will post again when I have finished reading...
How late will you be up this evening?

---

### Post by 2hot6ft2 on 2010-03-18
I read thru the launchpad bug page you linked to as well and a few of them solved the overheating by updating the BIOS of their machines.
I see you have an Acer Aspire 5315 and I checked their website here:
[http://support.acer.com/drivers_download.aspx](http://support.acer.com/drivers_download.aspx)
for your model and didn't find any BIOS updates.

Meanwhile I found a post from a couple years ago here: [Running Hot]("http://ubuntuforums.org/showthread.php?t=763450")
And while I don't see how it could possibly help you could give it a try since it can't do any harm and will only persist until you reboot unless you make it permanent.
> **TimKraemer said:**
> I found a solution:

The Problem seemed to be that my ram got incredibly hot, because the kernel was constantly reorganizing the memory and swapping to disk unused data. A quick google-search on "swappiness" gave me the solution: To stop the kernel from constantly optimizing my ram, I had to set the "swappiness" of my laptop from 60 down to 0. Now unused data is only moved to the swap partition if some application needs cache -> less usage of my ram ->  lower temperatur of my ram and of my CPU which sits just next to the ram.

You change it on-the-fly by changing the swappines:

```
sudo sysctl vm.swappiness=0
```

If it helps, add the line "vm.swappiness=0" to the end of /etc/sysctl.conf
Never mind the how to add it to sysctl.conf for now. If it actually helps we can tell you how to do it properly since the file already has an entry for it and it would just be a matter of changing the value (don't want 2 entries for it).

Also I don't know if you added the System Monitor Applet to your panel but if you haven't you may want to, that way you can see if the processor use starts to get real high which may indicate something putting a lot of load on your machine causing it to heat up (a runaway process).
Right click on the top panel and select Add to Panel then System Monitor then on Add then close.
You can always remove the applets later by right clicking on them and selecting Remove From Panel once we figure things out.

I also just found out how to add the hddtemp to the Hardware Sensors Applet so I thought I would toss that in here too.
> **dcstar said:**
> ```
gksudo gedit /etc/default/hddtemp
```

Make RUN_DAEMON="true", save and reboot.
Still looking.

---

### Post by audiomick on 2010-03-18
Hi Tony.
First of all, the following is my advice based on the info I have read here in the links here.
I have not tried any of it out, and can't promise that any of it will work.

Secondly, I gather you have a dual boot setup on the machine, and can boot into Vista? If this is not the case, you needn't bother reading the rest of this....;)

I am being so cautious because this is leading up to a BIOS update.
This is something to be approached with utmost caution. If it goes wrong, the computer is dead, and in the worst case the BIOS chip might have to be replaced, which might effectively mean the mother board being changed, from what I have heard and read.

I believe that flashing (updating) the BIOS yourself will generally instantly void any warranty that might be still valid on the machine.

On the other hand, the actual procedure in this case isn't very difficult as such, and the process is one that normally works ok.
You will have to decide for yourself, or wait until a few other people post and back me up or scream "no, don't do it!!!"


After some consideration, I would, if I were in your position, attempt the BIOS update using this version:

[http://launchpadlibrarian.net/35364174/BIOS_v1.45.zip](http://launchpadlibrarian.net/35364174/BIOS_v1.45.zip)

This is just a copy of the link in the post that I linked you to in my last post.
I will tell you what to do with it further down.

This is a newer version of the BIOS than is available at the Acer site here
[http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html)
where the highest version available is v1.43 from July 2008. The v.1.45 is from November 2008.

You will surely be aware that one should be wary of links to things that one can not confirm that safety of. I think this link is ok for the following reasons:

The thread that the link is in is on a trustworthy site, as far as I know

The zip includes a "readme.txt" in which
a) the laptop model is specifically mentioned
b) the instructions contain word for word the exact same bad English that the readme from the v1.43 driver from the Acer site contains. "please kindly unzip..."
[ATTACH]150558[/ATTACH]

The readme also mentions an eMachines E510. The eMachines site offers a v1.45 driver with a different name and readme, but the same creation date and time _to the second _as the one in the link in the post.
[ATTACH]150560[/ATTACH]

I am satisfied that the driver originally came from the same source as the BIOS updates on the Acer site and the eMachines site (probably the motherboard manufacturer.)


So, having been through that, here is what you do with it:

Boot into Vista.
Download the .zip file in the link.
Unzip it. It will unpack to the BIOS_v1.45 folder that you can see in the second screenshot.
click on the BIOS_v1.45.exe file and let it run.

That should be it.

---

### Post by 2hot6ft2 on 2010-03-18
Nice job audiomick and nicely written up. Considering the amount of information that leads to the conclusion that the BIOS update is possibly the solution I second your proposal and see no flaws in your instructions.
[-o<
Now I can close the half dozen tabs I have open.

---

### Post by audiomick on 2010-03-18
> **2hot6ft2 said:**
> Nice job audiomick and nicely written up.
Thank you very much. And thanks for the confirmation.;)

---

### Post by buskerjoe on 2010-03-18
Fixed my problem! Computer screen was going blank. Sure enough, as michael (#28) suggested, power saving preferences were set under screensaver to power off or suspend after only 5 minutes. I changed it to 45 minutes. 
  I still haven't been able to find how to re-activate when it's on "suspend," though. 
   So great to stumble onto this forum! Thanks to all who post!

---

### Post by 2hot6ft2 on 2010-03-18
> **buskerjoe said:**
> Fixed my problem! Computer screen was going blank. Sure enough, as michael (#28) suggested, power saving preferences were set under screensaver to power off or suspend after only 5 minutes. I changed it to 45 minutes. 
  I still haven't been able to find how to re-activate when it's on "suspend," though. 
   So great to stumble onto this forum! Thanks to all who post!
On my laptop the only way I've found to come out of suspend is to press the power button for just a moment (press and release). Then it will ask for my password and I'm back at the desktop.

---

### Post by audiomick on 2010-03-19
> **2hot6ft2 said:**
> ..the only way I've found to come out of suspend is..
I have never had that working. Not enough patience to work out how....

---

### Post by Tony.B on 2010-03-19
Now that I have the Core temperature reading, I can shut down & re-start before things get critical.  So, although this is a nuisance, and although my laptop's not behaving as it should, I can at least watch the gauges and avoid the problem of an automatic crash.

I'm sorry Michael, I'm not confident enough to tackle this BIOS thingy. BIOS means Built-in Operating System, I think, and the idea of tinkering with it scares me.

I tried **2hot6ft2**'s codes: 
Code: sudo sysctl vm.swappiness=0 produced the following output:
```
tony@tony-laptop:~$ sudo sysctl vm.swappiness=0
[sudo] password for tony: 
vm.swappiness = 0
```
When I started the above exercise, the temperatures were
[INDENT]- CPU 40
- Temp1 40
- Core 57[/INDENT]I've been watching the Core Temp gauge closely, while I'm typing this in fact, and, although it has hovered around 79 degrees, it hasn't increased any further than 82 (so far!).

> **2hot6ft2**: I also just found out how to add the hddtemp to the Hardware Sensors Applet so I thought I would toss that in here too.
Quote: Originally Posted by dcstar  
Code:
gksudo gedit /etc/default/hddtemp 

I did as you suggested and got the following on a pop-up screen:
```
# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# [automatically edited by postinst, do not change line format ]

# hddtemp network daemon switch. If set to true, hddtemp will listen
# for incoming connections.
RUN_DAEMON="false"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
#DISKS="/dev/hda"

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures. If set to a value
# different than 0, hddtemp will run as a daemon periodically logging
# the temperatures through syslog
RUN_SYSLOG="0"

# Other options to pass to hddtemp
OPTIONS=""

```
I don't know how to progress from here. Perhaps I've done something wrong.

Cheers,
Tony

---

### Post by Tony.B on 2010-03-19
> **Tony.B said:**
> BIOS means Built-in Operating System, I think, and the idea of tinkering with it scares me.

OK, I just wikipedia-ed it.  BIOS actually means "basic input/output system".  But I think my guess amounts to much the same thing, and is easier to understand.

I still don't wish to meddle with it, though.

There'll be Ubuntu 10.04 arriving in 5 weeks time.  The upgrade may well solve all my problems.

Does anyone agree?

Regards, Tony

---

### Post by audiomick on 2010-03-19
Hi Tony.
firstly, relating to what to do after this
```
gksudo gedit /etc/default/hddtemp                      
```form two posts back or so.

The "gedit" part of that is a text editor that is opened by that command, i.e. you can change the text in the window not unlike in a word processor.

What you need to do, according to 2hot6ft2's earlier post is to replace the word "false" with the word "true" here:


```
# [automatically edited by postinst, do not change line format ]

# hddtemp network daemon switch. If set to true, hddtemp will listen
# for incoming connections.
RUN_DAEMON="[COLOR=Red]false[/COLOR]"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
#DISKS="/dev/hda"

```just select the word, type over it and save and exit the editor. Make sure the inverted commas don't get lost...

Regarding the BIOS update vs. waiting for Ubuntu 10.10. 
Yes, it is possible that the next Ubuntu Version will have the problem sorted. There is no guarantee of this, but a reasonable possibility, as we know that there are people aware of the problem. If it is still mucking you around after that, you could still try the BIOS update then.

You are perfectly justified in being cautious with a BIOS update. It is a very low level procedure, and as I said already, if it goes wrong, the computer is dead. It is recoverable dead with a certain amount of effort, but it is still dead.

One option you have of course is to let a professional do the BIOS update for you, if you can find someone who is willing. It is, after all, a standard maintanance task. A computer shop should be willing to do it, and it shouldn't be that expensive.

---

### Post by Tony.B on 2010-03-19
> **JKyleOKC said:**
> My laptop is an HP model DV8000 so its internals are probably quite different from yours, but if you're running on AC power you might try taking out the battery and see if that makes any difference
> **VernonA said:**
> Earlier, Jim suggested you run with A/C power attached and battery removed (not A/C power removed and battery attached as your reply said). You should try this as it is a good suggestion and will help us eliminate one potential source of the problem

My apologies to **Jim Kyle** and **Vernon A** for not reading their posts carefully enough.  I didn't know that the battery is could be removed without dismantling the whole thing, but I found the instruction manual, waded through 15 other languages, and got the info.

Now that the battery is no longer in place, there seems to be no noticeable difference (except that the battery light isn't on!) but thank you very much for the idea.

Regards, Tony

---

### Post by Tony.B on 2010-03-19
Hello Michael

Thanks for all that.  Let me answer the last bit first:
> **audiomick said:**
> One option you have of course is to let a professional do the BIOS update for you, if you can find someone who is willing. It is, after all, a standard maintenance task. A computer shop should be willing to do it, and it shouldn't be that expensive.
Although the word Ubuntu comes from this part of the world, I regret that the concept doesn't extend to computer shops in this area.
[indent]- Most of their personnel seem to have the reputation of second-hand car salesmen.
- If you shake hands with them, you must count your fingers to make sure you got them all back.
- If you go to them with a problem, they just want to sell you the most expensive item they've got.[/indent]
That's why this forum is so wonderful.  Everyone we meet here is genuine and really wants to help.  I'm afraid that doesn't happen in my local shops.

OK. Rant over. I'm going to switch off, replace the battery before I lose it, and then look at the rest of your message.

Cheers,
Tony

---

### Post by Tony.B on 2010-03-19
> **audiomick said:**
> 
What you need to do, according to 2hot6ft2's earlier post is to replace the word "false" with the word "true" here:


```
# [automatically edited by postinst, do not change line format ]

# hddtemp network daemon switch. If set to true, hddtemp will listen
# for incoming connections.
RUN_DAEMON="[COLOR=Red]false[/COLOR]"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
#DISKS="/dev/hda"

```just select the word, type over it and save and exit the editor. Make sure the inverted commas don't get lost...
Sorry to appear so dense, but I have no experience of this. Is there something else I should have done?

I changed "false" to "true", saved and closed the pop-up box. But nothing happened, so I re-started my computer.  But still nothing happened.

I messed up, didn't I?

Cheers, Tony

---

### Post by audiomick on 2010-03-19
> **Tony.B said:**
> I messed up, didn't I?

Not necessarily.
If the change had an effect ( and that is only to be expected after a re-boot. I forgot to mention that...), when you right click on the sensors and select "preferences", on the second tab, "sensors", the change _might_ have added the option to active a hdd (drive temerature ) sensor.
There is no certainty that a) this wasn't there already (on my machine this was available before any of the "add more sensors" steps that have been discussed, or b) the sensor is just not available on your machine.
It is something that is worth a try, but if it doesn't have any effect, then that's just the way the world is, I think.

---

### Post by 2hot6ft2 on 2010-03-19
Looks like you've all been busy at it and already covered everything.
audiomick is right I left out that you'll need to right click on the sensor applet, select preferences then the sensors tab and there should now be a hddtemp sensor that wasn't there before.

Click on the arrow next to it and you should see your drive listed as something like /dev/sda.
Simply check the box and it should now appear with the other sensors in the applet.

Thanks for picking up on where I left off audiomick

---

### Post by 2hot6ft2 on 2010-03-19
I understand that you don't feel comfortable doing the BIOS update and I'm not trying to talk you into doing it by any means. I just had to get this out.

I wouldn't pay anyone to do the BIOS update. All they will do is see that you already have it downloaded and say come back tomorrow. Then they will double click on it and it will be done in what 10 - 15 seconds I think is what mine took a few months ago when there was an update for mine. And if they're as bad as you say then they'll stick it to you for that 15 second job. Well boot up and shut down so 5 minutes.

It is risky but it's nothing like it used to be where you would have to put it on a floppy disk and boot up with it praying the whole time the floppy was good and it wouldn't fail. I'm sure others here remember those days all too well.

If you're not comfortable with doing it you should at least get the flash downloaded so you wont have to search for it later when you get more used to how things work and become more comfortable with the idea.

I'm done with that. I got it out so onward.

---

### Post by audiomick on 2010-03-19
> **2hot6ft2 said:**
> If you're not comfortable with doing it you should at least get the flash downloaded so you wont have to search for it later when you get more used to how things work and become more comfortable with the idea.

This is very good advice. Download the zip file and burn it to a CD or something. Put it on the shelf, and forget about it for now. You might want to have a go at it at some stage, and if you have it there, the whole thing will be lot easier.

---

### Post by Tom.Gee on 2010-03-20
> **Tony.B said:**
> Hello Tom, thanks for that idea. 

I started up my computer from cold, checked email & sent off a couple of messages: temp counters stuck firmly on 40.
Then I shut down & re-started: temp counters still stuck on 40.
Then computer shut down all by itself about 10 minutes later.
When I restarted, temp counters showed 85.
  

OK. So much for that idea...


> **Tony.B said:**
> I switched to Windows Vista (sorry for swearing) and had absolutely no problems whatsoever.


Then this is surely a compatibility issue between Ubuntu and your machine, be it BIOS or hardware.  I would recommend the scary BIOS Update thinggy.  

> **2hot6ft2 said:**
> I understand that you don't feel comfortable doing the BIOS update and I'm not trying to talk you into doing it by any means. ... It is risky but it's nothing like it used to be where you would have to put it on a floppy disk and boot up with it praying the whole time the floppy was good and it wouldn't fail. I'm sure others here remember those days all too well.  

I remember those days.  And I also remember, most machines built since those days have fail-safes built in to help you recover from a bad flash.  It would be advisable to research and know how to invoke the machine's flash fail-safe mode if it has one.  

I've personally never had a flash go bad; however, I have always double checked my media before I flash.  Typically, I would either copy all files off the media into a temp directory, or I would open the .BIN and the .EXE files as read-only in a HEX editor, to be sure they could be read.  

It would sure be nice if you had a trusted computer geek somewhere nearby to help with this.  I've taken a quick look - from what I can see there is no facility to search for forum members by location.  If you were anywhere near Burlington NJ, USA I'd be glad to pop on over and give it a look...

Tom

---

### Post by Tony.B on 2010-03-20
> **2hot6ft2 said:**
> I understand that you don't feel comfortable doing the BIOS update......It is risky but it's nothing like it used to be where you would have to put it on a floppy disk and boot up with it praying the whole time the floppy was good and it wouldn't fail. I'm sure others here remember those days all too well.

If you're not comfortable with doing it you should at least get the flash downloaded so you wont have to search for it later when you get more used to how things work and become more comfortable with the idea.

Thanks, 2hot6ft2. You're right: I'm not comfortable with possibly jeopardising my laptop just for something that is a mere inconvenience.  The idea of copying the proposed solution to a flash download (= memory stick?) or a CD appeals to me, and I intend to do this.

Nevertheless,  I still hold out hopes that upgrading to Ubuntu 10.04 will solve problems, as I didn't have them in version 9.04.  

Another consideration is that, from what I've read, a BIOS upgrade must be performed with a stable electricity supply.  Here in Kwa-Zulu-Natal (just south of Durban in South Africa) we've had 3 unplanned periods of no electricity today. So I'm not very inclined to take the gamble that everything's going to be ok.

I hope you understand.

Cheers,
Tony

---

### Post by audiomick on 2010-03-20
> **Tony.B said:**
> Another consideration is that, from what I've read, a BIOS upgrade must be performed with a stable electricity supply.  Here in Kwa-Zulu-Natal (just south of Durban in South Africa) we've had 3 unplanned periods of no electricity today.
So that's what KNZ means. I had been wondering. I was in Durban about 12 years ago. I liked it there.

That kind of erratic electricity supply is a very good reason for leaving the battery in the laptop, even if it does shorten the life of the battery somewhat.

---

### Post by Tony.B on 2010-10-14
I've recently discovered that I can make my overheating laptop problem disappear which, in turn, solves the problem I posed in this thread.

I noticed that, if I close the lid of my laptop, it goes into suspend-mode. And the fan starts up correctly when I open the lid and continue working, *even if the laptop wasn't warm when I initially shut the lid.*

So my new Start-Up routine is:
1. Boot up laptop and wait until the desktop is displayed.
2. Close laptop lid and wait approximately 10 seconds until the system goes into "suspend" mode (on my Acer, the light showing that the laptop is switched on changes from steady green to flashing red).
3. Open laptop lid, type password to come out of "suspend". And, hey presto, everything works ok with no overheating issues.

This certainly works for me, I hope this simple procedure is of some assistance to others.

Cheers,
Tony

---

