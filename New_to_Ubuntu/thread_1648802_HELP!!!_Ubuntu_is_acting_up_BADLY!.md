---
title: "HELP!!! Ubuntu is acting up BADLY!"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by 289531.EXE on 2010-12-19
So, there I am working on a cover when I go to check my mail and out of nowhere - the damn window loses its title bar and the system starts to act sluggish. Ok, so I'll just restart and it should fix this minor glitch right? WRONG! It loaded really slow and when I open firefox or pidgin there is no title bar, no "X" or anything. I try clicking this and that and nothing, just more freezing and slowing down.

So I looked it up and found a suggestion. Change the visual effects. I changed from none to normal, which fixed the problem for a second. I went back to none and it took away my title bar and messed everything up again. I need the option at none since this laptop isnt the newest.

Now, all my work and photos are stuck in that hard drive. I NEED THAT HARD-DRIVE AND THE CONTENTS IN IT! Can someone please help me?

---

### Post by davec64 on 2010-12-19
try in a terminal:
```
metacity --replace
```
I think that's the right way around!
sounds like it might be an issue with the decorator. :)

---

### Post by 289531.EXE on 2010-12-19
I tried that but all I got was some sort of error message-

---

### Post by 289531.EXE on 2010-12-19
:'(     I need my archived art and the current cover I was working on

---

### Post by 289531.EXE on 2010-12-19
FML I just ran that code on this HD and the same thing is happening on this one, and now I have to keep it on normal visual settings. What's going on with Ubuntu? I never had this problem before and I didn't go changing anything, I was just using gimp and facebook.....?!?!?!!?!

---

### Post by 12apennachi on 2010-12-19
Do you have compiz? If so, compiz --replace. And for that matter, ditch compiz

---

### Post by 289531.EXE on 2010-12-19
Ok, so every time I run either code, it gives me error or warnings. I just salvaged my files but I don't want to have to re-customize my desktop and it's running slow now. What exactly could I do to fix this permanently and put my visual settings back to none?

---

### Post by fslezak on 2010-12-19
What graphics driver are you using?

---

### Post by 289531.EXE on 2010-12-19
Should I add that this happened after I added a new panel on top of the screen with a row of 34 different desktop workspaces?

---

### Post by iponeverything on 2010-12-19
> I never had this problem before and I didn't go changing anything, I was just using gimp and facebook.....?!?!?!!?! 

> Should I add that this happened after I added a new panel on top of the screen with a row of 34 different desktop workspaces? 

humm..

did you try removing the applet?

---

### Post by 289531.EXE on 2010-12-19
Yea, I caught that too. What I meant the first time was that I didn't go into any specific folders or files. And yes, I did remove the panel and the work spaces but it didn't really do anything-  How do I find that?

---

### Post by admiralspark on 2010-12-19
This may be a bit ridiculous, but did you run the aforementioned codes with sudo used before them?
If you did, we'll have to take a look at what's going on exactly.
If you could post the output of 
```
top
```
onto here so we can see what exactly is taking up all your memory?

How old is this hardware? Anything within the last several years should be able to handle Compiz, and anything older could be faulty hardware (or just dusty).

---

### Post by 289531.EXE on 2010-12-19
top - 14:45:47 up  3:15,  2 users,  load average: 2.97, 3.05, 2.87 Tasks: 138 total,   2 running, 136 sleeping,   0 stopped,   0 zombie Cpu(s): 71.3%us, 27.4%sy,  0.0%ni,  0.3%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st Mem:   2052492k total,  1572572k used,   479920k free,    42608k buffers Swap:  6010872k total,        0k used,  6010872k free,  1042040k cached   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              2051 administ  20   0  558m 207m  26m S 15.0 10.3   4:38.00 plugin-containe       819 root      20   0 50636  24m  15m S 11.4  1.2  20:30.10 Xorg                 1272 administ  20   0  7640 4320 2212 S  7.5  0.2  18:31.79 gconfd-2             4725 administ  20   0  348m 132m  29m S  2.9  6.6   8:44.11 firefox-bin          5341 administ  20   0 75280  23m 7772 S  2.9  1.2   3:28.95 compiz               5453 administ  20   0 48124  14m  10m S  2.3  0.7   0:03.27 gnome-terminal       1225 administ  20   0 27788 8400 6152 S  2.0  0.4   4:00.10 gnome-session        1269 administ  20   0  3060 1332  660 S  2.0  0.1   4:24.72 dbus-daemon          1278 administ  20   0 23264  12m 4328 S  1.3  0.6   3:02.63 at-spi-registry      6000 administ  20   0 18564 5248 4136 R  1.3  0.3   0:00.04 metacity             1280 administ  20   0 90516  10m 8008 R  1.0  0.5   1:49.57 gnome-settings-      1306 administ  20   0 60764  17m  12m S  1.0  0.9   2:10.11 gnome-panel          1308 administ  20   0 91368  30m  20m S  1.0  1.5   4:22.03 nautilus             2559 administ  20   0  114m  34m  21m S  0.7  1.7   1:29.21 pidgin                 47 root      20   0     0    0    0 S  0.3  0.0   0:05.84 kondemand/0          1305 administ  20   0 52864  12m 9756 S  0.3  0.6   0:40.42 nm-applet            1307 administ  20   0 20660 8516 6884 S  0.3  0.4   0:27.60 bluetooth-apple

