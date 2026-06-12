---
title: "No good experience with Ubuntu [HELP!]"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by Lone_wolf92c on 2010-03-03
I haven't had much luck with Ubuntu, I've tried it twice now and haven't gotten far enough to enjoy it. I'm hoping that someone here will be able to help me before I pass on Linux entirely and hop back on the Microsoft wagon...

I currently have a new HP laptop, model dv7-3085dx and put Karmic on it. All of the latest updates are on it, and I also got the NVidia drivers as well.

My list of grievances is as follows...

1) After 'waking' from sleep mode, the computer screen is fuzzy and choppy...like a faint layer of static over the display. It still runs fine at this point, but as you might guess i dont want a choppy screen.

2) Every time I reboot my computer, upon startup i'm given a message saying my laptop overheated, to unblock the vents, etc... This happens even if the computer has been running for no longer than 5 minutes so i don't think it is actually overheating.

2a / 3) There are also random lockups that have happened periodically...I label this with the 2a because this could be it overheating i suppose, but I would doubt it.

4) A smaller issue...the wireless light blinks on and off constantly while holding a solid wireless connection.

If anyone could be of some assistance it would be greatly appreciated. This is the second day running Ubuntu on this laptop so i don't think i've manually screwed anything up, but thats probably the case :P

Edit: i'm breaking maybe 8 commandments for putting this in the wrong spot, so hopefully i'll be flamed off to the right spot or a righteous mod will toss me where i belong.

Any suggestions for diagnostics?

---

### Post by ikt on 2010-03-03
Yeah this will probably be moved..

> **Lone_wolf92c said:**
> Any suggestions for diagnostics?

This might be of help:

[http://ubuntuforums.org/showthread.php?t=1415176](http://ubuntuforums.org/showthread.php?t=1415176)

I do recommend if you do decide to go back to windows to report these issues on launchpad, that way hopefully someone will be able to see these issues and possibly fix them. :)

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by Megrimn on 2010-03-03
> **Lone_wolf92c said:**
> 
2) Every time I reboot my computer, upon startup i'm given a message saying my laptop overheated
It *could* be overheating, depending on the environment you have your laptop in.  Our house gets very dusty very fast, no matter how often we clean it.  After I moved in I had to start blowing out my laptop at least once a month to keep it running at its coolest (no pun intended).  My desk is also right over the air vent, which doesn't help in the winter when we have the heat on, so I stick a phonebook over the vent sometimes.


> **Lone_wolf92c said:**
> 
4) A smaller issue...the wireless light blinks on and off constantly while holding a solid wireless connection.
This may just be a manufacturing issue. I've got the dv-9925nr, and a few of my friends have similar models.  We've all had problems with particular lights on the keyboard not always lighting up or coming on and off randomly.  Most of my 'light' issues started happening when I started hauling it to classes and such.  However, the functionality of these indicators and buttons (such as the power on button and the num lock) have not been reduced, and this problem occurs with both windows and ubuntu, so I've pretty much chosen to ignore it. (sorry for the lengthy response)

> **Lone_wolf92c said:**
> 
hopefully i'll be flamed off to the right spot or a righteous mod will toss me where i belong.

Flaming on ubuntuforums is much more scarce than on other forums, though it does exist and is against forum rules.  The community is here mainly to help others, and I should hope you find what you are looking for.  Just remember to be polite :)

---

### Post by overdrank on 2010-03-03
Hi and welcome Lone_wolf92c, Moved to Absolute Beginner Talk

---

### Post by Lone_wolf92c on 2010-03-05
Okay, here's an update of where I am currently...

Ubuntu 9.10, latest updates. I've patched my BIOS to F.13 from F.04 which has fixed the "overheat" message that displayed every time i rebooted...but that is all. All of the other problems still persist, including seemingly random lockups. I originally thought it could be attributed to the overheat but now my fans run just fine and i still get the lockups...

help?

---

### Post by 4Orbs on 2010-03-05
Two suggestions, don't know if they'll fix your problems. Set your screensaver to "Blank Screen Only". Set System Updates to check for updates once per week.

---

### Post by Rasa1111 on 2010-03-05
newb guy here again, thinking he might have a suggestion that will help.. ( but prolly wont) lol...

 See if switching the visual effects in system>preferences>appearance , to "None", will stop the freezing up and sketchy screen. 

 I know on new computers that shouldnt matter, 
but I installed it on my friends new laptop and it was getting all kinda of weird freeze ups and screen glitches until i turned the special effects off. 

sorry if it doesnt help, 
hope it does.
 good luck

---

### Post by tilixibr on 2010-04-22
About the blinking wireless light, I also got that when I upgraded my Ubuntu installed on an external HD, everytime there's activity between the router and laptop.

---

### Post by Jive Turkey on 2010-04-22
The light blinking, I believe is just a different implementation of the driver than what you are used to on windows.  I have an HP zv5460us and it does the same thing.  I think it is set to be more of an indication of activity like the HDD light, or the light on an NIC plug, in ubuntu, rather than an indicator of the wireless radio being turned on or off.

To check the overheating I would install lm-sensors and set it up.  I'll show you how.  Open a terminal and run the following commands:
Install:```
sudo apt-get install lm-sensors
```
Setup:```
sudo sensors-detect
``` this will prompt you for permission to check for various thermal sensors, it is safe to answer yes to everything in my experience.
At he end it will ask you about adding some kernel modules to the /etc/modules configuration file.  I just let it add them automatically.  the easiest way once that is done is to reboot so the modules are loaded automatically.

Once you've rebooted run```
sensors
``` in a terminal. and you should get some output like this:```
:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +31.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +28.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +28.0°C  (high = +74.0°C, crit = +100.0°C)  

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.06 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.90 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.94 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.21 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +0.02 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +3.09 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +2.66 V
fan1:       1427 RPM  (min =   10 RPM)
fan2:       1153 RPM  (min =    0 RPM)
fan3:       1790 RPM  (min =    0 RPM)
fan4:       1584 RPM  (min =    0 RPM)
temp1:       +44.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +29.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

```
I don't really worry unless things start to get up into the 70-80°C.  You'll also notice that some of the stuff is just wrong, that's just me being lazy and not going back to remove the errant modules from /etc/modules.

---

### Post by P4man on 2010-04-22
About the resume issue with your screen; if you make a screenshot, does it show up on it? im sort of curious what it looks like. 

Also, after resuming and looking at your "choppy" screen, try pressing control+alt+F1. That would give you a full screen terminal. Go back to the GUI with control+alt+F7. Is the screen okay now or still messed up?

As for the random lock ups, which is probably the worst part, it may also be the hardest part to diagnose. First things first, have you run a memory test overnight?

edit: oops. This is a somewhat old thread. Not sure if the OP is still following this!

---

