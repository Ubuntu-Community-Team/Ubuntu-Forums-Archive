---
title: "Ubuntu is REALLY slow!"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by _DeepBlue on 2010-02-02
Hello everyone :) 

I'm loving karmic, as it is easy to use and works amazingly.. but it seems to be VERY slow.. I have an ASUS m50 series laptop. I have two partitions, one with XP and one with Karmic. XP has no drivers, as they do not exist for this laptop for older versions of windows, but it is still substantially faster than Ubuntu, and I don't really understand why.. with slow i mean really really slow.. even the music when I boot is very laggy and goes in small crazy bursts.. part of the problem could be the fact that I don't think there are any drivers installed, the only ones that come up in "Hardware Drivers" are the graphics card and software modem. Anyone know how i can make it a bit faster? thanks! :)

also, unrelated problem. A while ago my external HD went mad (its a WD black book). All my folders are still there but they are all empty (they contained 3 years worth of work, music, movies, etc.). I tried data recovery programs, they all say that the files are detected but then it costs £60 to activate and use the software.. Anyone know a free program? many thanks

---

### Post by audiomick on 2010-02-02
Hi.
Drivers shouldn't be your issue. For most things, they are part of the OS. If you have enabled the ones that were offered to you in "hardware drivers", you should be right.

As far as speed goes, how much RAM do you have?

For the data recovery, look here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Flimm on 2010-02-02
I find the only thing that slows Ubuntu down sometimes is GNOME Do. Do you have that installed? Try running System Monitor and see what's taking all the processing power.

The vast majority of drivers on Linux are included by default, the drivers listed in "Hardware Drivers" are only closed-source ones or experimental ones. ("Hardware Drivers" used to be called "Restricted Drivers" but they changed the name for some reason.)

---

### Post by sadaruwan12 on 2010-02-02
For your none related problem use torrentz.com and youcould find a good program with the c**ck.

For the slow down run top in the terminal type top and hit enter that'll give you a good idea about wht is happening with your system. and if you could post the out put of top here we also could give you a better solution.

---

### Post by _DeepBlue on 2010-02-03
Thnks for the replies :)

>               **Re: Ubuntu is REALLY slow!**
 I find the only thing that slows Ubuntu down sometimes is GNOME Do. Do you have that installed? Try running System Monitor and see what's taking all the processing power.


system monitor says that its only Firefox who is being really heavy.. I can confirm, as it is immensely laggy, if I dont restart it every hour or so, if I play videos they lag and it generally becomes SO slow! 

> **audiomick said:**
> Hi.
Drivers shouldn't be your issue. For most things, they are part of the OS. If you have enabled the ones that were offered to you in "hardware drivers", you should be right.

As far as speed goes, how much RAM do you have?

For the data recovery, look here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Am looking at the link atm, thanks :)

Ram shouldn't be an issue, laptop has 3 gigs.. meh


> For the slow down run top in the terminal type top and hit enter
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
26118 leo       20   0  614m 223m  34m S   16  7.4 353:30.51 firefox            
 1520 leo       20   0 44316  21m  13m S   11  0.7 201:58.32 gnome-system-mo    
 1697 root      20   0  577m  56m  19m S    7  1.9 127:03.10 Xorg               
 7562 leo       20   0  2472 1196  884 R    1  0.0   5:48.94 top                
 5804 leo       20   0  191m  71m  51m S    0  2.4   0:49.85 soffice.bin        
 7540 leo       20   0 37064  13m 9616 S    0  0.4   0:16.86 gnome-terminal     
    1 root      20   0  2644 1532 1128 S    0  0.0   0:01.00 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:01.31 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:02.36 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.38 events/0       
```seems to be firefox.. hmm

---

### Post by _DeepBlue on 2010-02-04
Can confirm that the less I restart firefox (1 and a bit hours ago now) the more CPU it takes up. 

```
15386 leo       20   0  463m 188m  35m R  [SIZE=5]** 40**[/SIZE]  6.2  83:23.83 firefox            
10130 leo       20   0  157m  43m  21m S   13  1.4  13:43.38 rhythmbox          
 1520 leo       20   0 47584  24m  14m S   10  0.8 398:22.02 gnome-system-mo    
 1697 root      20   0  578m  57m  22m S    7  1.9 236:32.57 Xorg               
27062 leo       20   0  2472 1188  884 R    1  0.0   0:05.49 top                
 1890 leo       20   0 97184 9744 6956 S    0  0.3   4:59.31 gnome-settings-    
