---
title: "Help with Mobility Radeon 7500"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by Klogg4 on 2011-08-23
Hello,

I'm new to Ubuntu and and I just installed Ubuntu 11 on my older laptop to mess around with. I've been looking through the FAQs and the internets looking for help, but I've only gotten myself more confused.

I don't understand if my ATI Mobility radeon 7500 has been installed completely. Apparently the 7500 has a R100 core which is not compatible with the fglrx driver. The additional Drivers program does not detect anything to install. Do I need to install  the ati binary x.org driver?

How do I check to see if my video card is working? If it isn't installed how do i get it working. 

Thank you for all your help and sorry if this is a really easy fix.

Heres what I've found so far:

[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

[http://ubuntuforums.org/archive/index.php/t-32015.html](http://ubuntuforums.org/archive/index.php/t-32015.html)

---

### Post by LowSky on 2011-08-23
Those old ATI graphics cards are a thorn in the side of all Linux users. AMD cut off all support for these cards. And when the Kernel changed at one point drivers that were old stopped working. Because AMD would not open source the old driver Linux users were left in the dark.

---

### Post by gandaran on 2011-08-23
> **Klogg4 said:**
> Hello,

I'm new to Ubuntu and and I just installed Ubuntu 11 on my older laptop to mess around with. I've been looking through the FAQs and the internets looking for help, but I've only gotten myself more confused.

I don't understand if my ATI Mobility radeon 7500 has been installed completely. Apparently the 7500 has a R100 core which is not compatible with the fglrx driver. The additional Drivers program does not detect anything to install. Do I need to install  the ati binary x.org driver?

How do I check to see if my video card is working? If it isn't installed how do i get it working. 

Thank you for all your help and sorry if this is a really easy fix.

Heres what I've found so far:

[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

[http://ubuntuforums.org/archive/index.php/t-32015.html](http://ubuntuforums.org/archive/index.php/t-32015.html)
are you having any problems with the video card?
your Ati video card should work on ubuntu 11.04 with the default open source drivers, there aren't any others drivers to install as Ati doesn't support these old cards.

---

### Post by Mark Phelps on 2011-08-23
> **Klogg4 said:**
> How do I check to see if my video card is working? 
If you're seeing a graphical desktop, not a bunch of white text on a black background, your video card IS working.

And, as others have already told you, there are no drivers you can obtain for your card as AMD dropped driver support years ago.  

IF you try to force the install of any other drivers, you will only trash your display and have to go through a LOT of work to remove the drivers and replace them with what you already have in place.

---

