---
title: "couple of issues switching to ubuntu"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by geoth on 2010-10-08
I want to make the switch to ubuntu linux but i have 2 problems. 

1 -- when i finish the install or run the ubuntu live cd, i cant connect to the Internet though my wired connection. 
i think this is because i need to change my duplex/speed setting to 10mb half duplex like i do to get windows to work with my router. how can i do this with ubuntu?

2 -- I'm using a philips tv @ 1800x1014 res for a monitor but the desktop is off the screen i can not see my tool bars in gnome. how can i resize the screen?

---

### Post by k33bz on 2010-10-08
> **geoth said:**
> I want to make the switch to ubuntu linux but i have 2 problems. 

1 -- when i finish the install or run the ubuntu live cd, i cant connect to the Internet though my wired connection. 
i think this is because i need to change my duplex/speed setting to 10mb half duplex like i do to get windows to work with my router. how can i do this with ubuntu?

2 -- I'm using a philips tv @ 1800x1014 res for a monitor but the desktop is off the screen i can not see my tool bars in gnome. how can i resize the screen?

Not sure on your first query, however on your second one go to system-> preferences-> monitors you should be able to change the resolution there.

---

### Post by geoth on 2010-10-08
> **k33bz said:**
> Not sure on your first query, however on your second one go to system-> preferences-> monitors you should be able to change the resolution there.

even after the change in resolution my desktop still hangs off the edge of my screen. 

i fix this in windows by using the nvidia control panel i can adjust my screen. i think i have to do this because im using an HDMI cable to hook up to my tv.

---

### Post by geoth on 2010-10-08
i found a guide to help with my Internet connection problem here : 
[http://jaxov.com/2009/09/change-ethernet-cards-speed-and-dulex-settings-in-ubnutu-linux/](http://jaxov.com/2009/09/change-ethernet-cards-speed-and-dulex-settings-in-ubnutu-linux/)


was still wondering about readjusting my screen. should i switch my HDMI cable to a normal computer cable? my tv has ports for both. again changing the res does not help my screen always hangs off the edge.

---

### Post by qyot27 on 2010-10-08
If you fix it in Windows using nvidia's control panel, then I'm assuming you have an nvidia card, and therefore you can do the same thing in Ubuntu.  It requires the proprietary nvidia drivers which come by way of the Hardware Drivers option in the Administrative tools.  Then the option for Nvidia X Server Settings, aka nvidia-settings, will appear in the Administration area and you can do some of the necessary adjustments (I'm not sure about non-standard resolutions or screen resizing, but I'm sure there are ways to get X to do it).  You will need to launch nvidia-settings with gksudo in order for the changes to stick, though; it may also require logging out and back in again.  It may also be necessary to run **sudo nvidia-xconfig** to generate an xorg.conf file to start from before doing any editing in nvidia-settings.

Another option would be 'does the TV have an auto-adjust option'?  I know LCD monitors do, but I'm not sure if HDTVs do or not.  That might fix it without anything else needing to be done.

Yet another thing it could be, because it used to happen to me on my CRT monitors: the Hz value used for display can affect screen placement.  I usually have to drop the output to 60Hz to get the screen properly aligned.

---

