---
title: "Application window dims for no obvious reason"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by e_james on 2009-10-19
I have an eeepc 901 with ubuntu 9.04 installed since about May 2009. I don't remember noticing the problem in the first couple of months but, for the last 2 months or so, the current application window often dims for a short time - not the whole screen, just the window. It happens with Synaptic and with Firefox at least. It normally occurs immediately after I initiate some change, as if the application is trying to tell me that it has to work harder than usual at that time. I suspect it is a consequence of some other software I have installed or maybe a recent update. 

Any suggestions?

---

### Post by phidia on 2009-10-19
Open a terminal window, type "top" press enter-then open the application(s) that have been showing you the greyed out look. Observe how much of your cpu load they are taking in top. Hope that helps.

---

### Post by e_james on 2010-06-14
I still have no definitive explanation but I realised a few days ago that the symptoms might be consistent with the SSD wearing out. Any comments?

---

### Post by Peter09 on 2010-06-15
Sometimes the application may dim because its doing something over the internet, Synaptic for instance may dim while accessing repositories - is it only when you access the internet?

---

### Post by e_james on 2010-06-15
At the time I wrote post #3 I had just experienced a series of dimming events although they seemed to be diminishing in frequency. I have just now done some experiments involving drive access and internet access without seeing a single dimming incident until I activated Movie Player by a selection of video files. The Movie Player window dims for less than 1 second just before the playback starts. On previous occasions the dimming has lasted for several seconds, sometimes for so long that I have forced Movie Player to quit (Not responding).

There is another situation which might be related. I have a 5K text file which I open wth Gedit from time to time. The time to open it varies from about 3 seconds to about 30 seconds. Today it is about 4. There is no associated dimming but then the window only appears as the file details are displayed.

I have been reading about SSD characteristics and the "wear levelling" procedure could be an explanation for the hesitation / dimming. I have seen the window dimming on another laptop with a standard HDD and I think it may be the built-in Ubuntu indicator for "Application not responding". Comments anyone?

---

### Post by JBA2337 on 2010-09-26
> **e_james said:**
> I have an eeepc 901 with ubuntu 9.04 installed since about May 2009. I don't remember noticing the problem in the first couple of months but, for the last 2 months or so, the current application window often dims for a short time - not the whole screen, just the window. It happens with Synaptic and with Firefox at least. It normally occurs immediately after I initiate some change, as if the application is trying to tell me that it has to work harder than usual at that time. I suspect it is a consequence of some other software I have installed or maybe a recent update. 

Any suggestions?
I hope that someone will eventually answer your question, because I have the exact same problem, but with Ubuntu 10.04. When a window dims I can no longer interact with anything in the window. This is most irritating, since it prevents me from finishing anything I was doing in that window.

JBA2337

---

### Post by jtarin on 2010-09-26
Making a list of which aplications this is happening in would be helpful in trying to track down the phenomena. Are you sudo or user when you do this?

---

### Post by JustinR on 2010-09-26
Hi,

If you mean dimming as in the window 'greying out' then it's a Compiz setting that dims the window when it becomes unresponsive.

This is normal - you shouldn't be worried about it unless its a major distraction.

If it bothers you, then you could turn off Compiz - System > Preferences > Appearance > Desktop Effects set to 'Off'.
If it bothers you but you still want compiz, then go to Applications > Accessories > Terminal:
```

sudo apt-get install compizconfig-settings-manager

```
System > Preferences > CompizConfig Settings Manager
Then: Scroll down to 'Effects' > 'Fading Windows'. Uncheck the box called 'Dim unresponsive Windows'

---

