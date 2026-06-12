---
title: "Ubuntu efficiency"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by cybuss on 2010-12-24
alright 2 issues, 
how to make games in steam run faster?
and how to make ubuntu go into a very low power mode for downloading and simple things like that
trying to be a bit of green i guess (both for the environment and wallet ;))
i'm on lucid lynx

2 gigs of ram
3.5 GHz processor
7600 nvidia gt
80 gig hard drive (not trying to impress its junk versus these days just so you know what i got)

---

### Post by Ligerzero_942 on 2010-12-24
To save power you may want to turn off your graphics card, though I don't know how to do this.  As for games you may need to mess with the settings, turn the graphics down a notch or something. More ram couldn't hurt either.

---

### Post by cybuss on 2010-12-24
> **Ligerzero_942 said:**
> To save power you may want to turn off your graphics card, though I don't know how to do this.  As for games you may need to mess with the settings, turn the graphics down a notch or something. More ram couldn't hurt either.

yeah graphics turned down
and i most certainly pass the ram requirement for company of heroes
same for the graphics on max in fact before my windows crashed (hence the reason for ubuntu plus i love it)
it was perfectly fine on full graphics in ubuntu however it runs ok in lowest but if the bullets start flying like nuts it gets laggy
also i heard one of my friends say something about bottling or something to make wine programs faster?
and is there a mode that is like standby for windows but can download while in that state?

---

### Post by mikewhatever on 2010-12-24
IMO, turning off the graphics card is an overkill, but the CPU could be scaled down if it supports scaling.

---

### Post by cybuss on 2010-12-24
> **mikewhatever said:**
> INO, turning off the graphics card is an overkill, but the CPU could be scaled down if it supports scaling.

i don't think it does, and its not over-clocked 
thats how it came when i bought it
(cost a lot back then!)

---

### Post by NightwishFan on 2010-12-24
To save power, simply run the settings suggested by powertop. They will revert after every reboot, but just need to be run again. To get powertop, click here:
[Install Powertop]("apt://powertop")

To use powertop, open a terminal and run:
```
sudo powertop
```


As for improving performance, linux systems are fairly optimised by default and schedule tasks pretty fairly. Try killing some spare background tasks like music players etc.

---

### Post by mikewhatever on 2010-12-24
> **cybuss said:**
> i don't think it does, and its not over-clocked 
thats how it came when i bought it
(cost a lot back then!)

Well then, you got what you payed for (literally of cause ;)). It's not exactly green, but it is fast.

---

### Post by owiknowi on 2010-12-24
and if not needed, turn off:
- bluetooth
- wireless (use a cable for downloading)
- some powermanagement (only do set screen go blank after 1 minute and spin down hard disk when possible)
- reduce screen brightness (30% is mostly enough)
- do updates manually, also for all applications who do this automatically 
- purge/uninstall everything you don't need (be careful though)
- for downloading it'helps to have more ram (hdd access will be less)
- use bleachbit - with some care - to clean your os every once in a while

this way i've got a pc witch is pretty basic, 24/7 online and hardly ever hear the fan turning on.

of course this is just personal and it works for me (asus ul50a).

---

### Post by cybuss on 2010-12-24
al-right I don't think anyone understands me here
anyone other then powertop guy, it's  a nifty program but not what i am looking for but a good secondary if i don't find what i am looking for
i don't need more ram i don't want a slower processor i don't want to turn off my card
is there nothing like standby for pc? 
but allows you to download while its in a state of low energy?
also my computer runs very well other then for some reason its laggy on
company of heroes in ubuntu and not in windows
and removing idle files to make a computer faster is a joke (researched myself) and the processor doesn't run too hot (i change the cooling liquid once every 12 months) also it runs at a steady 5-10% usage mostly on the 5%
so the fan isn't going nuts it's silent most the time
i do like the turning down the screen brightness idea
and what's power-management?

---

### Post by NightwishFan on 2010-12-24
Is Company of Heroes a Windows software? If so, then I am sorry to say you need to petition them about their products performance on Ubuntu, to which they will respond they do not support Linux.

The direct reason why it performs less is this piece of software is a vendor locked in product designed only to run on newer versions of Microsoft Windows with the Direct X framework. Wine, which is a 3rd party software for Ubuntu and other Linux distribution is (miraculously) able to run most Windows programs natively. It is not able to run DirectX, so it translates the DX calls to OpenGL. I am unsure if this itself has performance penalties, however of course, not all calls are supported yet. The wine team has to play keep up with Microsoft as well.

