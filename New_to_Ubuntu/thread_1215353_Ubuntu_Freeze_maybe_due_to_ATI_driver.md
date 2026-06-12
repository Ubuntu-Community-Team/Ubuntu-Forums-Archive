---
title: "Ubuntu Freeze maybe due to ATI driver?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by jestonb on 2009-07-17
I have an old laptop that I wanted to make the plunge and install ubuntu on.  Its a Sony Vaio PCG-K17.  The install went perfect every thing started up then about 5 minutes in everything froze, I did a hard shut down and logged back in only to have the same thing happen.  After some reading it sounds like it might be the video driver.  The Sony has an ATI Technologies Inc Radeon IGP 330M/340M/350M video card.  I have tried to run the envyng update of the ATI driver and I have tried to download the driver from ATI, but the laptop freezes before I can download the entire driver.  

Am I on the right path?  Is there something else that I should check?

Thanks

---

### Post by nhasian on 2009-07-17
you didnt mention which version of ubuntu you were using.

try going to system->administration->software sources, then click on the updates tab, then tick the box for unsupported backports.  if there is a newer video driver, it will appear in the system->administration->hardware drivers for you.

---

### Post by binbash on 2009-07-17
Did you try to boot with different kernel to see if it is kernel related? Also turn off wifi, bluetooth while you are testing.

---

### Post by jestonb on 2009-07-17
Sorry forgot that part, its Jaunty Jackalope Ubuntu 9.04.  I tried to get the new updates but it froze before they could be downloaded.  Wifi is off.  Any ideas?

Thanks

---

