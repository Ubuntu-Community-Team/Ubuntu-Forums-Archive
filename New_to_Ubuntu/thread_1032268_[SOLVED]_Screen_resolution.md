---
title: "[SOLVED] Screen resolution"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by garrydog on 2009-01-06
Hi
I am trying to load this driver ,ati-driver-installer-8-12-x86.x86_64.run .
I have got as far as the ATI install panel .But the screen is so large I can't hit the next button as my display is locked in 800x600 .I have tried hitting the tab and enter ,but this will not work .Can someone help please .Thanks

---

### Post by orlox on 2009-01-06
I also had problems with bad screen resolution, but with nvidia drivers. To solve them, I activated a program called "pantallas y graficos" in spanish. It should translate as "screens and graphics". To activate it, go to system->preferences->main menu, and under others, look for this program (or something with a similar name, I dont remember the exact name for it in english). Also, under applications you need to check "other". Then you can access this application from the applications menu.

I don't remember precisely how that thing was used, but is pretty intuitive...

hope this helps

---

### Post by linux_tech on 2009-01-06
Can you access the terminal?

If so, type ```
xrandr -q 
```
What are the available resolutions?
If there is a 1024x768 there then you can type```
xrandr -s 1024x768
```
and the screen should change to this
you can also run ```
xvidtune 
```

to temporarily adjust to screen so can run the ATI install program.
You can use synaptic to install the driver also if you are not able to use the ATI program.

---

### Post by grainbarcelona on 2009-01-06
I had de same problem, with Nvidia. When I try to change the screen resolution, the answer is:
"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

The xrandr command in terminal mode returns error as well

Any advice on what I should do?

tnx

---

### Post by B34ST1Y on 2009-01-06
> **garrydog said:**
> Hi
I am trying to load this driver ,ati-driver-installer-8-12-x86.x86_64.run .
I have got as far as the ATI install panel .But the screen is so large I can't hit the next button as my display is locked in 800x600 .I have tried hitting the tab and enter ,but this will not work .Can someone help please .Thanks

try editing your xorg.conf file to properly adjust your display settings

---

### Post by kestrel1 on 2009-01-06
If you are using Ubuntu 8.04, then Screens & Graphics helps. Unfortunatley in Ubuntu 8.10 this has been removed (very big mistake IMHO)
I gave up trying to sort it out in 8.10 & copied the xorg.conf file from my 8.04 system that has similar hardware. From what I have seen 9.04 will have something that will be a bit more useful. I think it boils down to the monitor not being detected correctly. Mine isn't because I am running it through a KVM switch as I have more than one machine setup.

---

### Post by donkyhotay on 2009-01-06
I've had this getting my radeonX700 card working. It's like a can opener inside of a can type issue. You're probably using the VESA drivers for now which only goes up to 800x600 so editing xorg.conf doesn't help. In order to get better resolutions you install the drivers but the driver installer is designed to work at a resolution of 1024x768 so you can't see the screen, specifically the 'ok' button in order to install them. Well, at least this is what happened to me the last few times I installed the ATI drivers directly from their website. How I worked around it was just pressing 'enter' on my keyboard after choosing the options I needed for my system. This allowed me to get through the menu system and install my drivers. The ATI drivers work well for my system but their installer setup has to be one of the stupidest things I've ever seen as it only works if you have working drivers (and if you have working drivers why are you running the installer).

---

