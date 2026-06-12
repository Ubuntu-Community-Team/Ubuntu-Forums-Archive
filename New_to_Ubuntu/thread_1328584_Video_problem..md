---
title: "Video problem."
date: 2009-11-16
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-11-16
Hi Guys,

I have sadly installed a program in order to activate the external monitor (my TV), when I restarted the system I got the screen divided into 4 sections, its all tilted and I cant see anything in order to uninstall the crap I recently installed.

Is there a way of reseting the video driver from the terminal? Or is there anything else smart you can recomend?

Would love some help!! 

I have tried to reboot with and without the cable inserted but that did not help...

I have a SONY VAIO W series netbook, so no NVIDIA card to consider.

Cheers.
Anders

---

### Post by ohzopants on 2009-11-17
What program did you install that did this?

Do you have an xorg.conf file?  To find out try:
```

locate xorg.conf

```
and look for one in the /etc/X11/ (95% sure, on a windows pc now so can't check) directory

If you have one can you tell us what's in it?  Just paste it here.

---

### Post by lover_of_sc on 2009-11-20
Hi mate,

Thank you for your response, already managed to get it back to normal. I did find the program I installed (multi screen application) and uninstalled it with my 10inch screen which was divided into 6 different smaller screens with a horrible tilt... :-P

Not the easiest of a task... :-)

---

