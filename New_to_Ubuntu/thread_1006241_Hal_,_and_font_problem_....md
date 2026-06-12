---
title: "Hal , and font problem ..."
date: 2008-12-09
forum: New to Ubuntu
---

### Post by stevoo on 2008-12-09
Hey all,

i am writing a script to do something. Long story short, i am using Xvfb in order to run a headless operation.
I do it with this command :
    [PHP]DISPLAY=:99.0
	nohup Xvfb :99 -ac & ${src}/runTests.sh[/PHP]

but i end up getting this error that perhaps do not let my script run headless. 
[PHP]Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
nohup.out (END) 
[/PHP]

About the fonts, there is no /fonts/X11/cyrillic folder. How can i include that in ? And how can i find what hal is complaining about ? 

-sTevoo

---

