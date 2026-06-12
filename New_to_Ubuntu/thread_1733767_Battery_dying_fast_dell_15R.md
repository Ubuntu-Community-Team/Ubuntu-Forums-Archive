---
title: "Battery dying fast dell 15R"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by amithoward on 2011-04-19
Battery behaves differently between Windows and Ubuntu.:?

I'm attaching four screenshots here. 2 from Ubuntu Studio (10.10) and 2 from Windows 7 (64bit).
I'm using a Dell 15R which is only two weeks old. When I just bought it I installed Ubuntu 10.10 (64 bit) and it had no problems with battery (well not as much). But since the upgrade to Ubuntu Studio - after I unplug the charger from the fully charged battery, it shows only 1 hr remaining and 88% remaining with 91% capacity. The system time on the screenshots show that there was no time interval at all between the two pictures. And the battery performance on Windows is excellent. Can someone help?

Here are the screen shots - 
**Ubuntu (Charged and Discharge Shots)**
1. Charged
[IMG]http://www.imageurlhost.com/images/5a7ewythzdbpu8mb3vjz.jpg[/IMG]
2. Discharging
[IMG]http://www.imageurlhost.com/images/97ga4gj7wewn8yxsvmp.jpg[/IMG]

**Windows (Charging and Discharging Shots)**
1. Charged
[IMG]http://www.imageurlhost.com/images/gkhlj58298c0srq82k7y.jpg[/IMG]
2. Discharging
[IMG]http://www.imageurlhost.com/images/3ditdbh7hk8y0zmj5a7.jpg[/IMG]

[I]My system configuration is:
Operating System: Windows 7 Home Basic 64-bit
           Language: English (Regional Setting: English)
System Manufacturer: Dell Inc.
       System Model: Inspiron N5010
               BIOS: BIOS Date: 01/09/10 15:17:22 Ver: 08.00.10
          Processor: Intel(R) Core(TM) i5 CPU M 480  @ 2.67GHz (4 CPUs), ~2.7GHz
             Memory: 4096MB RAM
Available OS Memory: 3958MB RAM
          Page File: 1491MB used, 6424MB available

Graphics Card - 

          Card name: ATI Mobility Radeon HD 550v
       Manufacturer: ATI Technologies Inc.
          Chip type: ATI display adapter (0x9480)
           DAC type: Internal DAC(400MHz)
     Display Memory: 2740 MB
   Dedicated Memory: 1016 MB
      Shared Memory: 1723 MB
       Current Mode: 1366 x 768 (32 bit) (60Hz)[/I]
:guitar:

---

### Post by mynameisnotbob on 2011-04-19
It's more than possible that the mistake is in one of the displays, not actual battery time. Try actually seeing how long the battery lasts. Time estimates for things, in Windows in particular, are often quite inaccurate.

---

### Post by amithoward on 2011-04-20
> **mynameisnotbob said:**
> It's more than possible that the mistake is in one of the displays, not actual battery time. Try actually seeing how long the battery lasts. Time estimates for things, in Windows in particular, are often quite inaccurate.

I did try the actual battery backup in both Windows and Ubuntu. Turns out both the estimations are accurate. The full charged battery does last only 1 hour on Ubuntu and around 2:45 hrs on Windows. Even though I run heavier programs on Windows compared to Ubuntu.:roll:

---

### Post by manishraj2011 on 2011-04-20
> **amithoward said:**
> I did try the actual battery backup in both Windows and Ubuntu. Turns out both the estimations are accurate. The full charged battery does last only 1 hour on Ubuntu and around 2:45 hrs on Windows. Even though I run heavier programs on Windows compared to Ubuntu.:roll:
As per my observation and Also as reported by various Ubuntu Community users, the battery utilization is fairly high in Ubuntu as compared to Windows.....

May be it is due to some bug.....but till now in any of the threads I have not seen any satisfactory information....


But yes one thing that I want to say is that the **Capacity** of battery as shown by **Ubuntu Studio Screenshot **is **not good**....


The **Dell Inspiron Mini 1012 **which I am currently using shows **99.6 %** capacity after one year of use.... So try consulting Dell Customer Care regarding your battery and do tell us what they say...

