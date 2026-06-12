---
title: "Unity Display problem"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by mtangoo on 2011-05-03
Hi, I have been long using Lucid and I upgraded to Maverick. No problem. The same day I upgraded to Natty and while installing upgrades it did broke at samba4. After it was done I run apt-get upgrade --fix-broken and it did some stuff. Now I have two problem for days now: 1. During login and after login the display is cropped. Some part of display is not just used. windows in that case becomes smaller 2. If I rearrange Unity launcher (remove and add some program) and then reboot, I lost all configuration and everything reset to default  Help please

---

### Post by 23dornot23d on 2011-05-03
When you run this in a terminal 

[B]/usr/lib/nux/unity_support_test -p
 [/B]

what does it show you ...... ( just as a start to see what you have graphics wise )

heres mine


keith@keith-Aspire-7730ZG:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9300M GS/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

---

### Post by mtangoo on 2011-05-03
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

---

### Post by 23dornot23d on 2011-05-03
Try using the kdm desktop manager .....

It just gives you a different login process ..... 
( we can always change back to gdm if its no good for you )

sudo apt-get install kdm

choose kdm when it  asks ...... then reboot


> 
Now I have two problem for days now: 1. During login and after login the display is cropped. Some part of display is not just used. windows in that case becomes smaller 2. If I rearrange Unity launcher (remove and add some program) and then reboot, I lost all configuration and everything reset to default Help please


My reason for asking you to change desktop managers is ....

The machine is possibly running in the wrong resolution , what tends to happen running gdm is it just stops you and drops you into safe-mode from what I am seeing ...... on my own setup ....

When running kdm ..... it allows the graphics to work ok ...... in
some situations (like my own systems).

_____________________________________


I just want to see if you get the same problem or if it goes away .....

If it does not work .... or solve the problem you have ....

sudo apt-get remove kdm

choose gdm when it asks ...... then reboot

Will get you back to the gdm login as you had before .

---

### Post by mtangoo on 2011-05-03
No success. I ended in console and restarted and chose ubuntu and then screen went black. now I'm removing it. Thanks for help!

---

### Post by mtangoo on 2011-05-03
Any help/Suggestion? The problem is making life harder

---

### Post by 23dornot23d on 2011-05-03
I found a link here ..... [COLOR=Red]**[Link]("http://ubuntuforums.org/showthread.php?p=10711665")**[/COLOR] .... seems others have had problems too .....

but cannot see a good solution yet - 

I did a search and looked through some of the **[ links]("http://www.google.com/search?client=ubuntu&channel=fs&q=GM45+Express+Chipset+GEM+20100330&ie=utf-8&oe=utf-8")**

main problems seem to be with lagging and speed more that the size .....

but you may find more information doing searches on 

**[GM45 Express Chipset GEM 20100330 Solved]("http://www.google.com/search?client=ubuntu&channel=fs&q=GM45+Express+Chipset+GEM+20100330+solved&ie=utf-8&oe=utf-8")**

unless someone else thats had this problem on one of the links can help you
my main dealings have been with Nvidia .... so I am a little lost myself here
I always used to look for solutions with the xorg.conf file ..... as this was 
used to control the graphics settings .....

---

### Post by mtangoo on 2011-05-05
I tried different things (every option I could find) at failsafe and delete all config files I could fine (I mean compiz, compiz-1, conf). It works mostly.
Major problem is, I cannot save launcher settings. Each time I customize unity and reboot, all settings are gone. Iam lost!!!

---

