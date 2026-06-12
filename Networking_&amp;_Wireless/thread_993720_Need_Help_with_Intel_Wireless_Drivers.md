---
title: "Need Help with Intel Wireless Drivers"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by snakeDoctor88 on 2008-11-26
I posted something about this before and didn't get much help, but now I've made some more progress and found I need to update my wireless drivers(i think).

I have a Dell XPS M1530 with an Intel 3945 card.
My kernel version is 2.6.24-21-generic.

First off, the results of iwlist scan whether my wireless is switched on or off is:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

I honestly don't know what this is telling me.  Under the assumption that I need to update my drivers, I headed to [http://intellinuxwireless.org/](http://intellinuxwireless.org/) which lead me to [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) to get the latest iwlwifi driver.

Unfortunately in reference to kernels 2.6.24 and up it says "These kernels have the iwlwifi driver included and the released drivers (available from this site under download page) do  not work with these kernels.":mad:

So I'm completely in the dark.  Any help would be greatly appreciated.

---

### Post by TFX360 on 2008-11-26
[http://ubuntuforums.org/showthread.php?t=140085]("http://ubuntuforums.org/showthread.php?t=140085")

Should get you on your way!

---

