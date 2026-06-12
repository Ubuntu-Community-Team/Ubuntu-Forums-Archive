---
title: "Adjusting webcam colours."
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Pauho on 2009-04-30
Hello, since I've installed Ubuntu (first 8.10, now 9.04) my Acer Aspire One, my webcam colours have been all out of whack. Rather than describe it I'll just post an image from Cheese:

[IMG]http://farm4.static.flickr.com/3577/3489182524_3463d7bf6c_m.jpg[/IMG]

As you can see, apart from the grusome subject, something is wrong. I've been searching for programs to help with this, but so far no luck. Camorama doesn't connect to the webcam.

Any ideas?

Thanks in advance,
Paul

---

### Post by Melk79 on 2009-04-30
I ran into almost the exact same problem and was able to fix it by adjusting the settings in Totem, oddly enough.  See my old [thread]("http://ubuntuforums.org/archive/index.php/t-813636.html").

Final post:
June 1st, 2008, 10:36 PM
I have found a temporary fix to this problem. When the problem originally surfaced, the Color Balance setting sliders for Totem (Under Edit>Prefrences>Display) all lined up in the middle.

After a log off and power down for the night, I found the hue bar to be at far left in the morning. The picture output was not fixed. When I hit the Reset to Defaults button, the hue slider moved back to the middle with the rest of the settings, but when I slid it back left the picture corrected. This also fixed the color on Cheese and Skype. So, video looks good again, but I still don't know what happened and how to permanently fix it. Doesn't this seem strange? Why are these programs pulling settings from the same place, but Ekiga isn't?

This actually turned out to be a permanent fix.  It happened again a month or two ago and the same fix worked.  Let us know!

---

### Post by spiderbatdad on 2009-04-30
I don't know what happened to /etc/modprode.d/options in jaunty, but I think you can create the file now, but append it with .conf so...
create the file as root, /etc/modprobe.d/options.conf and try adding something like:
```
options v4l2 gamma=50
options v4l2 GRed=290
options v4l2 GGreen=310
options v4l2 GBlue=315
``` You will need to reboot. This should not cause any fatal errors, but I don't know if it will work for you.

---

### Post by Pauho on 2009-05-08
For some reason the hue slider is no coming up on the Totem Pref's screen. Despite searching on forums, checking Synaptic for a plugin and reinstalling Totem, this still isn't coming up. 

Any idea why that should be the case?

---

### Post by Pauho on 2009-05-10
Also, spiderbatdad: I worked up the courage to go mucking about with modprobe. I created the file options.conf and tried adding the data you suggested. Didn't work. I tried changing the colour values to 200 for each, but still no change.

v4l2 - Is this video for linux? Is there a way to make sure that the webcam is using this?

---

### Post by Pauho on 2009-05-29
*bump*

Still struggling away with this? Does anyone else have a solution?

---

### Post by mpsz on 2009-08-24
I have the same problem, I tried with different webcams in different computers with ubuntu and none of them worked right.
The colours and the image simply sucks.
Any help with this? Where can I configure the webcam settings? Like colours, contrast, hue, etc...

---

