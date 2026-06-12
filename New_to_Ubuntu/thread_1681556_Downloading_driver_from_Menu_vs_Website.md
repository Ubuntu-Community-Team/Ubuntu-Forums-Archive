---
title: "Downloading driver from Menu vs Website"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by maciej234 on 2011-02-04
Whats the difference between downloading ATI drivers from "additional drivers" via Ubuntu or thru downloading a driver from ATI's website?  I'm guessing one is open source and one is closed source.  I have a ATI HD 5670 card by the way.

---

### Post by Paqman on 2011-02-04
Neither are open source. Using the "Additional Drivers" tool means you're using the package manager to install the drivers, which means that kernel updates won't break your graphics.

---

### Post by quadproc on 2011-02-04
> **maciej234 said:**
> Whats the difference between downloading ATI drivers from "additional drivers" via Ubuntu or thru downloading a driver from ATI's website?
The last time that I tried to use the Ubuntu driver installation method, it did not allow me to choose which version.  Going to the ATI/AMD website allowed me to choose.  I have not checked recently so maybe this problem has gone away.

Being able to choose was crucially important when Ubuntu went from version 8.X to 9.X - X windows changed dramatically between those Ubuntu releases and the old and the new versions were completely incompatible.  You *had* to have the correct driver version or your graphics was dead.

I have read that Ubuntu will be discontinuing X windows in about a year and using a new graphics manager called Wayland.  I am not sure what the impact of this will be, but I think that it would be wise to choose a driver rather than letting someone else make the choice.

BTW, the recent ATI driver package is about 120 MB in size.  This might be important if you have a low bandwidth connection, or if you are charged for bytes transferred.  The open source driver is part of the release so it won't cost extra.

I am currently running the open source driver on this system but there is some kind of a problem which occasionally corrupts the screen at login time.  When I use the fglrx driver (ATI's proprietary driver) then I do not see this problem.  See launchpad bug 711056.

quadproc

---