---

### Post by amithoward on 2011-04-20
> **manishraj2011 said:**
> As per my observation and Also as reported by various Ubuntu Community users, the battery utilization is fairly high in Ubuntu as compared to Windows.....

May be it is due to some bug.....but till now in any of the threads I have not seen any satisfactory information....


But yes one thing that I want to say is that the **Capacity** of battery as shown by **Ubuntu Studio Screenshot **is **not good**....


The **Dell Inspiron Mini 1012 **which I am currently using shows **99.6 %** capacity after one year of use.... So try consulting Dell Customer Care regarding your battery and do tell us what they say...

That's what I read too. But 2 hours difference is quiet a hurt. I was worried about the battery capacity too but according to Dell's battery meter (cross checked with Window's) the battery shows full capacity when fully charged. So I'm guessing it has to be a problem with Ubuntu and Dell will just ask me to quit using Ubuntu (since they "recommend" Windows 7 :lol: ) I also read at places that Ubuntu is incapable to turn off unused hardware... unlike Windows and sometimes it even drains battery while the computer is shut down. Don't know for sure but that's what I read.

Anyway - still looking for a fix coz I haven't seen a lot of people having this problem. There has to be some tweaking options. ;-)

---

### Post by manishraj2011 on 2011-04-20
> **amithoward said:**
> That's what I read too. But 2 hours difference is quiet a hurt. I was worried about the battery capacity too but according to Dell's battery meter (cross checked with Window's) the battery shows full capacity when fully charged. So I'm guessing it has to be a problem with Ubuntu and Dell will just ask me to quit using Ubuntu (since they "recommend" Windows 7 :lol: ) I also read at places that Ubuntu is incapable to turn off unused hardware... unlike Windows and sometimes it even drains battery while the computer is shut down. Don't know for sure but that's what I read.

Anyway - still looking for a fix coz I haven't seen a lot of people having this problem. There has to be some tweaking options. ;-)
After slight googling, I came across this:

[http://www.ubuntugeek.com/ibam-the-intelligent-battery-monitor-for-laptops.html](http://www.ubuntugeek.com/ibam-the-intelligent-battery-monitor-for-laptops.html)

May be it can be for some help for you.

---

### Post by mynameisnotbob on 2011-04-20
You could try disabling some background applications that you don't need...but be careful. You could delete something important.

---

### Post by amithoward on 2011-04-20
Ok. This is where I am now. I tried IBAM and it keeps telling me "no apm data available". So I don't know what went wrong there. I even tried to make Ibam as a launcher (someone posted it on a blog) but it didn't work either.
Windows 7 has a new option called 'powercfg' though command prompt and it gives you the exact details of the battery.
This is what I got -
&#65279;[I]Battery:Battery Information
Battery ID: 2063SMPDELL 8NH550B
Manufacturer: SMP
Serial Number: 2063
Chemistry: LION
Long Term: 1
Design Capacity: 48840
Last Full Charge: 44722[/I]

The amount of battery life is calculated like this -
44722/48840*100 = **91.568386568**
So the capacity of the battery is calculated good by Ubuntu. Which means I should contact Dell coz my laptop is only 2 weeks old. :s Or is this is the normal capacity of a new battery? I don't know if it should be 100%. Any ideas?

I'll see what services and programs are running on the background that are sucking the battery life on Ubuntu. Hopefully I won't kill anything crucial. :D

---

### Post by mynameisnotbob on 2011-04-20
91 shouldn't be normal for a two week old laptop. By the way, here's a list of things that run on startup you probably don't need.
Evolution Alarm Notifier-unless you use evolution
SSH Key agent-unless you connect using it
Visual Assistance-you aren't blind, are you?
Ubuntu One-unless you synchronize your files on a regular basis

---

### Post by amithoward on 2011-04-21
I disabled the above mentioned and also a few more from BUM (boot up manager). From all this I was able to get 30 mins extra only. Also stumbled upon something called Laptop Mode. But it is going over my head. Still very new to Linux terminology and scared to mess with the scripts and all. So if anyone has messed around with LM then it would really be helpful. For what I've read it doubles up the battery life 2 times.

---

### Post by manishraj2011 on 2011-04-21
> **amithoward said:**
> I disabled the above mentioned and also a few more from BUM (boot up manager). From all this I was able to get 30 mins extra only. Also stumbled upon something called Laptop Mode. But it is going over my head. Still very new to Linux terminology and scared to mess with the scripts and all. So if anyone has messed around with LM then it would really be helpful. For what I've read it doubles up the battery life 2 times.
I am not sure what is laptop mode exactly, but whatever I found in the thread [http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867) , it seems like it is something related to CPU frequency scaling.

I am not so involved in messing up with codes..... so I came up with following solution which I accidently saw.

Steps:- 

1) Right-click  the top-most/lower bar/panel and select **add to panel**.

2) From the list you get, select and add **CPU frequency scaling monitor. **You have to add it same number of times as your CPU cores (i.e. 2 for Dual-core processors ).

3) You can change the CPU monitored by right-clicking the icons and selecting the preferences.

