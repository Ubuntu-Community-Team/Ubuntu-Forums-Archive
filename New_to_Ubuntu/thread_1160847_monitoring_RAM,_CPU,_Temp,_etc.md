---
title: "monitoring RAM, CPU, Temp, etc"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-05-16
Hi,

I know that I can add a little widgets to the top and bottom panels that monitors CPU speed. Is there one for RAM usage and computer temperature?

I know i can do this with conky, but i don't really having to minimize to my desktop every time to see whats going on, and i just don't like the setup overall. 

What's the package to install?

Thanks for your help

---

### Post by desperado665 on 2009-05-16
You can use the following in terminal:

```
sudo apt-get install lm-sensors
sudo sensors-detect
```

hit Y to everything
then install sensors-applet

```
sudo apt-get install sensors-applet
```

or if you just want to view temps without the applets:

```
sudo sensors
```

---

### Post by akimatsu123 on 2009-05-16
never mind, i figured out ram and cpu and network mointors came with "system monitor" thats built into ubuntu

any ideas abt temp?

---

### Post by desperado665 on 2009-05-16
Those codes will add cpu/video/hard drive temp sensors if your motherboard supports them

---

### Post by drubdrub on 2009-05-17
A note on using the sensors-applet ...

Right-click the panel and select "Add to panel".  A window will appear.  Select "Hardware Sensors Monitor" applet and click the "Add" button.  The temperatures should be displayed on your panel.  The 

Please note ... The panel is often located at the bottom of the screen, but is configurable to be placed on any of the 4 edges of the screen.

Additional information can be found at [http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)

Enjoy!

---

### Post by anextx on 2010-02-01
hmm... when i followed this process the only sensor it detected was 'AMD K10 thermal sensors' but when it listed the code to add to /etc/modules it said 'no driver for AMD K10 thermal sensors yet'

is there another way to check for the driver or an alternative method for system monitoring?  hdd and cpu temp is what im interested in.

-anextx

---

### Post by CJ_Hudson on 2012-09-28
Hi, I can run the sensor program from the Terminal and get the info but can't seem to get the real-time on-screen readout- please instruct? :KS

---

### Post by oldos2er on 2012-09-28
Please start a new thread, this one's quite old.

---

