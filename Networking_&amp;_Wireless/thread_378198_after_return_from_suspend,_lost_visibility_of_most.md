---
title: "after return from suspend, lost visibility of most routers"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by hardyn on 2007-03-07
edgy, using network manager.

after return from suspend, i seem to loose all but one wifi router in my area (there are a few), this is a new problem, and i cant figure out what i did to make it do this, i did recently disable blue tooth service, as i have no blue tooth hardware.

from restarts, everything seems to work normally, i am prompted for a keyring password.
and am able to connect no, problem.

after return from suspend, my normal view of 7-8 routers is reduced to just one, which i can still connect to, but its not mine a wish not to connect to it.

poking around in keyring manager, i am told that my keyring daemon is not running. while i don't think that this should upset my receiving of SSID info it is interesting just the same.

thanks for any help.

---

### Post by gradedcheese on 2007-03-07
I'm not sure about PAM and the keyring manager, but you could force your WiFi driver to reload and see if that helps (as a troubleshooting step).  Do you know what driver/chipset you have?  Once you know the module name,

1) 'disable wireless' in NetworkManager
2) sudo rmmod module_name
3) sudo modprobe module_name
4) 'enable wireless' in NetworkManager

---

### Post by hardyn on 2007-03-07
ipw2200

i will try that.

---