4) If you single click the Icon you can see various option like Conservative, On-demand, Performance and Power-save.

There is even a help manual for this application.

---

### Post by mynameisnotbob on 2011-04-21
try turning down the brightness...
also, go to power manager. its in system preferences.

---

### Post by aliasandy on 2011-04-21
hmm, i have the 15r as well dualbooting ubuntu and win7, and mine dies quickly on ubuntu because i had to turn ACPI off, how did you get it to boot with ACPI, or is yours also off

---

### Post by amithoward on 2011-04-22
I tried the CPU Frequency Scaling monitor and set both the CPUs to PowerSave mode which keeps them on 1.20Ghz each. I don't run heavy programs on Ubuntu so that is enough for me to surf the net and multimedia stuff. But I didn't see any difference in the battery life. :s I already have my brightness turned down to 20% only while running on Battery. I've disabled bluetooth, saned, speech dispatcher, timidity, ubuntu one, evolution notifications, printer queue applet and visual assistance. Which is how I got the extra 20 mins.

ACPI is turned on. I found it after installing Boot-Up Manager (search synaptics pm. It's also called BUM). Click Advanced check box in the bottom. Check under services tab. Right click and make it to start or stop etc. So I'm not sure if it does make much of a difference.

---

### Post by manishraj2011 on 2011-04-22
> **amithoward said:**
> I tried the CPU Frequency Scaling monitor and set both the CPUs to PowerSave mode which keeps them on 1.20Ghz each. I don't run heavy programs on Ubuntu so that is enough for me to surf the net and multimedia stuff. But I didn't see any difference in the battery life. :s I already have my brightness turned down to 20% only while running on Battery. I've disabled bluetooth, saned, speech dispatcher, timidity, ubuntu one, evolution notifications, printer queue applet and visual assistance. Which is how I got the extra 20 mins.

ACPI is turned on. I found it after installing Boot-Up Manager (search synaptics pm. It's also called BUM). Click Advanced check box in the bottom. Check under services tab. Right click and make it to start or stop etc. So I'm not sure if it does make much of a difference.
With none of the options working for you and the Windows 7 also showing 91 % battery status for full charge, I think now its the time for you (amithoward) to contact the Dell Customer Care for battery replacement. Just check out what they have to say on this.

In the mean time, we can search and try some more options.

---

### Post by amithoward on 2011-04-22
I would definitely contact Dell coz I have a Asus Netbook which is around 1.5 yr old and it's battery capacity is still 98% :/ But my problem is not so much the capacity of the battery but the difference of battery backup between Windows 7 and Ubuntu. Why is my 91.6% capacity battery is giving me over 3 hours (in power saving mode) on Windows 7 and only 1.5 hours on Ubuntu 10.10 (with the least power consumption settings according to my knowledge). This is not something that Dell will fix but Ubuntu should. :(

---

### Post by ercskala2012 on 2012-01-01
I have used Ubuntu for 3 years now. When i used windows my battery can run for 6 Hours when i put Ubuntu it runs for 30 Minutes. Why is it doing this.

---

