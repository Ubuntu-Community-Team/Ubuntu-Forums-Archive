---
title: "firefox shuts down"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by DarinB on 2009-08-19
My firefox shuts down all the time annoying unusable, 
i tried making .mozilla a _back up and letting it recreate it but it is such a pain forgot tons of my passwords, i decided to look in the original .mozilla and now i see a appreg file what is that....i read that i should delete it is that true??????

---

### Post by RedSingularity on 2009-08-19
Did you try running it from the terminal to see what is causing the shutdown?

---

### Post by DarinB on 2009-08-19
how do i do that well i imagine i open a terminal and type firefox. but then how do find out how it crashes???????
, i do see a futex wail in system monitor but not sure if that is the cause the internet is confusing on the futex issue????? but it is really horrible, thinkint of using opera but that is a pain not as easy for me as firefox.

---

### Post by BigBananaMan on 2009-08-19
All you need to do is open up a terminal and type "firefox" and use it like normal.  When it does exit, you should see some text displaying what happened.
I hear Opera is a good browser though I've never tried it myself.  Generally issues like this are something minor that you can fix in a few minutes once you figure it out.

---

### Post by RedSingularity on 2009-08-19
Which firefox version are you using?  And if you could, just post the output in the terminal when you run firefox in there.

---

### Post by DarinB on 2009-08-19
i really hope it is easy but it is nerve racking...
i use firefox 3.0.13 i have also be having panel crashes as well i thought it was do to the linux image upgrade i got today,,,so i am using image .14 but it is all getting kind of confusing as soon as it shuts down i will be back.

---

### Post by DarinB on 2009-08-19
darin@darin-desktop:~$ firefox
Segmentation fault

here it is it happens so much hard to stay on this site

---

### Post by RedSingularity on 2009-08-21
Do you have an option for "firefox-3.0" in the repos?

---

### Post by znoren on 2009-08-21
I am also using Firefox 3.0.13 in Jaunty. Firefox causes a segmentation fault when I try to organize bookmarks - not when I click "Organize Bookmarks...", but when I click a folder to organize. It also happens when I right-click a bookmark (e.g., to delete it).

DarinB, do you do anything in particular that may cause the segmentation fault?

---

### Post by DarinB on 2009-08-21
watching hulu or any other streaming video sometimes if i have a few tabs open i have removed scim as it says in another post and removed all of my addons. i tried replacing the .mozilla folder but caused no change. i am ready to throw this thing out the window if it is a bad enough crash the panel crash and i have to hard reboot. this is killing me any ideas, i don't know how ubuntu can all of a sudden go so wrong.

---

### Post by winotree on 2009-08-21
Sorry to hear about your problems -- but I can't believe that Ubuntu would suddenly stop working anymore than I believe that Firefox would, although they apparently seem to leave us hanging sometimes.  :)  Regardless, have you tried any of the remedies suggested in the Standard Diagnostic - Firefox which you'll find here [http://kb.mozillazine.org/Standard_diagnostic_-_Firefox](http://kb.mozillazine.org/Standard_diagnostic_-_Firefox)

It may be a bit of work to go through this but if successful, it'll be worthwhile.  Hope to hear you're up and running smoothly sometime soon.  ;)

---

### Post by DarinB on 2009-08-21
trying to do the trouble shooting for firefox-3.5 but can't figure how to get it into safe mode??? the instructions aren't clear for me????

---

### Post by winotree on 2009-08-21
This ** /usr/bin/firefox-3.0 -safe-mode**  worked for me (but to be honest I had to look for it).  It also presupposes you're using the same version of the fox...  ;)

Make sure that *your* Firefox is turned off when doing this -- just follow the directions, take your time and do each step as you come to it.  If this doesn't help for goodness sake post back for assistance.

---

### Post by lockaar on 2009-08-21
Hey everyone,

I'm actually having what sounds like the same problem as the Topic Creator, Firefox will just crash on me whenever I visit for example, Hulu.com (loading the page), Justin.tv (going into any category after the main page), or even sometimes ESPN (main page, or randomly any other sub-page). I'm using version 3.0.13 of Firefox.

I've checked the errors and every time Firefox crashes it is the same error no matter the site, my error reads:
```
@ubuntu:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x621b50: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621b50: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621b50: NP_GetValue
GCJ PLUGIN: thread 0x621b50: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621b50: NP_GetValue return
GCJ PLUGIN: thread 0x621b50: NP_GetValue
GCJ PLUGIN: thread 0x621b50: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621b50: NP_GetValue return
Illegal instruction
```

I don't know what could be causing this, I recently installed the latest AdobeLabs version of Flash (10) for 64-bit system, but I doubt that is the problem since more people haven't reported it.

---

### Post by DarinB on 2009-08-22
i removed xmarks and the crashing has slowed a bit, some sites crash more than others and if i have multiple tabs open. you can see an apology at the xmarks site. i just stopped all tabs but no change. I also found it is certain web sites. I did reinstall flashblocker but it seems to Still be a mystery. i am wondering and **please** some one answer can I go back to a firefox 3.00000 or even 2.00 i remember 2.0 was the best. i must say that evern opera crashes but the opera site says its a java run time error. BOY!!!! that is the argument against open source.......the inconsistencies in add ons. and apps like firefox.

