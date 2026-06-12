---
title: "3D switch between windows"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by ehalls on 2009-12-29
Hi,
 
I have seen on videos that there is a cool 3d way to switch between windows in Ubuntu. A bit like the button close to start menu in Vista, and then you use the mousewheel to scroll between windows. Does anyone know how to install that?
 
There is also a menu where the icons magnifyes as I move the mouse over them. What is that menu called? I don't mean the avant navigator where the icons jumps up an down when you move over them, like on a mac.
 
Best regards 
 
Erik

---

### Post by aktiwers on 2009-12-29
Open synaptics package manager and search for "Compizconfig"

Then install the package called " Compiz configuration settings manager"

When its installed find it under System => Preferences => Compiz configuration settings manager

in there search for "shift switcher" and enable it. Now on your keyboard click the windows key and tab at the same time.

Edit:
The dock you are talking about might be the one included in Gnome-DO (or its not included in the latest versions, they split, but the version in the repos has it).

again in Synaptic search for "gnome-do" and install it. Run it from Applications => Accessories => Gnome-Do.

Go to preferences in Gnome-Do and enable "docky theme".


An even faster way to install those apps is by going to Applications => accessories => terminal 
and type:
```
sudo apt-get install gnome-do compizconfig-settings-manager
```

or simply click these 2 links:
[Install Gnome-DO (click!)]("apt:gnome-do")
[Install CCSM (click!) ]("apt:compizconfig-settings-manager")

---

### Post by ehalls on 2009-12-30
> **aktiwers said:**
> Open synaptics package manager and search for "Compizconfig"

Then install the package called " Compiz configuration settings manager"

When its installed find it under System => Preferences => Compiz configuration settings manager

in there search for "shift switcher" and enable it. Now on your keyboard click the windows key and tab at the same time.

Edit:
The dock you are talking about might be the one included in Gnome-DO (or its not included in the latest versions, they split, but the version in the repos has it).

again in Synaptic search for "gnome-do" and install it. Run it from Applications => Accessories => Gnome-Do.

Go to preferences in Gnome-Do and enable "docky theme".


An even faster way to install those apps is by going to Applications => accessories => terminal 
and type:
```
sudo apt-get install gnome-do compizconfig-settings-manager
```or simply click these 2 links:
[Install Gnome-DO (click!)]("apt:gnome-do")
[Install CCSM (click!) ]("apt:compizconfig-settings-manager")

Hi aktiwers,
It didn't work to press windows key and tab after enabling shift switcher. I am running Ubuntu netbook remix, maybe that has something to do with it? Since 3d desktop didn't work to it maybe that is the case, however I didn't receive any error messages. 

In Gnome-Do i couldn't enable the Docky theme. It says "... To use this features you must enable compositing". 

Anyways, now I know the names of these features. It is hard to google them when only can explain them. Thanks for the help.

Best Regards

Erik

---

### Post by aktiwers on 2009-12-30
Hi Erik,

Your welcome and welcome to the forums!

Please always come to these forums if you have anyt questions, people here would love to help :)

Do you know what video card you have? Maybe you could have a look at the "Hardware drivers" app, and see if it has anything for you?

Its located at System => Administration => Hardware drivers

---

### Post by Paqman on 2009-12-30
> **ehalls said:**
> I don't mean the avant navigator where the icons jumps up an down when you move over them, like on a mac.


In AWN Manager you can choose from loads of different effects for when you mouseover icons, including one that magnifies. I personally like the spin and glow effect.

---

### Post by ehalls on 2009-12-30
> **aktiwers said:**
> Hi Erik,

Your welcome and welcome to the forums!

Please always come to these forums if you have anyt questions, people here would love to help :)

Do you know what video card you have? Maybe you could have a look at the "Hardware drivers" app, and see if it has anything for you?

Its located at System => Administration => Hardware drivers

It says "No proprietary drivers are in use on this system" and the rest is just blank. My computer is GIGABYTE 912m tablet pc. I had Ubuntu installed before and then the 3d desktop worked and all the compiz effects, however after installing Ubuntu netbook remix it didn't work. Maybe compiz is disabled in netbook remix? Thanks for the hospitality! :)

---

### Post by ehalls on 2009-12-30
> **Paqman said:**
> In AWN Manager you can choose from loads of different effects for when you mouseover icons, including one that magnifies. I personally like the spin and glow effect.

Hi Paqman,
I can't find the AWN Manager when searching in the Ubuntu Software Center, what does AWN stand for? And what is that spin and glow effect formally called in the program?

Best Regards,
Erik

---

### Post by Paqman on 2009-12-31
> **ehalls said:**
> Hi Paqman,
I can't find the AWN Manager when searching in the Ubuntu Software Center, what does AWN stand for? And what is that spin and glow effect formally called in the program?

Best Regards,
Erik

If you have Avant Window Navigator installed then the AWN Manager will be in your System > Prefs menu.

---

### Post by 3rdalbum on 2009-12-31
You can't use Compiz at the same time as the Netbook Launcher. You could modify your system so it runs regular Gnome like the normal Ubuntu, and then you'll be able to run Compiz.

Or you could just install regular Ubuntu.

---

### Post by ehalls on 2009-12-31
> **3rdalbum said:**
> You can't use Compiz at the same time as the Netbook Launcher. You could modify your system so it runs regular Gnome like the normal Ubuntu, and then you'll be able to run Compiz.

Or you could just install regular Ubuntu.

Hi 3rdalbum, 
I have read on the forum that there should be a switch-to-desktop mode button under system-preferences in UNR, however I can't find it. By the way, is there any differences in speed between UNR and regular Ubuntu, because I don't feel feel much difference, even when I had compiz desktop effects enabled in regular Ubuntu.

Cheers

---

### Post by theozzlives on 2009-12-31
UNR is mainly designed for the smaller screens on netbooks. To enable Compiz, put```
compiz --replace
```in your startup applications and reboot.

---

### Post by ST3ALTHPSYCH0 on 2009-12-31
> 
It says "No proprietary drivers are in use on this system"
> 

```

     compiz --replace 

```
Uhh, you can't composite a screen without 3d drivers installed.

---

### Post by ehalls on 2010-01-01
> **theozzlives said:**
> UNR is mainly designed for the smaller screens on netbooks. To enable Compiz, put```
compiz --replace
```in your startup applications and reboot.

That did it, now both 3d desktop rotation, windows switcher, gnome-do and avant windows manager works! Thanks!

---

