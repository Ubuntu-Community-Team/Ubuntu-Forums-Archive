---
title: "Problem with updating Flash"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by rgs962 on 2009-08-09
I was trying to update my computer yesterday and encountered a problem while installing the updates. During the installation of the updates the Flash update would not finish. After some time, I decided to stop everything and start over. When I tried to update again, the Update Manager said the everything was up to date. I then hit the "Check" button and in the error box it gave me this:

  E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to open the Synaptic Manager, but it gave me the same error as the text above. 

I am using Ubuntu 9.04. 

I would appreciate any help that I can get to put my computer back to normal. None of the video applications work.

Thanks in advance for any help.

---

### Post by taurus on 2009-08-09
Shut down synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by rgs962 on 2009-08-09
Taurus............thanks for the input, everything seems to be working fine.


rgs962

---

