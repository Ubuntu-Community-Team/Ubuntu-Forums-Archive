---
title: "Docky -- a simlpe &quot;How to&quot;"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by jrandolph on 2010-02-24
Someone asked in a PM me to tell them how to get and set-up Docky 
So I thought I would give the instructions to everyone who may want this "screen dock"....

open a terminal and type the following 3 commands:

```
sudo add-apt-repository ppa:docky-core/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install docky
```

go to the menu --> Applications --> Accessories --> Docky
it should start up
if you have a menu at the bottom of your screen right click delete that
click 'Docky' (left most icon)
for theme select I selected 'Smoke' (you may have to click close and then reopen)
Click the 'Start When Computer Starts'
As far as hiding options use whatever works for you
Choose what you want displayed on the Docklets tab
Customize to your own preferences or needs


i added weather, cpu monitor, clock, and gmail (make sure to right click them and set them up after added)
if you want to get rid of an icon from docky, just click it and drag and drop it off somewhere (like your desktop)
you can also drag new icons/applications onto the docky to add them
you can click things like the weather, cpu monitor, clock a few times to get different information
you can play around with the other options it has

Hope this helps kolo-01

---

### Post by kolo-01 on 2010-02-24
hi, thanks a lot for your reply, but i have since installed docky, along with some of the other docks, docky is definitely the best but is incredibly temporamental and unstable needing regular 'force quits', im not sure why this is as it can run quietly in he background for hours not taking up any resources but then goes straight to 70%..have you heard of this problem or know of any way to make it more stable?

---

### Post by n0dix on 2010-02-24
@jrandolph thanks for the mini How to.

---

### Post by jrandolph on 2010-02-24
I honestly have no issues with it
I cant seem to think of why it would take up hardly any at all
mine has never gone beyond mayby 5% 
I have had to force quit but that has only happened when my computer shutdown unexpectedly and upon reboot docky doesnt respond

Sorry if I am no help on that 
I will see if I can ask my brother - he is originally who told me about it

@n0dix - I hope you like it - IMO its the best dock

---

### Post by tom.swartz07 on 2010-02-24
> **kolo-01 said:**
> hi, thanks a lot for your reply, but i have since installed docky, along with some of the other docks, docky is definitely the best but is incredibly temporamental and unstable needing regular 'force quits', im not sure why this is as it can run quietly in he background for hours not taking up any resources but then goes straight to 70%..have you heard of this problem or know of any way to make it more stable?

I have the same problem, and the only thing that I could narrow it down to is this;

If you have a lot of applets running on docky, then it will tend to chew up your CPU once in a while. Im not sure if its a bug, per se, but I could check and see if they have a fix for it coming in the works.

Right now, I have (besides the launchers/open windows) weather, gmail, bookmarks and mounted drives applets running. I would say that maybe once a day I need to re-start docky because it gets a little runaway


Anywho- hope this helps

---

### Post by jrandolph on 2010-02-24
maybe [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/395190")will help

---

