---
title: "Weather not showing on clock"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Legeril on 2010-10-14
My clock displays time / date a seems to function correctly, but even though I have added a location and the options to display weather conditions and temperature are checked it does not display them. I have an icon I've added to my upper panel but I would prefure to use the clock and save the space for other icons.

Is this a common problem? Has anyone fixed this before?

---

### Post by jtarin on 2010-10-14
Possibly...the clock applet will NOT show your weather/temp unless the timezone in your location matches the TIMEZONE variable set for your system (in /etc/rc.conf).  For me, I had to change mine from 'America/Los Angeles' to 'PST8PDT', which is what I had in my rc.conf.  After that, everything worked as expected.

---

### Post by amjjawad on 2010-10-14
> **Legeril said:**
> My clock displays time / date a seems to function correctly, but even though I have added a location and the options to display weather conditions and temperature are checked it does not display them. I have an icon I've added to my upper panel but I would prefure to use the clock and save the space for other icons.

Is this a common problem? Has anyone fixed this before?

Do you have Ubuntu 10.04 or 10.10?

In my case (Ubuntu 10.04), I have to be connected to the Internet so that my Weather function could work probably. What I've done to add Weather was:
Directly after I installed Ubuntu 10.04, I clicked on the Time and Date then I clicked on Edit (Location). I set my location where I'm now and everything was and still working as long as I'm connected to the Internet. There's no problem at all.

I'm not sure what version/release of Ubuntu do you have but as I said, I have 10.04 :)

---

### Post by Legeril on 2010-10-14
Yes I am using 10.04, although I am in a small city in China called Jining. This city isn't on the list of cities given, is there a way to add my city? Maybe that will fix the problem then

---

### Post by jtarin on 2010-10-14
> **Legeril said:**
> Yes I am using 10.04, although I am in a small city in China called Jining. This city isn't on the list of cities given, is there a way to add my city? Maybe that will fix the problem then
Setting the latitude and longitude will overcome that.
Example: Lat:43.116669 North   Longitude:131.933334 West

---

### Post by irv on 2010-10-14
I am using 10.10 and I have the same problem. Here are all my setting.
Time by no weather.
[ATTACH]172301[/ATTACH]
Edit: I don't even have a /etc/rc.conf

---

### Post by Legeril on 2010-10-14
I tried the Longitude and latitude option but still no fix, I'm making this thread as solved. I just jiggled a few icons around so now it 'looks' like my clock is doing what it's supposed to

---

### Post by Netscannur on 2010-10-15
I think they may be having an issue with the weather servers... Weather was working just fine when I first installed 10.10 and then it went down a couple of days ago.

---

### Post by irv on 2010-10-15
I gave up on using weather with the clock an am using screenlets. See screen shot.
[ATTACH]172415[/ATTACH]

---

### Post by MAkerboom on 2010-10-23
I've found out that after I enable 'Automatic Time Synchronization' (which installs NTP) the problem is solved and the weather icon & temp. next to the date/time are displayed.

How to enable 'Automatic Time Synchronization':
[http://www.watchingthenet.com/enable-auto-time-synchronization-in-ubuntu-and-kubuntu.html](http://www.watchingthenet.com/enable-auto-time-synchronization-in-ubuntu-and-kubuntu.html)

---

### Post by mista-ace on 2010-10-23
hey after you set the place click on the time and go to Locations and then click on Set .. it will work... hope!

---

### Post by yorgos1 on 2010-10-30
> **jtarin said:**
> Possibly...the clock applet will NOT show your weather/temp unless the timezone in your location matches the TIMEZONE variable set for your system (in /etc/rc.conf).  For me, I had to change mine from 'America/Los Angeles' to 'PST8PDT', which is what I had in my rc.conf.  After that, everything worked as expected.

Had the same problem with my ubuntu (10.10), followed your advice and corrected the problem, Thanks!!!

---

### Post by jtarin on 2010-10-30
> **yorgos1 said:**
> Had the same problem with my ubuntu (10.10), followed your advice and corrected the problem, Thanks!!!
Your welcome.:)

---

### Post by Knatchwa on 2010-10-31
Was having the same problem for a few days, when I looked up the exact coordinates and modified the Longitude and Latitude - I found it working again. That was after closing the clock and adding it again to get it working.

---

### Post by kitno84 on 2011-02-02
> **mista-ace said:**
> hey after you set the place click on the time and go to Locations and then click on Set .. it will work... hope!

worked for me, thanks.

ubu 10.10

---

### Post by astraluxkl on 2011-05-09
> **Legeril said:**
> My clock displays time / date a seems to function correctly, but even though I have added a location and the options to display weather conditions and temperature are checked it does not display them. I have an icon I've added to my upper panel but I would prefure to use the clock and save the space for other icons.

Is this a common problem? Has anyone fixed this before?
[B]You have 2 solutions:

        1.[/B] You can use **"Weather Applet"** from  
***                 <Gnome-panel>** right click*
                 **<Add to Panel>*** click*
[I]                 .. select weather Applet and _use It_
[/I]
        **2.** Install **"[B]indicator-weather**"
                                                   [/B]_*After installing **[B]indicator-weather**[/B]*__* you can find it in*_[I]: 
                                                   "Applications[/I] » Accessories » *Weather Indicator*"
                 *_**Ubuntu**__** 11.04**_*

                        Weather Indicator has  been accepted in the Natty repositories.
                        You can find and Install *‘indicator weather’* the the Ubuntu Software Centre.
 
                 _***Ubuntu 10.10***_
                 Weather-Indicator PPA                         The indicator can be installed in Ubuntu 10.10 via the official team PPA.
                        Simple add **ppa:weather-indicator-team/ppa **to your software sources
                        or run the following two commands in a new Terminal session:

 
[LIST]
[*]**sudo add-apt-repository ppa:weather-indicator-team/ppa **
[*]**sudo apt-get update && sudo apt-get install indicator-weather **
[/LIST]
[COLOR=Black]At last you can add _***[B]indicator-weather**[/B]*_ it in "System»Preferences»Autostart Applications"[/COLOR]

---