---

### Post by 289531.EXE on 2010-12-19
> **289531.EXE said:**
> top - 14:45:47 up  3:15,  2 users,  load average: 2.97, 3.05, 2.87 Tasks: 138 total,   2 running, 136 sleeping,   0 stopped,   0 zombie Cpu(s): 71.3%us, 27.4%sy,  0.0%ni,  0.3%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st Mem:   2052492k total,  1572572k used,   479920k free,    42608k buffers Swap:  6010872k total,        0k used,  6010872k free,  1042040k cached   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              2051 administ  20   0  558m 207m  26m S 15.0 10.3   4:38.00 plugin-containe       819 root      20   0 50636  24m  15m S 11.4  1.2  20:30.10 Xorg                 1272 administ  20   0  7640 4320 2212 S  7.5  0.2  18:31.79 gconfd-2             4725 administ  20   0  348m 132m  29m S  2.9  6.6   8:44.11 firefox-bin          5341 administ  20   0 75280  23m 7772 S  2.9  1.2   3:28.95 compiz               5453 administ  20   0 48124  14m  10m S  2.3  0.7   0:03.27 gnome-terminal       1225 administ  20   0 27788 8400 6152 S  2.0  0.4   4:00.10 gnome-session        1269 administ  20   0  3060 1332  660 S  2.0  0.1   4:24.72 dbus-daemon          1278 administ  20   0 23264  12m 4328 S  1.3  0.6   3:02.63 at-spi-registry      6000 administ  20   0 18564 5248 4136 R  1.3  0.3   0:00.04 metacity             1280 administ  20   0 90516  10m 8008 R  1.0  0.5   1:49.57 gnome-settings-      1306 administ  20   0 60764  17m  12m S  1.0  0.9   2:10.11 gnome-panel          1308 administ  20   0 91368  30m  20m S  1.0  1.5   4:22.03 nautilus             2559 administ  20   0  114m  34m  21m S  0.7  1.7   1:29.21 pidgin                 47 root      20   0     0    0    0 S  0.3  0.0   0:05.84 kondemand/0          1305 administ  20   0 52864  12m 9756 S  0.3  0.6   0:40.42 nm-applet            1307 administ  20   0 20660 8516 6884 S  0.3  0.4   0:27.60 bluetooth-apple

  2 users?

---

### Post by ugm6hr on 2010-12-19
> **289531.EXE said:**
> Should I add that this happened after I added a new panel on top of the screen with a row of 34 different desktop workspaces?

Have you reduced the number of workspaces back to 4?

> 2 users?
root and you.

---

### Post by 289531.EXE on 2010-12-19
I removed the work spaces and deleted the new panel and now my system is running really slow. This morning it was fine until the title bar with the minimize and maximize buttons were vanished. And now I'm running this on normal visual effect if I change it back to normal, the title bar vanishes again. I tried metacity and compiz code and I didn't see a difference, for metacity I got an error message anf for the compiz code, a warning message. I'm baffled-

---

### Post by 289531.EXE on 2010-12-19
Am I going to just have to reboot my whole laptop or could this be an issue with my laptop and not the OS?

---

### Post by 289531.EXE on 2010-12-19
This is what I get with this code:

metacity --replace
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)
Aborted


AND


compiz --replace

WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!

WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

---

### Post by 289531.EXE on 2010-12-19
When I did this, visual effects was on normal (it was on none before anything happened)and the windows were fine. I typed in the first code and it removed the title bar, I entered the second code right after and it gave me the title bar, does all this slow down the hardware?

---

### Post by 289531.EXE on 2010-12-19
Oh and one more thing:

after this happened in the morning, all the wall papers I removed came back. I don't know how, but I removed all of them except for the solid color, wonder if that "says" anything?

---

### Post by 289531.EXE on 2010-12-19
I just removed all the visual effects and no more title bar......................................???

---

### Post by ugm6hr on 2010-12-19
What version of Ubuntu are you using?
Have you installed any additional window managers?
How many workspaces do you now have?

---

### Post by 289531.EXE on 2010-12-20
it was 10.04
no and none, i rebooted my LT with 10.10

---

### Post by 289531.EXE on 2010-12-20
Thanks tho!

---

