---
title: "touchpad works but not listed in xorg.conf or preferences"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by aleph.charles on 2009-07-05
I recently solved a problem that I was having, and I haven't seen any other posts anywhere on the web describing this problem or the solution. In case my solution is useful to any other neophytes, I thought I would post it here.

I just started using ubuntu (hardy heron) on a refurbished laptop, and ran into the hover click issue. None of the advice I ran across for turning off hover click helped, because the touchpad didn't show up in system -> preferences -> mouse or in the default xorg.conf. The touchpad worked fine, but xorg.conf only had a mouse entry, but no touchpad entry. Making changes to the mouse entry, and even adding a touchpad entry had no effect. After a while of trying various options in xorg.conf and trying to figure out how to get SHMConfig to work, I finally tried running the command listed at the top of the xorg.conf file to regenerate the default xorg.conf. 

 sudo dpkg-reconfigure -phigh xserver-xorg

When I ran this, the newly generated xorg.conf file contained a touchpad section and, after rebooting, the system -> preferences -> mouse interface included a touchpad section, where I was able to turn off touchpad clicking. I haven't tried modifying the xorg.conf to use any of the other tricks for turning off only hover clicking, but at least my system does now recognize its touchpad as a touchpad.

I never did get SHMConfig to work properly (I still get 
:~$ sudo synclient -l
Can't access shared memory area. SHMConfig disabled?
)
but everything seems to be working okay, so I'm not sure if I need it.

---

### Post by LewRockwell on 2009-07-05
you might add information on your equipment for future reference

while it's not mandatory to put such information in the title area, it sure makes it easier for others

to wit, note:

title: "help me please" equals FAIL

title: "Dell Inspiron 6000, Broadcom bcm43XX chipset, kubuntu 6.04 wireless problems" equals MUCH BETTER!

as always, your mileage may vary, buyer be aware and beware...

.

---

