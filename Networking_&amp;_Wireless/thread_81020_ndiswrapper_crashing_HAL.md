---
title: "ndiswrapper crashing HAL?"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by ooboontoo on 2005-10-23
I have had about as much trouble as anyone else installing a DWL G132 usb wireless on Hoary Hedgehog (or any other distro).

latest atempt is ndiswrapper, which worked great after installing all necessary kernel headers and gcc, but now when i boot with the usb card in, detecting network devices function fails, and I ctrl C out.  Then, after login, the screen freezes and says that HAL has failed.  

Another interesting phenomenon..
when i boot without the card in, it times out of detecting network devices, boots fine (minus the lag).
Then when I run ndiswrapper -l it gives the list of drivers present (those req'd) (all with card in after login).  but when i sudo modprobe ndiswrapper, the system lags (no response at all), and i ctrl c out again.  
here's the interesting part,  after that, i can no longer ndiswrapper -l, as it will lag as well.

WTF?

I'm rather new to linux, but learning fast.

any info you may need not given, just ask..

thanks

---

