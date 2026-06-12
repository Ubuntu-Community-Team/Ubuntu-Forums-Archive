---
title: "Xvfb question ..."
date: 2009-01-14
forum: New to Ubuntu
---

### Post by stevoo on 2009-01-14
i had managed to make a headless session for Xvfb in order to run some tests on my machine.

But i am having problems currently when i am trying to move it onto a server running 6.04. 

There is no X installed there, and my IT installed Xterm for me to use. 
I unable to make Xvfb working using Xterm. I am wondering if someone knows what X does Xvfb required in order for it to work .


i get the following errors when i try to startup Xvfb on my server
```
*****:~/tmp/test$ Xvfb :99 -s 0 -screen 0 1680x1024x24
Couldn't open RGB_DB '/etc/X11/rgb'
error opening security policy file /etc/X11/xserver/SecurityPolicy
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Could not init font path element /usr/share/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/X11/fonts/75dpi/, removing from list!
FreeFontPath: FPE "/usr/share/X11/fonts/misc/" refcount is 2, should be 1; fixing.

```

---

### Post by kironnk on 2009-08-05
Where you able to fix the issue. I have a similar problem.

I am getting the below error while trying to run Xvfb. I also see that /usr/X11R6/lib directory doesn't exist. Can you please help me out.

(WW) Could not open RGB file "/usr/X11R6/lib/X11/rgb.txt"; will use built-in copy.
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
Thanks
Kiron

---

