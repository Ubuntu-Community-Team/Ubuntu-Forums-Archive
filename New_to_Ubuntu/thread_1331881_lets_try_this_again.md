---
title: "lets try this again"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by clay woodruff on 2009-11-19
whew that got me in trouble, and i thought this OS was trouble. ok so to all those i offended I'm sorry. also i wasn't trolling, whatever that is. yes I'm running 9.10 but i have no clue as to how to get to a command prompt maybe I'm missing something on the screen because its huge the resolution is 640x480 on a 15 in screen. i didn't get the chance to copy the links to read so if you would be so kind i would appreciate the help. thank god I'm not illiterate. I'm used to blueprints most of this stuff is a foreign language to me. so please be patient

---

### Post by clay woodruff on 2009-11-19
upps i forgot i'm not running it with windows its just 9.10 and noahall yes i did get the driver from hardware manager i have a nvidia 5200 fx

---

### Post by themusicalduck on 2009-11-19
To open a terminal go to Applications > Accessories > Terminal.

Try typing this into the terminal ```
sudo nvidia-settings
``` and see if something comes up, or if there is an error message. You'll need to enter your password too (no characters will come up, just type it and press enter)

---

### Post by clay woodruff on 2009-11-19
ok i started a thread that got me in hot water with admin so it looks like i lost some of the people that were helping me, the post started of WTF. anyways i can get to my nvidia settings screen without any problem the problem i'm having is i can't set my resolution higher than 640x480 i spent the last few days trying to find out a fix for this and when i did i tried to access my root file and i was denied because ROOT was the owner not me... so i flipped the F out and fired off a post stating that fact and here i'am starting a new thread. so what i need to know is how to gain access to my files and my file system let alone the rest of the computer i can't access. also even when i do enter my password when prompted it still doesn't give permission

---

### Post by Merk42 on 2009-11-19
So when you tried sudo nvidia-settings it didn't accept the password?
Did you install Ubuntu yourself or did someone else?

---

### Post by clay woodruff on 2009-11-19
ohh no i'm sorry yes it did and it went to the nvidia control screen but i can access that through the drop down menu. thats not the problem, and when i have been prompted to enter password it does accept it but it didn't get me into my root file. its my understanding i need to modify my xorg.conf file to fix the resolution problem. and i installed it myself............ opps maybe i shouldn't of admitted that. not to computer savy

---

### Post by wojox on 2009-11-19
Okay,

```
gksudo nvidia-settings
```

is what's going to let you edit your xorg.conf file to set your resolution and make it stick. gksudo is you logging into the application as root.

---

### Post by BQAggie2006 on 2009-11-19
Have you first tried making sure the proper drivers are initialized? If not, try going to System >> Administration >> Hardware Drivers, then try activating the proper driver.

---

### Post by clay woodruff on 2009-11-19
yes i got the right drivers. got them from the hardware manager. ok so i type that in the terminal section right. i did and it took me back to the nvidia control screen

---

### Post by Merk42 on 2009-11-19
> **clay woodruff said:**
> yes i got the right drivers. got them from the hardware manager. ok so i type that in the terminal section right. i did and it took me back to the nvidia control screen

Which is what it is supposed to do.
The difference between running gksudo in the terminal vs merely the dropdown is gksudo will allow you to save changes.

---

### Post by wojox on 2009-11-19
Okay you want to click on X Server Display Configuration and set your resolution in there.
And save to X Configuration File.

---

### Post by clay woodruff on 2009-11-19
ok now everything is messed up it streached the screen long ways and i got this message
r current changes to the X server display configuration may no longer be applied due to changes made to the running X server.

You may either reload the current X server settings and lose any configuration setup in this page, or select "Cancel" and save your changes to the X configuration file (requires restarting X to take effect.)

If you select "Cancel", you will only be allowed to apply settings once you have reset the configuration. do i need to enter my monitor type because it shows something else

---

### Post by wojox on 2009-11-19
It should already know your monitor type, but if it's in the drop down select it. On the resolution try and select auto and see where it puts you.

---

### Post by clay woodruff on 2009-11-19
ok this is what i got on the display tab
Model     CRT-0 (CRT-0 on GPU-0)
i have a hp vf51 flat panel and it doesn't show that
on the cofig line it says separate x screen
resolution says only off auto or 640x480 or 320x240 
 its set at 60 hz
at the model line it says 640x480 _ 60 hz
panning says 1024x768
 
my screen is stretched long ways and width ways i have to use mouse to pan through screens
also on the x screen tab 
screen number 0
color 16.7 mill
meta mode 1-...

and the layout screen shows CRT-0
640x480

---

### Post by clay woodruff on 2009-11-19
crap ok i just noticed that in the lower laft corner it says switched to metamode
when i go to that and click on it it gives me these choices
or it says 640x480 _60hz @1024x768 +0+0
320x240 +0+0

---

