---
title: "Does an icon dock exist for Ubuntu?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by GumpTron on 2009-04-24
Thank you for taking the time to read this.

I have just installed the newest version of Ubuntu and I would like to find a dock for my desktop. I have heard of something called "Simdock", but I was not able to install it.

I use "Rocketdock" on my Vista OS and I love it. I really want a "dock" on my Ubuntu desktop and I have heard some really nice ones are available. Any help is appreciated. Thank you.

---

### Post by random turnip on 2009-04-24
Rocketdock is my favorite thing about Vista right now, lol.

Yes, i know for a fact that there is at least one decent dock application on Ubuntu, i've seen numerous screenshots, but as i'm not on Ubuntu right now i can only advise to search for "dock" in the get application window.

---

### Post by GumpTron on 2009-04-24
> **random turnip said:**
> Rocketdock is my favorite thing about Vista right now, lol.

Yes, i know for a fact that there is at least one decent dock application on Ubuntu, i've seen numerous screenshots, but as i'm not on Ubuntu right now i can only advise to search for "dock" in the get application window.

i searched for "dock" in the add/remove program and I did not get anything. Any other ideas?

---

### Post by slibuntu on 2009-04-24
Avant Window Navigator is one of the best docks.

I also love the dock of Gnome Do, install gnome do, go to preferences, and select the appearance and pick the dock one. It's great

---

### Post by Peter09 on 2009-04-24
AWn is a good doc.
You can install with

```
sudo apt-get install avant-window-navigator
```
```
sudo apt-get install awn-manager
```

---

### Post by GumpTron on 2009-04-24
> **Peter09 said:**
> AWn is a good doc.
You can install with

```
sudo apt-get install avant-window-navigator
```
```
sudo apt-get install awn-manager
```

did this, but where do i find the dock to activate it?

---

### Post by Peter09 on 2009-04-24
System->Preferences->Awn Manager (tick the startup on boot box)

You can also start it from a terminal with

```
avant-window-navigator
```

---

### Post by GumpTron on 2009-04-24
> **Peter09 said:**
> System->Preferences->Awn Manager (tick the startup on boot box)

You can also start it from a terminal with

```
avant-window-navigator
```

Works! Thank you.

---

### Post by riza hylviu on 2009-04-24
Mine is in  Applications/accessories , 
it does not start always when you boot ubuntu so yo have to add it to start up aplications  System/Preferences/Start up applications with the command 
avant-window-navigator

---

### Post by GumpTron on 2009-04-24
I am getting "Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager".

HELP! I am not able to load the dock and my compiz settings aren't working at boot up.

---

### Post by Peter09 on 2009-04-24
Yep - you have a problem with your graphics.

Post the output of

```
lshw -C video
```

---

### Post by GumpTron on 2009-04-24
> **Peter09 said:**
> Yep - you have a problem with your graphics.

Post the output of

```
lshw -C video
```

WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GeForce 9600M GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by Peter09 on 2009-04-24
if you run compiz in a terminal what errors do you get?

---

### Post by JoshuaRL on 2009-04-24
Two things:  1).  What graphics card do you have?  If you don't know, go to Applications->Accessories and open the Terminal.  From there, put this in:
```
lspci
```
Then post it in a thread with [noparse]```
 tags 
```[/noparse] around it.

2).  What graphics driver are you using, and is there a proprietary one available?  Go to System->Administration and open Hardware Drivers.  What do you see there?

---

### Post by GumpTron on 2009-04-24
> **Peter09 said:**
> if you run compiz in a terminal what errors do you get?

im a noob, just installed today. Tell me what you need me to do so I can get you the info.

FYI compiz and all the settings were working fine until i tired to use that dock application.

---

### Post by Peter09 on 2009-04-24
Open a terminal by 
Applications->Accessories->Terminal

then type in the terminal the following

```
compiz
```

what happens, paste any errors here.

---

### Post by Peter09 on 2009-04-24
Just thought---
go to System->Preferences->Appearance

Got to the visual effects tab and tick EXTRA

---

### Post by GumpTron on 2009-04-24
> **Peter09 said:**
> Just thought---
go to System->Preferences->Appearance

Got to the visual effects tab and tick EXTRA

"desktop effects could not be enabled"

---

### Post by GumpTron on 2009-04-24
> **Peter09 said:**
> Open a terminal by 
Applications->Accessories->Terminal

then type in the terminal the following

```
compiz
```

what happens, paste any errors here.

$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Peter09 on 2009-04-24
Suggests that your graphics driver is not setup.

Check that in

System->Administration->Hardware Drivers 

to see if a third party driver needs to be enabled.

---

### Post by GumpTron on 2009-04-24
> **Peter09 said:**
> Suggests that your graphics driver is not setup.

Check that in

System->Administration->Hardware Drivers 

to see if a third party driver needs to be enabled.

I did the search, but for the record I had set this up earlier and it worked fine. Anyway, I did the update (again) and it worked. I then enabled the extra features in "visual effects" and I now have a working dock and my compiz is working. I am going to restart to see if it holds, brb.

---

### Post by GumpTron on 2009-04-24
everything seems to be working. Thank you for your help

---

### Post by Peter09 on 2009-04-24
Great - enjoy

---

### Post by slibuntu on 2009-04-24
Another happy customer :)

---