19201 leo       20   0  206m  77m  53m S    0  2.6   3:29.10 soffice.bin        
    1 root      20   0  2644 1532 1128 S    0  0.0   0:01.06 init             
```


EDIT: on the previous post Firefox was running for 350 minutes, and using less cpu but lagging more, on this one 83 minutes and using more than double the cpu, but not lagging.. whats going on!?

---

### Post by semi_fiction on 2010-02-04
Might it have something to do with your CPU frequency scaling?

---

### Post by _DeepBlue on 2010-02-05
> **semi_fiction said:**
> Might it have something to do with your CPU frequency scaling?


meh, i have no idea what that means!

---

### Post by Vignesh S on 2010-02-05
CPU frequency scaling is how fast the CPU is operating at i.e. its clock speed. On that, how fast is your CPU?

To check how fast the CPU scaling is, add the CPU frequency scaling meter to your panel. To do this, right click on the panel, and click on "Add to panel". A dialog box should then come with a list of things that can be added to the panel. Add the CPU frequency scaling monitor to the panel and report how fast the CPU is :)

And while I'm still here (:-)), there is a much easier way to check how much CPU is being used up at the present moment. You can do this by adding the System Monitor applet for the panel via the same method outlined above :) Let us know how it goes

---

### Post by _DeepBlue on 2010-02-05
> **Vignesh S said:**
> CPU frequency scaling is how fast the CPU is operating at i.e. its clock speed. On that, how fast is your CPU?

To check how fast the CPU scaling is, add the CPU frequency scaling meter to your panel. To do this, right click on the panel, and click on "Add to panel". A dialog box should then come with a list of things that can be added to the panel. Add the CPU frequency scaling monitor to the panel and report how fast the CPU is :)

And while I'm still here (:-)), there is a much easier way to check how much CPU is being used up at the present moment. You can do this by adding the System Monitor applet for the panel via the same method outlined above :) Let us know how it goes


It says 2.50 GHz... good or bad thing?

---

### Post by raditzman on 2010-02-05
Try running chrome as your browser, instead of firefox. Also install xubuntu instead of ubuntu. These 2 things will make a difference.

---

### Post by mörgæs on 2010-02-05
Here is what is worth knowing of Firefox

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Vignesh S on 2010-02-06
> **_DeepBlue said:**
> It says 2.50 GHz... good or bad thing?

That is a VERY good thing. Definitely beats the two computers I have here :P

hmmm, I don't get it though. Your computer is so powerful, and even on a computer that has something similar to it (albeit with 4GB RAM), Ubuntu flew on it. 

I wouldn't recommend Xubuntu, though it is worth a shot if you'd like to. It definitely runs faster in my experience, though on a computer like yours, it isn't worth it unless you'd like your system to REALLY fly (I'm talking hardly any lag if at all, but even on my desktop, ubuntu hardly lags at all).

---

### Post by Flimm on 2010-02-06
If it's Firefox causing the problems you might want to try disabling any extensions and add-ons, or switching to another browser.

---

### Post by airtonix on 2010-02-06
> **sadaruwan12 said:**
> For your none related problem use torrentz.com and youcould find a good program with the c**ck.


We don't support piracy here thank you.

---

### Post by leandromartinez98 on 2010-02-06
Are you using visual effects? There cases in the past where the graphic card was not so well supported that the effects were software-controlled, then the whole system became really slow. If you are, try disabling them.

---

### Post by cwalker1960 on 2010-02-06
swap partition???  even with the 3 gigs of ram , sometimes linux needs a place to dump

---

### Post by palmettoj on 2010-02-25
Any new fixes/problems here? I have a similar issue with my machine running slow. I don't think I have any add-ons or extensions with firefox (I'm assuming I would have had to *add* them on to have them installed? -where can I check just to be sure?). I don't have graphic effects enabled (they won't work with my intel integrated graphics, as far as I can tell from reading threads here). My cpu won't support frequency scaling (to the best of my knowledge) and seems to be running fine and not bogging down too much. I have 2G ram and cpu is intel P4.
My problem seems to arise more when I have left the machine on and/or left firefox running and/or locked the screen (or the screen saver has come on by itself after idle). I've noticed when typing in fields that the screen doesn't keep up with my typing. I've also noticed that sometimes sound with youtube videos won't work until I close firefox and open again. (In closing firefox, I usually have to go thru system monitor and end process. It usually shows firefox as "sleeping" under the list of processes).
Does anyone know what's going on behind the scenes to cause these problems?

---

