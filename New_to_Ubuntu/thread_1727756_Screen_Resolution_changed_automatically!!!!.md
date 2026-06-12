---
title: "Screen Resolution changed automatically!!!!"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by gaurish108 on 2011-04-12
I rebooted my computer today and  the screen resolution has changed  automatically to 640x480. The usual screen resolution 1024x768 does not seem to  be available in System-->Preferences-->Monitors. Further,  typing xrandr at the terminal gives me only two screen resolutions, one of the highest one being 640x480. 

What should I do?

Thanks

---

### Post by jtarin on 2011-04-12
Go through "Control Panel>Monitors and see if the dialog offers more choices. Did you recently install any software? Do an update?

---

### Post by Blasphemist on 2011-04-12
I worked on an issue very similar today. That one turned out to be a cable or the KVM switch the person was using. In the process of getting to that (isn't it always the simple explanation when something changes so abruptly) we did go through how to add undetected resolutions that aren't showing up. Look at this.


Adding undetected resolutions
Due to buggy hardware or drivers, your monitor's correct resolutions may not always be detected. For example, the EDID data block queried from your monitor may be incorrect.

If the mode already exists, but just isn't associated for the particular output, you can add it like this:


$ xrandr --addmode S-video 800x600
If the mode doesn't yet exist, you'll need to create it first by specifying a modeline:


$ xrandr --newmode <Mode``Line>
You may create a modeline using the gtf or cvt utility. For example, if you want to add a mode with resolution 800x600, you can enter the following command: (The output is shown following.)


$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
Then copy the information after the word "Modeline" into the xrandr command:


$ xrandr --newmode "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
After the mode is entered, it needs to be added to the output using the --addmode command as explained above.

I do recommend that you think back to anything that may have happened prior to this occurring that could have possibly caused it. Also, what is your platform? What is your hardware and software platform detail?

---

