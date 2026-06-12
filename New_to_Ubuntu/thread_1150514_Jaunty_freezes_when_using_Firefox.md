---
title: "Jaunty freezes when using Firefox"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Setämies on 2009-05-06
[SIZE=4]I have an annoying problem that occurs a couple of times a day. When I'm using Firefox, the system randomly freezes and my keyboard and mouse won't respond to anything. Only hard reset will get it back up and running. Sometimes it occurs when the Flash plug-in (non-free) is active, but I have, however, replicated this even without Flash. I haven't experienced this without Firefox.

Now, I have found some bug reports on Launchpad that this problem is somehow related to Compiz and buggy Nvidia drivers (I'm currently using the "Nvidia 96" drivers installed through "Hardware Drivers", I have an ancient Geforce 4200TI), but the only remedy they provided was to disable Compiz or use the Nv drivers. I really don't want to do either, I want my desktop to be beautiful **and** functional. Besides, I haven't found enough proof that this will actually remove the problem.

I would have posted some error logs and whatnot, but I don't know where they are preserved or if they are generated in the first place, since the system becomes completely unresponsive.

Could you please tell me where to start solving this problem?

EDIT: I should add that I've had this problem since 8.10 and the problem persisted even on a clean install of 9.04.
[/SIZE]

---

### Post by blazemore on 2009-05-06
I would start by testing without the proprietery drivers, to see if they are the problem
I would then remove Compiz, to see if that's causing a problem.

Make sure you're running the most up-to-date drivers. By the way, are you sharing a Firefox profile with a dual-booted Windows system?

---

### Post by Setämies on 2009-05-06
Ok, I tried installing the latest legacy driver 96.43.11. Everything else is working like a charm and no freezes so far, but I've got a new problem. I lost window decorations while upgrading. How do I get them back?

Or, more precisely, I lost the whole window title bar!

---

### Post by NightwishFan on 2009-05-06
If you have compiz on press alt+f2 and type:
```
gtk-window-decorator --replace
```


If you have no desktop effects on run:
```
metacity --replace
```

---

### Post by Setämies on 2009-05-06
> **NightwishFan said:**
> If you have compiz on press alt+f2 and type:
```
gtk-window-decorator --replace
```


I'm running compiz, and this command didn't help. What's next?

---

### Post by NightwishFan on 2009-05-06
Let me be clear, your problem is no bar above individual windows correct?

First see if 3d rendering is available. If you see gears then you are fine.
```
glxgears
```

Then try this (in terminal).
```
sudo apt-get update && sudo apt-get upgrade
```

Then try this again (In terminal now, and tell me what the errors are if any.)
```
gtk-window-decorator --replace
```

We can go on from there

---

### Post by Setämies on 2009-05-06
I did all of the above.
Glxgears was fine.
The second step was fine.
However, when I tried in terminal
```

gtk-window-decorator --replace
```
It did absolutely nothing. It never actually completed execution. It just stood there ad infinitum with the cursor blinking below, with no output whatsoever.

---

### Post by blazemore on 2009-05-06
Try hitting Alt+F2, typing
```
sudo apt-get install fusion-icon
```
Ticking the "Run in Terminal" box and pressing OK

Then set the program "fusion-icon" to run at startup.

---

### Post by NightwishFan on 2009-05-06
Does metacity work? I am assuming it does. Another step you can try is to see if emerald works, however I prefer the GTK-Window-Decorator.

Try to reinstall compiz and the gnome packages for it, and the log out and log back in.

---

### Post by Setämies on 2009-05-06
> **blazemore said:**
> Try hitting Alt+F2, typing
```
sudo apt-get install fusion-icon
```Ticking the "Run in Terminal" box and pressing OK

Then set the program "fusion-icon" to run at startup.

This did not work.

> **NightwishFan said:**
> Does metacity work? I am assuming it does. Another step you can try is to see if emerald works, however I prefer the GTK-Window-Decorator.

Try to reinstall compiz and the gnome packages for it, and the log out and log back in.

Yup, metacity works. I'm going to try reinstalling compiz.

---

### Post by blazemore on 2009-05-06
Right click on the fusion icon and set the window decorations to Compiz.

---

### Post by Setämies on 2009-05-06
It only offers me GTK and Emerald. (neither of them work, when Compiz is active)

---

### Post by Claus7 on 2009-05-06
Hello,

I confirm the same issue to my installation as well. I face exactly the same problem. Only drivers from intel seem to be the solution? The last time I installed them things were not very good...

EDIT: I decided to install the same driver as you did. The installation went ok, apart from the fact that it was complaining with some errors, I suppose because I had from synaptic intalled the 96 package from there. So I think that it is best before, to remove everything nvidia from there and also to disable any restricted drivers from System->Administration. I rebooted and still had some problems with unknonwn resolution, so I entered from secure shell, removed the "bad-out of range" resolution and still had problems with compiz and the surrounding borders. In order to make this work I added this in xorg.conf file:
(under section screen)
Option "AddARGBGLXVisuals" "true"

(in the end of the file)
Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "on"
EndSection

EDIT2: Things seem to work sharper and better I think, yet is early to say things about firefox. The logo nvidia appeared the first time, yet I have not seen it the second time...

Regards!

---

### Post by Setämies on 2009-05-07
^Thank you, sir! That did the trick for me! The only thing I'm still worried about is system stability, but only time will tell!

Once again, thank you!

---

### Post by clockworksaint on 2009-05-08
> **Setämies said:**
> [SIZE=4]I have an annoying problem that occurs a couple of times a day. When I'm using Firefox, the system randomly freezes and my keyboard and mouse won't respond to anything. Only hard reset will get it back up and running. Sometimes it occurs when the Flash plug-in (non-free) is active, but I have, however, replicated this even without Flash. I haven't experienced this without Firefox.

I have had the same problem a few times since I upgraded to Jaunty recently. During one of the hard resets, my file-system got corrupted. Here's the thing - it happened again while running the LiveCD. I was reading a page in Firefox and suddenly everything froze. Mouse cursor wouldn't move, nothing changed on the screen, no keyboard response. Again I could only restart by holding down the power button.

I have a "Philips Freevents" laptop with an Intel Core 2 Duo Mobile P7350, 4GB RAM, nVidia GeForce 9300M GS and a wifi card that identifies itself as "Intel Corporation Wireless WiFi Link 5100".

I did not have this problem in 8.10. Is there anything I can do to try to pin down the problem?

---

### Post by Claus7 on 2009-05-08
Hello,

what I would suggest you is reinstall the nvidia drivers from synaptic. Other that that you could follow exactly the process I described in previous post, yet having in mind to choose the right driver file for your situation. 

As far as viewing log files for your system is concerned, this link might help you:
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

Regards!

---

### Post by Setämies on 2009-05-08
[SIZE=4]This thread is going all over the place - sorry about that - but after inspecting the system logs thoroughly I may have found the actual culprit. Xorg.log revealed no error relating to my display drivers, neither did other logs. I did find something interesting in several logs within freeze/crash timeframe:[/SIZE]

```
May  6 18:00:36 julius-desktop pulseaudio[5245]: pid.c: Stale PID file, overwriting.
May  6 18:00:37 julius-desktop pulseaudio[5245]: alsa-util.c: Error opening PCM device hw:0: No such file or directory
May  6 18:00:37 julius-desktop pulseaudio[5245]: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
May  6 18:00:37 julius-desktop pulseaudio[5245]: alsa-util.c: Error opening PCM device hw:0: No such file or directory
May  6 18:00:37 julius-desktop pulseaudio[5245]: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.
May  6 18:00:37 julius-desktop pulseaudio[5245]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
```[SIZE=4]
This error occurs on many occasions[/SIZE]

```
May  6 20:28:16 julius-desktop pulseaudio[2979]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
```[SIZE=4]So it seems that the freeze might originate from the infamous Pulseaudio. Is there anything I can do about this?[/SIZE]

---

### Post by Claus7 on 2009-05-09
Hello,

I think that what you might be able to do is remove pulseaudio from your system entirely (go to synaptic and remove the pulseaudio files). It is not uncommon to see people doing this in the forums. 

Regards!

---

### Post by thiefy on 2009-05-20
i have a very new dell notebook with nvidia 9500 sli   - don't know if that's relevant...
quite fresh installation of jaunty 64 bit and compiz running.
though, things work well, except battery life is pathetic and 
whenever i close firefox the system freezes and the only way out is to hold down the power button.
this is sad.


i would like to do as you advised. in removing pulse audio - i'd reckon alsa is fine and what do i need pulse for?
though, in synaptic, if i search for pulse, it says i'd have to remove 'ubuntu desktop' also, this i don't want to do.
how should i proceed?

---

### Post by thiefy on 2009-05-20
oooh, and i have a bean now!
yay!

---

### Post by thiefy on 2009-05-27
ok, i've learned that removing ubuntu-desktop doesn't do anything. so it's ok...

now i've remove the pulseaudio  - but there's still a ton of pulse things installed.

anyone know if it it's wise to get rid of all pulse audio type things in synaptic?
i've learned that it is horrible and i think the cause of my firefox crashing the computer, so i'd like to remove it.
any advice?

---

### Post by Blue Sassley on 2009-05-27
When you removed the pulseaudio packages did you use autoremote?

```
sudo apt-get autoremove pulseaudio
```

If not you should be able to just run autoremove without any packages to clean up unused packages

```
sudo apt-get autoremove
```

Blue

---

### Post by WinterMadness on 2009-05-27
until your problem is solved, try using epiphany instead of firefox. it imports all your favorites and plugins and its lightning fast. i used to have firefox issues, and i used epiphany for a long time and it never had the problems.

---

