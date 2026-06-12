---
title: "CPU temp monitor app?"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by nipsy on 2010-03-24
Hello from a 4 day old Ubuntu user here! I've come across several problems that I've been able to fix simply from reading these forums, so I figured might as well ask away.

I am running Ubuntu 9.10 (dl with wubi installer) on a dual boot with Vista Premium on a Toshiba Satellite laptop. I had to remove all my innards earlier because my laptop was getting so hot it kept shutting down. Well I removed all the dust bunnies that had migrated and multiplied inside, got it back together and am running well again. 

My problem is this: I'd like to get a CPU temp monitor on my panel. But all the ones I've Google'd or read about here are for older versions. CoreTemp won't run on this, and I've looked in my "add to panel" and I don't have the CPU temp monitor app.

Any suggestions? I want to monitor constantly, not every now and then. If you need more info for this question, please let me know, I wasn't sure how much to put.

Thanks in advance!

---

### Post by themusicalduck on 2010-03-24
If you search in the Software Centre for computertemp, there is a package which is apparently an applet for the gnome panel.

Although I installed it, but can't seem to find the applet in the list of applets to add to the panel..

It might work for you on Karmic though, I'm using the Lucid beta.

EDIT: Ah.. but if you press alt+f2 and run ```
pkill gnome-panel
``` it should appear in the list after that!

---

### Post by 3rdalbum on 2010-03-24
If you install the package "lm-sensors", then run:

```
sudo sensors-detect
```

Afterwards, you will be able to run the 'sensors' command to see the current state of all your computer's sensors. You can use this with the 'watch' command to keep a close eye on them:

```
watch sensors
```

---

### Post by nipsy on 2010-03-24
I don't see an option to load "im-sensors" anywhere...

as for the first option, that didn't work either

---

### Post by andrewthomas on 2010-03-24
> **3rdalbum said:**
> If you install the package "lm-sensors", then run:

```
sudo sensors-detect
```
Then you can install sensors-applet from synaptic, right click on your top panel and select add to panel...

---

### Post by andrewthomas on 2010-03-24
> **nipsy said:**
> I don't see an option to load "im-sensors" anywhere...

as for the first option, that didn't work either
  It is 
 **lm-sensors**

```
sudo aptitude install lm-sensors
```

---

### Post by 2hot6ft2 on 2010-03-25
Here's a short version of installing them:
Just open a Terminal (Applications -> Accessories -> Terminal) and type (or copy and paste):

```
sudo apt-get install lm-sensors sensors-applet hddtemp
```

Next, run sensors-detect. Answer y to each one until finished.
```
sudo sensors-detect
```

Now you can also run
```
sudo hddtemp /dev/sda
```
Where sda is your hard drive.
and it will show the temperature of your hard drive if it can.

All temps. are in Celsius by default, but you can change it to F or Kelvin if you want.

adding hdd temp to sensors-applet
> **dcstar said:**
> ```
gksudo gedit /etc/default/hddtemp
```

Make RUN_DAEMON="true", save and reboot.
Finally, restart to load all the sensors (you can choose Logout instead of Restart and it will be much faster). Once back at the desktop, right-click on the top panel and choose "Add to Panel." Select "Hardware Sensors Monitor" and click the "Add" button, then "Close." Right-click on all the sensors applet that appears on the top panel and choose "Preferences." Click the "Sensors" tab. There you can select/de-select all the relevant sensors and adjust their low and high values as well as set alarms if desired.

---

### Post by nipsy on 2010-03-25
sorry, i meant "lm sensors", had a blind moment...trying it now

thanks

alright, finally got my gnome hardware applet running in panel.. I thank ya highly, it only took me 2 hours this time...

---

### Post by Maverick52 on 2010-05-29
Nice & helpful:D

---

### Post by Steveplanetary on 2010-08-04
In the spirit of ubuntu I wanted to add my remarks, since I struggled with this problem for over a week.  At the end of the thread, typing sudo hddtemp /dev/sda did indeed show my hdd temp.  I next typed gksudo gedit /etc/default/hddtemp into the terminal window, but when I pressed the Enter key the cursor moved all the way to the left side of the window on the next line instead of at the end of hydrocarbon@ubuntu:~$.  I then typed Make RUN_DAEMON=true, followed by Enter.  The cursor again moved to the left side of the window, so I typed Make RUN_DAEMON=save, followed by Enter.  Then I typed 'save' Enter.  The terminal window then responded with hydrocarbon@ubuntu:~$, then informed me that Make was not a command.  I then typed Make RUN_DAEMON=save, and the terminal window again informed me that Make was not a command.  So I typed 'save' Enter, and the terminal window informed me that 'save' was not installed, but could be installed.  That didn't seem like something I wanted to do, so I typed RUN_DAEMON=true, then pressed Enter, and the terminal obliged by not objecting to the command.

After logging out then back in again, I followed the instructions step by step.  The problem at this time was that I had two CPU temperature icons, but none for the hard drive.  These two CPU icons corresponded to the two processes libsensors and acpi in Properties, which in turn is found in Hardware Sensors Monitor.  I clicked on the + sign to the left of both these processes, then unchecked one of them.  I don't know how to avoid having two processes that do the same thing.

To get a hard drive icon on the panel monitoring the temperature I had to run sudo dpkg-reconfigure hddtemp.  I was presented with the same window I had seen when going through the process.  After some playing around it occurred to me that to change from the default of No to Yes I just had to use the left arrow key to change which word had the red highlighting.  The rest of the configuring just involved accepting the defaults.  I was also able to choose different, more appropriate icons for the CPU and hard drive temperature readouts.

I hope this is helpful.  It's not an easy thing to write about.

---

### Post by jtarin on 2010-08-04
> **Steveplanetary said:**
> 
I hope this is helpful.  It's not an easy thing to write about.I can imagine it was quite an emotional moment.:-({|=
:p

---

