---
title: "application window size"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by paulstenlund on 2009-03-04
My applications and setup screens are opening larger than my desktop and I can't move them up. This means I can't click "apply" at the bottom of the setup/config window. How can I reduce or change the size

Thanks
Paul

---

### Post by binbash on 2009-03-04
can you try this please : 

compizconfig settings manager > workarounds plugin > untick legacy fullscreen support

---

### Post by paulstenlund on 2009-03-04
installed compizconfig and unticked workaround - windows still come up to big. Actually compizconfig came up to big and I had to use mouse wheel to get to workaround the elevator bar was off the screen to the right

OOPS - I unticked Workaround - I went back and opened workaround and unticked Legacy full screen support and reticked Workaround - I'll try it now - thanks for the response

---

### Post by paulstenlund on 2009-03-04
Windows are still larger than the desktop

---

### Post by Therion on 2009-03-04
Have you logged out and logged back in after un-ticking the "Legacy Fullscreen Support" box?

---

### Post by paulstenlund on 2009-03-04
Just restarted the machine - compizconfig still coming up bigger than window and off to the right - can't drag it to the left either

---

### Post by cjv8888 on 2009-03-04
> **paulstenlund said:**
> Just restarted the machine - compizconfig still coming up bigger than window and off to the right - can't drag it to the left either

This may not make the windows smaller but if you open a terminal and type

gconf-editor

then

navigate to apps/compiz/plugins/move/allscreens/options and uncheck constrain_y

This will allow you to grab the window with Alt+left mouse button and move the top of the window above the screen.

Then you can access the buttons at the bottoms of the windows.
Hope this helps.

---

### Post by blueridgedog on 2009-03-04
You can hold down the "alt" key and click anywhere on the window and drag it so you can get to the buttons you need.

---

### Post by paulstenlund on 2009-03-04
Bluerigdedog

That will certainly help

CJV888

That should solve the immeadiate problem


Thanks guys

This is an awesum operating system

---

### Post by paulstenlund on 2009-03-05
any new ideas?

---

