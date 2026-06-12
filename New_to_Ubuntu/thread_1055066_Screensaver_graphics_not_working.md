---
title: "Screensaver graphics not working"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by vhegos on 2009-01-30
Hi all,

My screensaver recently stopped working.  Unfortunately, I did not notice immediately, so I do not know what I did that corresponds to the time it stopped working.  I have a hunch it is when I installed the edubuntu desktop.  Now I cannot make any screensaver work.  After the set time, the screen goes black and locks, but the graphics are not present.  I do not even get the graphics for the preview of the selected screensaver in the System-> Preferences -> Screensaver configuration window.  I appreciate any suggestions.  I miss BioF.  

Thanks!!

---

### Post by dorkdork777 on 2009-01-30
Are your desktop effects still working?

---

### Post by vhegos on 2009-01-30
That makes me realize that I had switched from the nvidia driver to the nv driver.  Switching back solves the problem.  The question now becomes 'What is the point of the nv driver?'

Thanks!

---

### Post by dorkdork777 on 2009-01-31
IIRC, the nvidia driver is closed-source and provides 3D accelleration, so you can use the full potential of your card. However, since it's closed source and not as well maintained as the Windows version, there's still some bugs we need nVidia to fix.

The nv driver, on the other hand, is the opposite - no 3D accelleration, but it's open source and has quite a few less bugs. This is the default one, but it's recommended to later install the nvidia driver.

However, there's a group of people working on a third driver - [nouveau]("http://nouveau.freedesktop.org/wiki/") - which, when completed, will provide the best of both worlds. 3D accelleration, open source. It's not ready yet, though - it's working better than the nv driver for some configurations, but not working at all for others. 3D support is still under heavy development.

---