If you feel no one is understanding your question, please be more clear. :)

---

### Post by mikewhatever on 2010-12-24
> **cybuss said:**
> ...
is there nothing like standby for pc? 
but allows you to download while its in a state of low energy?
...

No.
Standby is the equivalent of suspending in Ubuntu, but you can't download stuff when suspended. Simply put, your computer doesn't seem to be built for power efficiency. In car terms, it's a Hammer and, however hard you try, it will not become a Fiat Uno.

---

### Post by cybuss on 2010-12-24
> **NightwishFan said:**
> Is Company of Heroes a Windows software? If so, then I am sorry to say you need to petition them about their products performance on Ubuntu, to which they will respond they do not support Linux.

The direct reason why it performs less is this piece of software is a vendor locked in product designed only to run on newer versions of Microsoft Windows with the Direct X framework. Wine, which is a 3rd party software for Ubuntu and other Linux distribution is (miraculously) able to run most Windows programs natively. It is not able to run DirectX, so it translates the DX calls to OpenGL. I am unsure if this itself has performance penalties, however of course, not all calls are supported yet. The wine team has to play keep up with Microsoft as well.

If you feel no one is understanding your question, please be more clear. :)

didn't think that wine has to translate DirectX calls to OpenGl, that's a good enough answer for me why it runs slower on wine then windows
(company of heroes is a tough 1 on graphics)
and thanks for answering mike about the suspend,
and i found power-management, i guess ill call this a wrap if no one knows a way to make wine a bit more efficient in its translations or how to bottle i think he called it?

---

### Post by NightwishFan on 2010-12-24
I suggest you run the game on lower settings if possible.

---

### Post by robert shearer on 2010-12-24
There is a graphical applet for cpu frequency scaling that may be of use to reduce processing calls when not running cpu intensive apps. (like simple downloading) your cpu must support scaling for this to be of use.

Right click on the top panel and select 'add to panel' then scroll down to 'cpu frequency scaling monitor' and add that.

If your cpu doesn't support scaling you will get a pop-up to that effect. Just right click the applet and 'remove from panel'.

If it is supported just click the applet to select the power scheme you want. 'On-demand' should throttle the cpu when not being used for demanding processing but give increased processing performance when needed.

The applet shows the cpu state in real time to allow monitoring.

---

### Post by mastablasta on 2010-12-24
> **cybuss said:**
> and i found power-management, i guess ill call this a wrap if no one knows a way to make wine a bit more efficient in its translations or how to bottle i think he called it?
 
better porcessor, more ram help translate faster. other than that the wine people are working hard on this :-)
 
as for managing power if you download you always use processor (to run the programme) and hard disk (because you write data on it constantly). you cold turn off the monitor and save a bit of power liek that. but as already said computer can't be idle if it is supposed to be doing something. makes sense to me.

---

### Post by sffvba[e0rt on 2010-12-24
For better performance for games in Wine you can install Playonlinux... they often have settings that are optimized for new(er) games... If you run Starcraft 2 with the optimized scripts it is much better than just running straight under wine... It is in software center so give it a go.


404

---

### Post by cybuss on 2010-12-24
alright i been messing with this for awhile now and cant get it to work
maybe i am a simpleton or its tough
those who wish to go on the perilous journey of bottling and debugging this code.
 env WINEPREFIX="/home/basil/.wine" wine C:\\Program\ Files\\Steam\\Steam.exe 

with the instructions of gotsanity in this link
[http://www.uluga.ubuntuforums.org/showthread.php?p=7178372](http://www.uluga.ubuntuforums.org/showthread.php?p=7178372)

post your attempts and ill see if it works!

---

### Post by cascade9 on 2010-12-24
> **cybuss said:**
> i don't think it does, and its not over-clocked 
thats how it came when i bought it
(cost a lot back then!)

Sounds like its a P4 then. 

> **NightwishFan said:**
> To save power, simply run the settings suggested by powertop. They will revert after every reboot, but just need to be run again. To get powertop, click here:
[Install Powertop]("apt://powertop")


Been a while since I tried anythign like this with a P4, but IIRC the module that should be used (p4-clockmod) shouldnt be run with any other governor. 

BTW, P4s have no voltage control, and no real frequency scaling support. So the way that P4-clockmod does its job it with clock modulation (idling every 'x' clocks) which isnt that effective at powersaving, and tends to be slow to react. 

If you treally want to save power a newer system would be a better way to go.

---

