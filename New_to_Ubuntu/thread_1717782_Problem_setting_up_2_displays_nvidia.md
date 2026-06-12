---
title: "Problem setting up 2 displays nvidia"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Hellfish03 on 2011-03-30
I've just switched to from windows to ubuntu 10.10, and I have no experience with linux. I am trying to set up a monitor with 1440 x 900 resolution with an LCD TV 1366x768 as the second display. I'm using a Geforce 8800 GTS card and both displays are connected their own vga port. I am using the correct propriety driver for the card. 

I have both working using Twinview with the monitor at 1440 x 900 resolution and the LCD TV only at 1024x768. When I change the resolution of the TV to the correct size 1360x768, as I had it on windows, the edges of the screen are off of the display. 

Any help greatly appreciated!

---

### Post by khelben1979 on 2011-03-30
Are you changing to 1360x768 from within the nVidia control panel, or is it done on the TV using it's own inbuilt settings?

What version of the nVidia drivers are you using?

---

### Post by Hellfish03 on 2011-03-30
Yes, I'm changing the settings in the nvidia control panel. I'm using the current version of the driver. When I search for additional drivers I get the option to use version 173 which I tried and got the same problem.

---

### Post by papibe on 2011-03-31
Be aware that most TVs do not display the whole signal on the screen by default. They do a mild zoom on the signal (a bad practice inherit from analog practices). Sometimes you need to play a little with the TVs options for the VGA/HDMI input. For example, in my Sony Bravia I had to go to Screen -> Display Area, and set it to "Full Pixel". In my brother's Samsung it's something like  Picture -> More -> Picture Options -> Screen Size, and the Value is "Just Scan".

Good Luck!

---

### Post by wolfen69 on 2011-03-31
You need to use the Nvidia control panel by invoking:
```
gksu nvidia-settings
```
Otherwise the settings won't be remembered after reboot. After getting all the settings done, remember to save to x-config file.

---

### Post by Hellfish03 on 2011-03-31
Thanks for the replys. I've had a look through the TV settings and everything is ok there. I have been using the nvidia control panel and saving the x-config then rebooting. But still the same problem. When I choose the 1360x768 resolution 1/2 of the display is off screen. When I let nvidia automatically choose the resolution it picks 10274x768, which works just fine, but the picture is not as sharp as it could be and the full screen doesn't always fill the screen. It worked just fine on windows and I haven't changing anything in the set up since then. So maybe a problem with the driver? 

Any help greatly appreciated!

---

### Post by Hellfish03 on 2011-04-04
I'm still having problems fixing this. is there any way to add custom resolutions? i have a feeling i was using 1280×720 before, but this is not available in the nvidia settings

---