---

### Post by sandyd on 2009-08-22
> **lockaar said:**
> Hey everyone,

I'm actually having what sounds like the same problem as the Topic Creator, Firefox will just crash on me whenever I visit for example, Hulu.com (loading the page), Justin.tv (going into any category after the main page), or even sometimes ESPN (main page, or randomly any other sub-page). I'm using version 3.0.13 of Firefox.

I've checked the errors and every time Firefox crashes it is the same error no matter the site, my error reads:
```
@ubuntu:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x621b50: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621b50: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621b50: NP_GetValue
GCJ PLUGIN: thread 0x621b50: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621b50: NP_GetValue return
GCJ PLUGIN: thread 0x621b50: NP_GetValue
GCJ PLUGIN: thread 0x621b50: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621b50: NP_GetValue return
Illegal instruction
```

I don't know what could be causing this, I recently installed the latest AdobeLabs version of Flash (10) for 64-bit system, but I doubt that is the problem since more people haven't reported it.

[https://bugs.launchpad.net/bugs/315202](https://bugs.launchpad.net/bugs/315202)

read that

and this

[http://ubuntuforums.org/showthread.php?t=972922](http://ubuntuforums.org/showthread.php?t=972922)
try removing gcj-base

---

### Post by DarinB on 2009-08-22
above i don't have the gcj-4.2-base
gcj-4.3-base i do have icedtea-6-jre-cacao and
icedtea6-plugin
not sure what to do reinstall it???? throw my pc out the window??? Delete ubuntu and reinstall vista?????

---

### Post by DarinB on 2009-08-22
Ok i just went to my .java and made it .java.backup
it hopelessly crashes the panel. so i reboot and made it .java again i thought it might regenerate a .java that is clean the way .mozilla does.....so now i am back to square one but as i said i only have icedtea-6-jre-cacao and
icedtea6-plugin and java common????what next?

---

### Post by mgmiller on 2009-08-22
I recently had a similar problem that started overnight for no reason.  Turned out it was a hardware issue.  One of my memory sticks had failed.  As soon as Ubuntu tried to access that part of memory, bam! Things went screwy.  Usually it manifested in Firefox.  I actually installed opera, which seemed to work better because it has a smaller memory footprint.

Anyway.  Here is how you check..
When you reboot and you see the screen with the kernels listed, scroll down to the last entry which is memtest.

Let it run a bit and see if you get any errors.  In my case the screen lit up with red text almost immediately.

I next tried using only 1 of my memory sticks at a time and running memtest and discovered which one was bad.  Running on the 1 good stick I had no problems and got a replacement stick from the memory manufacturer.  

I've had no problems since.

Hope this helps...

---

### Post by lockaar on 2009-08-22
I don't have any of the gcj-4.x base's installed, so I don't think that is part of my problem, unless it NOT being installed is causing the problem...

I will try installing them to see if that is the problem.

EDIT: Installing those did nothing other than remove all of those GCJ PLUGIN errors, but Firefox still crashes and the terminal now just reads:

```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
```

---

### Post by mgmiller on 2009-08-22
I also went crazy with segfaults and inconsistent crashes and everything else everyone here is complaining of.

Have you tried running memtest yet?  Quick and easy and it rules out a number one source of sudden onset inconsistent instabilities.

:popcorn:

---

### Post by DarinB on 2009-08-22
I did it ran thousands of errors for over 3 hours and kept running i figured something was wrong with the test, the pc is only about 5 months old. and only started with problems about a month ago. i have done a lot of stuff and now it works really ok still crashes but no were near as much. Not sure what to do? i hate to have to replace hardware i will be calling the company on monday. i wonder, i did run a memtest with a hardy live disc and it did not take too long but came out ok.

---

### Post by DarinB on 2009-08-23
well i had one shut down on firefox. i did open up the box pull out the ram and reseat them. not it runs much quicker, can't think of why it would need that, but i have a few fans installed but it was really hot to the touch! could it be the heat that is messing it up. is there an app that measures temp or is that hardware???

---

### Post by DarinB on 2009-08-23
I installed lm-sensor it works i think but by pc has only been running for a few minutes. it is at 40.00C ???
Is there a gui for this????
or screenlet????

---

### Post by DarinB on 2009-08-23
is this normal for a core 2 duo
darin@darin-desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

darin@darin-desktop:~$ 
what is acpitz ?????
the sensors appelet is awesome if it works well

---

### Post by mgmiller on 2009-08-23
> is this normal for a core 2 duo
darin@darin-desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  40 degrees C is ok.   You will notice the last line above that shows the critcal temp for this CPU is 75 degree C.  

My AMD triple core runs at about 44 with a mild overclock without issues.  I would not worry unless it ran in the high 60's, at which point I would look at my CPU cooling options.

> I did it ran thousands of errors for over 3 hours
AH HA!
You say you had thousands of errors in memtest.  There is your problem.  Reseating the ram could have cleaned a little micro-corrosion off the terminals.  You may want to reseat it a few times and then re-run memtest again.  Unless it gives you a totally clean result, then the memory is bad.  Use the newest version of memtest on a current 9.04 live CD if possible.

The age of the machine is irrelevant, memory can go bad at any time with little to no warning.

You are best to make sure there are no dust bunnies anywhere in the machine and all the cooling fans are working and any air filter screens (which may be hidden and not obvious, check your case manufacturer info to be sure) are clean.

Memory can run hot to the touch.  Are you sure the mobo voltages are correct for the ram?  Did you build this machine or buy it from a big name like Dell or HP?

If the mobo voltages are too high, it will make the ram run hot and fail prematurely.  An extra fan aimed at the memory or adding ram sinks (heat sinks for ram) will help to cool the memory.  But this is not normally needed in a machine that is not overclocked.

---

### Post by DarinB on 2009-08-23
a couple of things how can i check the voltage and how to i point a fan at the ram? i have two case fans and each HDD has a fan. fan speeds 5532 rpm and 3013rpm not even sure how to put in a heat sink for ram or what to buy. but the case is a web with a filter i did remove the dust from the filters but i did that only a month ago. please look below so i can better diagnose what is going on

can some one tell me what all the different temperature readings mean.some i obviously know but other i don't like temp1 vcores and difference between cores and cpu
like temp1
vcore1
vcore2
m/b temp
cpu
core0
core1

---

### Post by mgmiller on 2009-08-23
> can some one tell me what all the different temperature readings mean.some i obviously know but other i don't like temp1 vcores and difference between cores and cpu


You have a dual core CPU (core 2 duo), so it has 2 cores, called cpu0 and cpu1 or sometimes core0 and core1.
Some of these vary a bit, but in general:

temp1  Could be the mobo temperature under the cpu or from anther sensor somewhere.
vcore1  voltage to first cpu core
vcore2  voltage to 2nd cpu core
m/b temp  temperature under the cpu
cpu  could tell you the type of cpu
core0 usually the speed of cpu core 0
core1 usually the speed of cpu core 1

If you want to have some fun, right click a blank area of your panel and select "New Panel".  Then right click the new blank panel and select its orientation, I use left, to make it vertical on the left side of my screen.  Also set the size to 39 Pixels.

Now right click it and select "Add to Panel" and look for "Hardware Sensors Monitor" and click it to add it to the panel.  Next look for "CPU Frequency Scaling Monitor" and click to add that to the panel and then click and add a second one to the panel also so there are now 2 of these.

Next, you can go to each of the cpu frequency scaling icons and right click them and select Preferences.  Set one to cpu 0 and the other to cpu 1.  Now you are looking at both cores in real time to see how they speed up and slow down.  You can also left click each core to set its speed to various parameters if this function is supported by your CPU.

The other icons are each right clicked in turn and set to what you want to monitor.  You can set the minimum and maximum temperatures so the color scales work and add and remove various sensors.

Finally, right click a blank area of the new taskbar and select Properties again.

This time you will uncheck "Expand" and put a check mark in "Show Hide Buttons".

Now you have a panel that will slide up and down with the click of one of the hide buttons on either end of the panel.  If you want to see or change something, do a click slide down to open it and then a click to slide it back up out of the way.

Now that the fun is out of the way.  It depends on the mother board as to how to adjust the voltages for the memory or if it's even possible.  

It's done from BIOS.  You have to look around the menus in BIOS to find the memory voltage section.  If it's available, it's usually adjustable by 0.1 volt steps.  You need to know the exact model of ram sticks you have.  Often there is a sticker some where on the ram stick that says exactly what it is.  Then you can google for the correct voltage.  Hopefully, the ram voltage matches what the mobo is set for.  If not, change the setting in BIOS so they match.  

Often, the voltage is specified as a range of voltages.  If that is the case, you can experiment by changing the voltage up or down within the range to see how it behaves.  

In general, higher voltage means more heat, but allows for some overclocking.  Lower voltage is cooler, but if too low can also become unstable.  

Sometimes, the memory will require a voltage that is not available in the BIOS setting.  In that case, some one did not do their homework when they selected the components for the computer.

Adding a ram sink can be done by either glue on or clamp on methods.  

Doing a google search on ram heatsinks will give you a lot of information.

More expensive ram usually comes with a clamp-on style of heat sink already attached.  The cheaper "value ram" is usually naked.  

I would be more interested to know the exact model of ram and what mobo you have to see if the voltage settings are correct or even if they can be changed.

It sounds like you have a lot of case fans and have cleaned the filters and other dustbunnies.  Did you blow the dust out of your cpu cooler also?

With the machine turned off, hold a vacuum cleaner near it and then blast into the cpu cooler with some canned air.  Messy, but effective.

Aren't computers fun?  :lolflag:

---

