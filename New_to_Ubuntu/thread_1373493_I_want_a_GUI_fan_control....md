---
title: "I want a GUI fan control..."
date: 2010-01-05
forum: New to Ubuntu
---

### Post by cartisdm on 2010-01-05
I can't seem to find a fan control program with GUI controls.  I have installed GKrellm but that just seems to show my system specs (including temp).  In my windows partition I run **I8KfanGUI** to keep my system at a cool 33 degrees Celsius but my Ubuntu system wants to run around 46 degree and can get up to 53 degrees under normal use.

---

### Post by cartisdm on 2010-01-15
bump?

---

### Post by sliketymo on 2010-01-15
This may help :

[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

---

### Post by cartisdm on 2010-01-19
> **sliketymo said:**
> This may help :

[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

I tried that, but it seems to be made for IBM ThinkPads and I couldn't get it to work.

Blah.  Is there really not a GUI fan control? What do you people do with computers that get hot?

---

### Post by inobe on 2010-01-19
we keep the fan and heatsinks clean and watch temp monitors.

if your system gets hot' it's mainly due to poor maintenance.

install sensors applet in synaptic, it won't control fan speeds, it is a temp monitor, right click panel and hit "add to panel" search for hardware sensors monitor.

side note: i want a gui fan control too.

---

### Post by cascade9 on 2010-01-19
> **cartisdm said:**
> I can't seem to find a fan control program with GUI controls.  I have installed GKrellm but that just seems to show my system specs (including temp).  In my windows partition I run **I8KfanGUI** to keep my system at a cool 33 degrees Celsius but my Ubuntu system wants to run around 46 degree and can get up to 53 degrees under normal use.

All **I8KfanGU** does that ubuntu isnt doing is making your fans run at max speed. 46C is fine at idle, and 53C isnt that hot. 

You might be running 'cool and quiet', that will drop your CPU fan speeds at low load/temps and then push the speeds up at high loads/temps.

---

### Post by inobe on 2010-01-19
i set the fan speed parameters in my system bios.

when it gets hot the fan speeds up automatically, this only happens when the system is encoding large files.

---

### Post by 3rdalbum on 2010-01-19
> **cartisdm said:**
> I tried that, but it seems to be made for IBM ThinkPads and I couldn't get it to work.

Blah.  Is there really not a GUI fan control? What do you people do with computers that get hot?

I let my computer's BIOS adjust the fan speed based on heat.* Adjusting fan power based on the input from a temperature sensor is one of the things that computers do much better than people.

I've never understood the obsession with manual fan control. It's just creating more work for yourself, and inevitably you either end off with too little cooling or more noise than necessary.

*(actually, I have Noctua fans in my computer; they're so quiet that I just have them plugged straight into the PSU and it still makes less noise than a BIOS-controlled Intel stock cooler).

---

### Post by cartisdm on 2010-01-19
> **cascade9 said:**
> All **I8KfanGU** does that ubuntu isnt doing is making your fans run at max speed. 46C is fine at idle, and 53C isnt that hot. 

You might be running 'cool and quiet', that will drop your CPU fan speeds at low load/temps and then push the speeds up at high loads/temps.

I8fanGUI actually allows percentage based fan speed that can be manually set in as many temperature ranges at you would like ie

25-30 degree = 20% fan speed
31-35 degree = 30% fan speed
etc....

> we keep the fan and heatsinks clean and watch temp monitors.

if your system gets hot' it's mainly due to poor maintenance.

I take my laptop apart on a regular basis and every time I do, I make sure to clean out the heat sink and fan assembly so I know that isn't the problem.  at 45 degrees and up my computer will occasionally hang up on heavy programs.  When running around 35 degrees I could run Crysis (not literally) without a hiccup.

> install sensors applet in synaptic, it won't control fan speeds, it is a temp monitor, right click panel and hit "add to panel" search for hardware sensors monitor.

I already have sensors installed, that's how I know my system is getting to the mentioned temperatures.

Well, I guess I I will see if setting my fan controls in the BIOS will make any difference :(

---

### Post by Grenage on 2010-01-19
It's been many years since I needed to dabble with fan speeds, BIOS auto control is excellent these days.

---

### Post by tulcak on 2010-07-09
for those of you who insist on telling folks to set the fan speed in your bios or to use a command line you realize that you are not being helpful at all.  my bios does not allow me to control fan speed.  i don't want to use a command line.  the title of the thread is:  RE:  I WANT A GUI FAN CONTROL.

If you have no useful information why are you posting?

I am still looking for a GUI solution to control my fan speed.  whe I find it, I will post.

---

