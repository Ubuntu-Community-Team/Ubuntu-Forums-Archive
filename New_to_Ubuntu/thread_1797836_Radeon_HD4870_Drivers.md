---
title: "Radeon HD4870 Drivers?"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by climhazzard36 on 2011-07-05
I have a Powercolor 4870 1GB and ubuntu Natty 64-bit.

How do I check that I have the best drivers installed and if I haven't, how do I go about installing them.

Any help will be really appreciated.

---

### Post by seawolf167 on 2011-07-05
You can install them via the Additional Drivers section, by going to System -> Administration -> Hardware Drivers, or on 11.04, click the power button in the upper right corner, select System Settings, then Additional Drivers. You can then select which drivers to activate.

Additionally, you can install the proprietary driver suite as released by ATI by downloading and running the driver install file from their website [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English").

---

### Post by climhazzard36 on 2011-07-05
I ran that by running
```
sudo sh ati----.run
```

I rebooted and my monitor preferences were set back to clone ( I have 2 monitors).

The problem I got now is that when I try extend the monitors instead of cloning them I get a pop-up that says:

"The selected configuration could not be applied- requested position/size is outside of limit"

Any ideas?

---

### Post by seawolf167 on 2011-07-05
Were the drivers actually installed? I normally have to stop GDM to be able to install the drivers.

Switch to tty1 by hitting [ALT][F2]

Stop GDM

```
sudo service gdm stop
```

Change to the driver directory

```
cd /path/to/driver
```

Make the driver executable

```
sudo chmod +x name.of.driver.run
```

Run the driver

```
./name.of.driver.run
```

After installation, reboot, then you can open the driver suite from System -> Administration -> Catalyst Driver Suite and change the monitor preferences.

---

### Post by climhazzard36 on 2011-07-05
Alt + F2 just started the 'run application' pop-up, so I used ctrl+alt+F2 which started tty2 (not sure if that is the same thing)

I ran your commands and rebooted. I then changed my pref's in CCC and rebooted again.

That didn't change anything, but this time around I could change it via preferences > Monitors.

The only problem I got now is that when moving windows around the desktop they move sluggishly, kinda jumpy almost. They didnt do this before the driver install :S

Any ideas?

(thanks for the help so far by the way, I appreciate it :D)

---

### Post by seawolf167 on 2011-07-05
Sorry, it is [CTRL][ALT][F1], accidentally put in the wrong command!

Instead of changing the preferences from System -> Preferences -> Monitors, can you change it from the driver suite that was installed? There should be two entries (a "normal" one and one that says "Administrator" next to it). Run the "Administrator one, and change the resolution and positioning from there and see if it helps.

---

### Post by climhazzard36 on 2011-07-05
Ahh no worries!

I was using the administrative option already btw.
I can change the options in CCC but they do not change the lag problem. Its a problem in games (eg. neverput).. the game lags really badly.

Running the session with (no effects) cures the desktop problem but not the game problem :/

---

### Post by seawolf167 on 2011-07-05
Does reconfiguring xserver-xorg help at all?

[CTRL][ALT][F1]
```
sudo service gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo service gdm start
```

---

### Post by climhazzard36 on 2011-07-05
Just tried that, and nope no effect :/

Should I un-install this driver and try the propriety ones? Will they be as good?

---

### Post by akand074 on 2011-07-05
You're using Natty aren't you? Did you disable sync to vblank? From compizconfig settings manager under OpenGL? I hear that's a known bug.

---

### Post by climhazzard36 on 2011-07-05
Thankyou!

I disabled Sync to VBlank in Compiz which made things run smooth but caused a lot of tearing.

Then I went into CCC and selected 'Tear-Free-Desktop' and now its running brilliantly.

Thankyou both for all your help:popcorn:

---

### Post by seawolf167 on 2011-07-05
Awesome - glad it worked, thanks for the info akand074.

---

### Post by climhazzard36 on 2011-07-05
Is there any way to give rep on this site?

---

### Post by seawolf167 on 2011-07-05
Nope - the closest would be to leave a visitor message on said user's page saying something to the effect of "+1 Rep" lol

---

### Post by akand074 on 2011-07-05
> **climhazzard36 said:**
> Is there any way to give rep on this site?

No, we're just here to help as volunteers, no need to be recognized. I knew there was a second thing to do but I swear I couldn't think of it. I should have remembered to tell you to enable tear free desktop. I'm glad you managed to figure it out yourself! Hope you stay issue free.

---

### Post by climhazzard36 on 2011-07-05
Ahh alright, 

I hope I do too, but since I'm still learning the basics, I can guarantee I'll mess something up in the near future :P

Thanks again both!

---

### Post by tomster2300 on 2011-10-28
> **akand074 said:**
> No, we're just here to help as volunteers, no need to be recognized. I knew there was a second thing to do but I swear I couldn't think of it. I should have remembered to tell you to enable tear free desktop. I'm glad you managed to figure it out yourself! Hope you stay issue free.

I know this is kind of an old thread, but I wanted to post and say thank you for your earlier post. Unchecking sync to vblank just made a night and day difference for me in 11.10.  Ubuntu now flies!  :)

---

