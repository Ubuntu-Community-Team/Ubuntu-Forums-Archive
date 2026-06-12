---
title: "Unable to change refresh rate.."
date: 2009-09-11
forum: New to Ubuntu
---

### Post by fr0g on 2009-09-11
I'm running Jaunty on a Gateway Tablet Ta6..recently I tried to use a secondary monitor, just for kicks but didn't like it so I disconnected it.  Ever since, I am unable to alter the refresh rate on my lap top, it's stuck permanently at 60hz and it's really bothering me, another thing..not sure if it's related but I cannot play videos since this incident either.
I did find some info about editing the xorg.conf file but cannot find the correct HorizSync and VertRefresh numbers for my laptop..

Any suggestions will be appreciated,
Cheers.

---

### Post by wojox on 2009-09-11
```
HorizSync     30.0 - 130.0 # Safe for LCD's
VertRefresh   50.0 - 100.0 # Safe for LCD's and most CRT's.
```

Put this in Section "Monitor"

---

### Post by fr0g on 2009-09-11
thanks for the reply wojox
mm not too far off what the values I was trying though..
applied the ones you suggested, saved, and restarted.
Still nothing..

Must be something else if those are safe for the majority of monitors, any ideas??

---

### Post by fr0g on 2009-09-11
Please someone give me a hand with this, I need the use of my computer running as it should again..

---

### Post by RabbitWho on 2009-09-11
I never noticed refresh rate making much performance difference (except to give me a headache) you could try swapping to xubuntu? 

Sorry I can't help you with how to change the refresh rate as it won't alter from 60 on mine either.

---

### Post by fr0g on 2009-09-11
yes, that..and everything is slower and laggier..
what is xubuntu? 
so you've never gotten yours to change either, how long did you attempt?
it's odd because everything was just dandy before the other day with the second monitor..

---

### Post by RabbitWho on 2009-09-12
> **fr0g said:**
> yes, that..and everything is slower and laggier..
what is xubuntu? 
so you've never gotten yours to change either, how long did you attempt?
it's odd because everything was just dandy before the other day with the second monitor..

I didn't really attempt, I just clicked on it and I saw there were no other options, but for me it's the se same in vista, so it might just be the computer. 

Xubuntu is the same ubuntu but with Xfce instead of Gnome, which means it's lighter and faster, and as far as I know it comes with a few different default programs, but you can install the same programs as you can have on ubuntu if you like anyway. 
The system requirements are much lower than with Ubuntu. oh gtg! i'll finish later
[]("http://en.wikipedia.org/wiki/Desktop_environment")

---

### Post by Wim Sturkenboom on 2009-09-12
Are you sure that you could change it to a higher value before you started exercising with your external monitor? 60Hz is a very normal maximal vertical refresh rate at max resolution for laptops. It is the max refreshrate that I get on my Acer Aspire one (1024x600) and Fujitsu Siemens (1280x800). Only when I lower the resolution I can get higher refresh rates.

Others might be able to confirm if their laptops can do a max resolution on the laptop screen that is significantly higher than 60 Hz.

There is a relationship between the resolution and the refreshrate (basically laying in the required bandwidth). A higher resolution will lower the maximum usable refreshrate. That relationship applies to the electronics in both the monitor and the screen.

---

### Post by fr0g on 2009-09-12
Wim, well I had it my refresh rate higher with the highest resolution earlier, before attempting to use the external monitor..but now, no longer using it I cannot obtain that refresh rate. I can lower the res and then adjust it, but frankly the other resolution options look wretched and I can't stand them haha.

RabbitWho, interesting, I like the sound of it..especially because my laptop cannot even run compiz without blacking out menus and windows when I select/open them. Would I have to do a complete reformat or is it possible to just "switch" over?

---

### Post by RabbitWho on 2009-09-12
I think there's a few graphical things you can do with Gnome that you're not able to do with Xcfe, "no eye candy" someone said. so if you like compiz maybe you won't really like Xubuntu..
Compiz could be what's slowing down your computer as well? 

You could always run Xubuntu from a live cd first and see how you like it, there is a code to switch from Gnome to Xcfe (I don't know it, but you'll find it somewhere), but i heard it works like a reinstall and you loose all your stuff anyway, so do back up!

---

### Post by fr0g on 2009-09-12
Ah, right. Well no, I'm not using compiz currently. That's one reason why I had to reinstall earlier because i tried using it and like I said, everything went black that I opened so I was unable to disable compiz hah. Looks like i might just have to back up and reinstall again though..haven't found anyfix for what's happening. Thanks for the suggestion, might consider xubuntu.

---

### Post by Wim Sturkenboom on 2009-09-14
You can try in a terminal

```

$ sudo dpkg-reconfigure &#8211;phigh xserver-xorg

```

---

