---
title: "Changing mouse and touchpad options?"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Bogdanovist on 2009-03-26
I need to customise my mouse and touchpad options but what I want to do is not encompassed by the GNOME preferences (i.e. System -> Preferences -> Mouse). 

From searching these forums there are a lot of posts giving advice on how to change aspects of mouse behaviour through the xeorg.conf file, however it also appears to be the case that in ubuntu 8.10 this functionality is largely deprecated. So, what is the mechanism through which customisation now takes place?

FYI what I want to do is separately map the left/right buttons on my mouse and touchpad but changing the preferences in GNOME changes both together, there is no way to control them independently. I'm happy to play around in the guts of the OS to try and work out how to do this, I just need to know where to start looking.

Any advice would be appreciated.

---

### Post by Nepherte on 2009-03-26
Input devices are now configured with hal fdi files instead of with xorg.conf. More information can be found here:
[https://help.ubuntu.com/community/SynapticsTouchpad#Configuration%20with%20HAL%20fdi%20files](https://help.ubuntu.com/community/SynapticsTouchpad#Configuration%20with%20HAL%20fdi%20files)

---

