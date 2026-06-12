---
title: "new to ubuntu, lots of questions!!"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by abhishek39 on 2011-04-16
i am totally new to ubuntu, and have a lots of questions, plz help
[i use ubuntu 10.10]
(1)why sometimes my pc freezes during shut down?
(2)why cant i enable my visual effects to at least normal? whenever i do that the screen flashes some times, and then displays something like this- visual effects could not be enabled.
(3)a don't hav network connection on my pc i use net on other computer,
how can i download wine 1.2 and install it.

---

### Post by vivek.pandey on 2011-04-16
> **abhishek39 said:**
> i am totally new to ubuntu, and have a lots of questions, plz help
[i use ubuntu 10.10]
(1)why sometimes my pc freezes during shut down?
(2)why cant i enable my visual effects to at least normal? whenever i do that the screen flashes some times, and then displays something like this- visual effects could not be enabled.
(3)a don't hav network connection on my pc i use net on other computer,
how can i download wine 1.2 and install it.

about your visual effects normal is the default visual setting so how 
1) you need to update your system..try it and see if it works
2)cum you dont have it?  and if it is not checked then what is checked?
3)why cant you connect to net from pc .. getting some errors or you dont wanna have on it?

---

### Post by abhishek39 on 2011-04-16
> **vivek.pandey said:**
> about your visual effects normal is the default visual setting so how 
1) you need to update your system..try it and see if it works
2)cum you dont have it?  and if it is not checked then what is checked?
3)why cant you connect to net from pc .. getting some errors or you dont wanna have on it?

for your first comment, i dont hav a net connected to my pc
fr d 2nd, i cant understant, or may be you mean that which visual effect is enabled in my pc, the answer is "none" is selected
fr the 3rd, very simple, i dont hav a modem, eiher i use net on my friens pc or in cafe.

---

### Post by Paqman on 2011-04-16
> **abhishek39 said:**
> 
(1)why sometimes my pc freezes during shut down?


It shouldn't. What model PC do you have, and what version of Ubuntu is it running?

> (2)why cant i enable my visual effects to at least normal? whenever i do that the screen flashes some times, and then displays something like this- visual effects could not be enabled.

You probably need to install drivers for your graphics card.

> 
(3)a don't hav network connection on my pc i use net on other computer,
how can i download wine 1.2 and install it.

Installing packages offline is a bit of a pain. You can get Wine 1.2 from [this page]("http://packages.ubuntu.com/maverick/wine1.2"), but you'll also need to have ALL the other packages with a red dot installed to be able to install Wine.

Probably the easiest thing to do would be:
[LIST=1]
[*]Install Wine on the other machine
[*]Copy the entire contents of /var/cache/apt/archives to a memory stick or a CD
[*]Copy all of those files into /var/cache/apt/archives on your offline machine
[*]Open Synaptic, hit reload and install Wine.
[/LIST]

---

### Post by vivek.pandey on 2011-04-16
> **abhishek39 said:**
> for your first comment, i dont hav a net connected to my pc
fr d 2nd, i cant understant, or may be you mean that which visual effect is enabled in my pc, the answer is "none" is selected
fr the 3rd, very simple, i dont hav a modem, eiher i use net on my friens pc or in cafe.

sorry for the weirdest possible answers i gave

ok for visual effects you need drivers... you need to activate the ati drivers in system->administration-> additional drivers... and you need net for that as far as i know...i would suggest you to connect your pc once to net and update+get the drivers 

to install wine offline you can download its tar file and the n extract and install on your pc

---

### Post by abhishek39 on 2011-04-16
> **Paqman said:**
> 


but you'll also need to have ALL the other packages with a red dot installed to be able to install Wine.


[/LIST]

what are you saying, 
what do you mean by "you'll also need to have ALL the other packages with a red dot installed to be able to install Wine." 
does this mean that i have to download and install all of those more than 25 package individually.
this cant be done so easiy, plz help

---

### Post by abhishek39 on 2011-04-16
> **vivek.pandey said:**
> sorry for the weirdest possible answers i gave

ok for visual effects you need drivers... you need to activate the ati drivers in system->administration-> additional drivers... and you need net for that as far as i know...i would suggest you to connect your pc once to net and update+get the drivers 

to install wine offline you can download its tar file and the n extract and install on your pc


i just followed the steps in by pc, in the additional drivers option 
the box is empty saying "no proprietary drivers are in use on this system"

and, where can i find the tar file for wine. plz answer clearly and step wise.

---

### Post by vivek.pandey on 2011-04-16
just try following this link for wine
[http://ubuntuforums.org/showthread.php?t=1383693](http://ubuntuforums.org/showthread.php?t=1383693)

---

### Post by Paqman on 2011-04-16
> **abhishek39 said:**
> what are you saying, 
what do you mean by "you'll also need to have ALL the other packages with a red dot installed to be able to install Wine." 
does this mean that i have to download and install all of those more than 25 package individually.
this cant be done so easiy, plz help

Yes, that's exactly what i'm saying.

The way software works on Linux is that every package (eg: Wine) declares a number of dependencies. Those are all the packages on that page with a red dot. In order for the package manager to install Wine, all of those must already be installed, because it needs them to work. Some will already be on your system, but some won't. Normally the package manager will automatically download any extra ones you need and install them, but since you aren't online you would have to install them manually. Each one of those packages might even have packages that they depend on, and so on and so on. This is called Dependency Hell.

The easiest thig to do is use a machine which is online to get all the packages you need and copy them to your machine, as I explained above. Once you have all the required packages in your APT cache the package manager can install Wine without needing to download anything.

---

### Post by Paqman on 2011-04-16
> **vivek.pandey said:**
> just try following this link for wine
[http://ubuntuforums.org/showthread.php?t=1383693](http://ubuntuforums.org/showthread.php?t=1383693)

That won't work. Even if you compile from source you will still need to satisfy the dependencies.

---

