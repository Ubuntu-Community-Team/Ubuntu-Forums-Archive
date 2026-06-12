---
title: "problem with sounds!!!"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by hoopz23 on 2009-01-07
ok this may be a noob question but i just started using ubuntu 8.10 about a month ago and i am trying to switch to it full time but i have one HUGE problem. As of now I am using Wubi to run ubuntu on my laptop with Vista as the main OS. my problem is that even if i plug in my headphones, the sound still comes out from the laptop's main speakers. Is there some sort of drivers that i need to install? or is it coz i am using wubi? :-k

HELPING ME PLX :icon_frown: :confused:

---

### Post by RobsterUK on 2009-01-08
Have you tried going into Ubuntu's sound settings (double click speaker icon by the clock) you should be able to enable/disable outputs there

---

### Post by linux_tech on 2009-01-08
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type


```
gnome-alsamixer

```
check settings, check headphones if you want to use headphones

---

### Post by hoopz23 on 2009-01-08
i tried using each of the output devices but the sound still comes out from the main speakers :(

maybe it's not recognizing my sound card or smthn? or i need to install something? :confused:

---

### Post by ChildOfMana on 2009-01-08
Double click on the speaker icon in the top right corner of your screen.

In the dialog box that comes up select the 'Switches' tab and ensure there is a tick in the tick-box next to 'Headphones'.

If there is no 'Headphones' option the click 'Preferences' and tick 'Headphones' in the 'Select tracks to be visible' dialogue, then click 'Close'. 'Headphones' should now appear as an option under the 'Switches' tab.

---

### Post by hoopz23 on 2009-01-09
ok stupid question: what if there's no "headphones" under the select tracks to be visible dialouge nor the switches tab?

---

