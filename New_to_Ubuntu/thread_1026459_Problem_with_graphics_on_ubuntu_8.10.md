---
title: "Problem with graphics on ubuntu 8.10"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by whoney on 2008-12-31
Hi Guys, 

First post for me and I am hoping someone out there can help me. I am not a complete newbie to Linux/Unix as I have been using it at work on and off for the last 10 years. 

I am trying to get my desktop machine at home setup to dual boot between WinXP and ubuntu. I managed this last year with the 7.10 release of ubuntu but never got the internet connection running as apparently there is a problem with the driver for the (Realtek 8139RTL) ethernet controller on my motherboard. 

So, over the last few days I have set about reinstalling WinXP and installing the latest version of ubuntu (8.10). Initiatially I was attempting to upgrade from 7.10 > 8.04 using the "alternate CD" but I had problems with that also.

Anyway ... the current status is that for some reason I cannot get the 8.10 live CD to boot on my machine. The rough specs are: AMD CPU 1.9GHz'ish, 512MB, GeForce1 Pro (nVidia) video card and old Iiyama Vision Master Pro 410 17" monitor.

I have been attempting to boot ubuntu from the live CD initially to check that the network driver problem is resolved ... however I cannot even get this far as just after the african music plays on boot the monitor sits there just flickering between video modes with just a black screen.

I have tried the same CD in this laptop I am using now and it boots just fine so I am guessing this is some kind of video setup problem ...

Any ideas folks?

TIA
Wayne

---

### Post by billgoldberg on 2008-12-31
> **whoney said:**
> Hi Guys, 

First post for me and I am hoping someone out there can help me. I am not a complete newbie to Linux/Unix as I have been using it at work on and off for the last 10 years. 

I am trying to get my desktop machine at home setup to dual boot between WinXP and ubuntu. I managed this last year with the 7.10 release of ubuntu but never got the internet connection running as apparently there is a problem with the driver for the (Realtek 8139RTL) ethernet controller on my motherboard. 

So, over the last few days I have set about reinstalling WinXP and installing the latest version of ubuntu (8.10). Initiatially I was attempting to upgrade from 7.10 > 8.04 using the "alternate CD" but I had problems with that also.

Anyway ... the current status is that for some reason I cannot get the 8.10 live CD to boot on my machine. The rough specs are: AMD CPU 1.9GHz'ish, 512MB, GeForce1 Pro (nVidia) video card and old Iiyama Vision Master Pro 410 17" monitor.

I have been attempting to boot ubuntu from the live CD initially to check that the network driver problem is resolved ... however I cannot even get this far as just after the african music plays on boot the monitor sits there just flickering between video modes with just a black screen.

I have tried the same CD in this laptop I am using now and it boots just fine so I am guessing this is some kind of video setup problem ...

Any ideas folks?

TIA
Wayne

Use the alternate cd to install Ubuntu.

---

### Post by wolffkrieger on 2008-12-31
Does it show a black screen or are you able to see the desktop but at a wrong resolution?

I had a problem like this when I first insalled intrepid. No matter how I did it, via live cd or upgrade from 8.04. At setup (with live CD) the screen resolution would be too high for my monitor, thus I was not able to distinguish anything (menus, options, prompts, etc.).

I googled for some help but never found anything. What I did was to memorize the location of the Screen Resolution menu. Once the live CD had booted I would open de Applications menu, move to System (from Applications it's 2 taps on the right arrow keys). One arrow key down (Preferences), one arrow key right (goes into Preferences menu) then two taps on the s key (opens Screen Resolution. Here I would go to the select resolution dropdown list and select a low resolution and clic on the apply button. This fixed the resolution problems.

When installed if the resolution is bad at startup just fill in username and password, once logged in the resolution should be good (if not repeat steps above, you'll only need to do this once). My graphics is a Radeon HD 2600, once I activated the restricted driver with the Hardware Drivers menu I found that the login screen's resolution was fixed.

---

### Post by Hydrid on 2008-12-31
I had the same problem and the solution was to install 8.10 from the cd with no graphics support in the beging of the installation.When u boot from the cd it has an option (i think its f4)to choose to install with generic graphics driver.Hope this helps you.

---

### Post by whoney on 2008-12-31
Thanks for the replies guys. :)

> **wolffkrieger said:**
> Does it show a black screen or are you able to see the desktop but at a wrong resolution?

It's just a black screen. The monitor is just constantly switching between BNC and D-SUB inputs presumably trying to find an input signal.

Interestingly, booting v7.10 as a Live CD (which I never tried before) the graphics and the network (!) both work first time.

---

### Post by whoney on 2008-12-31
> **Hydrid said:**
> I had the same problem and the solution was to install 8.10 from the cd with no graphics support in the beging of the installation.When u boot from the cd it has an option (i think its f4)to choose to install with generic graphics driver.Hope this helps you.

I have just had a look and yes, if you select F4 there is an option to install "Safe graphics mode". I will give this a try. Thanks.

---

### Post by whoney on 2008-12-31
OK, the system is now installing in safe mode ... thanks chaps :D

I will leave this thread "unsolved" for now in case I need any more help with setting up the graphics/driver once the install is complete.

---

### Post by whoney on 2008-12-31
:(

Well, the installation using the alternate CD did not go well. I am not sure what happens but I tried it twice and on both occassions the install failed and the Live CD booted. 

So, I decided to give the v8.04 Live CD a go. I managed to get this installed using the text based installer but now I cannot get the graphical login to load at all ... just a black screen.

Any suggestions on how I fix this?

The graphics card is a Creative Labs Geforce 1 Pro (CT6971) 16MB and the monitor is a 17" CRT Iiyama Vision Master Pro 410.

:confused:

---

