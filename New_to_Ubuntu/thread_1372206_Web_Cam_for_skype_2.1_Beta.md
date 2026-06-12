---
title: "Web Cam for skype 2.1 Beta"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by uaebuntu on 2010-01-04
I'm using 9.10 on various platforms.

After several tries with different usb webcams from Phillips and Genius which were supposed to be Linux compatible and upgrading from LTS to 9.10 I can get my webcam

Bus 002 Device 004: ID 0ac8:332d Z-Star Microelectronics Corp. Vega USB 2.0 Camera

to work with Cheese but not with Skype Beta 2.1.0.47. Can anybody suggest what I need to do differently to get it working?

---

### Post by Methuselah on 2010-01-04
If it works with cheese it should probably work with skype.
Did you check your skype settings to ensure skype video is enabled and the right device is selected?

You should click the skype logo at the bottom of the main window and select options then video options on the left.
Make sure 'enable skype video' is checked and also that the webcam is the selected video device in the dropdown.

Apply your settings.

There should be a box with a 'test' button.
Test the webcam.

---

### Post by prshah on 2010-01-04
> **uaebuntu said:**
> 
to work with Cheese but not with Skype Beta 2.1.0.47. 

If you are getting a scrambled / discoloured / solid blue / solid green image, try this command from the terminal (Applications-Accesories-Terminal)```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```

If it works, you can create a custom launcher for this. Please post back if you want more details.

---

### Post by laidback on 2010-01-04
I'm using 9.04 but the last time Skype got upgraded via Synaptic updates the mic stopped. Might not be the answer but this may help:-

[http://ubuntuforums.org/showthread.php?t=1306561&highlight=skype](http://ubuntuforums.org/showthread.php?t=1306561&highlight=skype)

(solution, revert to previous version)

---

### Post by uaebuntu on 2010-01-05
I checked my skype settings, video enabled and correct webcam selected.

Pressed the test button and test screen still black, button would not press again

tried the LD_PRELOAD but that made no difference.

---

### Post by uaebuntu on 2010-01-06
Tried the final suggestion which was to downgrade to Skype 2.0. Still blank (black) video screen in Skype options after [test] button pressed.

Cheese still works so camera is OK.

---

### Post by mbzn on 2010-01-06
Are you sure cheese is completely closed when starting skype? it could be that one program(cheese) locks the device and the other(skype) cannot access it.

---

### Post by uaebuntu on 2010-01-06
Cheese was not opened when testing skype so there should not have been any conflict. Have checked in System Monitor and can't see anything else that might conflict.

Even with skype as only application open after clean restart then there is still nothing.

---

### Post by encompass on 2010-01-07
I too have the same cam, 0ac8:332d, and it works in cheese but not skype.  It does work in skype in 9.04 but not in 9.10.  So you could install that and it would work fine.  That is what my wife is doing.

---

### Post by uaebuntu on 2010-01-07
Solved, bought another Philips camera, works with everything. Thanks to everyone for the help

---

### Post by encompass on 2010-01-07
This issue has been brought up with skype.  Hopefully they can fix it.  It seems to be something with the new kernel.
Also, could you provide information about the cam?  I would love to see a picture of the box here as well.

---

