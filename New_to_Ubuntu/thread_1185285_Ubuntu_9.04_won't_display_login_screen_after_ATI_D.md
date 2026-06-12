---
title: "Ubuntu 9.04 won't display login screen after ATI Driver upgrade using Envy..."
date: 2009-06-12
forum: New to Ubuntu
---

### Post by winx2linx on 2009-06-12
Hi,
My system's screen display looks garbled after I updated the ATI Display driver.
I did a clean install of Ubuntu 9.04,applied all the updates, and then searched for the display driver in the Synaptic Manager. But I didn't find anything regarding ATI driver in Synaptic.
So I searched on the internet with the query "Install ATI Display Driver in Ubuntu 9.04" and came to a page where it says that it is very easy to install the driver using Envy.
Then I installed Envy and after firing up Envy, it asked me to choose 3 to install ATI Driver and then 0 to install it. I did and after the installation finished, it asked me to restart the system.
I restarted, and now the system's not well... Every time, I restart,after the initial Ubuntu bootscreen of a booting where a yellow/orange line passes from left to right, the screen doesn't shows anything. It has some red patches on the top and some yellow/green patches below that...

My system config is AMD  64 X2 5000+, 2GB RAM, onboard ATI X1200 Card...

Please help me...

Thanx in Advance and GOD Bless...

---

### Post by rogueleader12345 on 2009-06-15
When you boot, try selecting "Safe graphics mode". I had the same problem.

---

### Post by winx2linx on 2009-06-16
Thanx mate...
Thanx for the reply...

I uninstalled the driver in terminal using envyng -t command...

Now the desktop's back, but the resolution is 800x600 and I am not able to configure it using display properties...

Thanx for Your inputs...
Bye n GOD Bless...

---

### Post by Mark Phelps on 2009-06-17
Just in case you try to reinstall the ATI driver ... you guys had the same problem because AMD/ATI has dropped support for older video cards from their drivers, and the last version of their drivers that WILL work with the cards won't work in Ubuntu 9.04.  I would have hoped that Envy would have detected this conflict, but apparently it did not.

---

### Post by phroggz on 2009-07-14
so will there be any solution to this anytime soon??? or where could i ask for more help? i have the same problem (and the same computer configuration) that win2linx has. well, i did, then i did a complete system reinstall. i haven't used ubuntu in quite some time, but then this computer isn't all that old, there should be better support for this graphics card, shouldn't there?

the main problem is, whenever any 3d processes are activated, my cpu usage skyrockets, slowing down everything and not even looking that good. the drivers i used on windows were pretty good, so i reckon those for linux might be updated soon?

thanks for any feedback :D

---

