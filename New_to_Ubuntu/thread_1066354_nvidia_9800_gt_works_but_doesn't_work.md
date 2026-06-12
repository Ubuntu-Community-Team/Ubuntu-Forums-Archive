---
title: "nvidia 9800 gt works but doesn't work"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Rrasyrogenees on 2009-02-10
i originally was using an 8600 that got fried due to overheating (i live in a hot area and i added two fans afterwards to prevent this from happening again).  i put my older card back in which was having problems of it own but it kept working for a few weeks while i waited for the finances to get this new card (yet my old card did allow me to play WoW but the graphics would spike here and there and at inappropriate time... like fighting).  i bought an nvidia GeForce 9800 GT and since then i have not been able to play WoW.  i am not sure it is the card that is a problem as much as WoW and wine.  my NVIDIA X Server Settings seems to mean that it is working fine but i am not savvy on what things i am supposed to be looking at and what they mean anyway.

Operating System:   Linux-x84_64
NVIDIA Driver Version:  177.82


anyway, what i am experiencing is when i try to start WoW i get the opening window to click on "play", after i do that it changes my resolution and give me a garbled (if that is a good word for the graphics being all mixed up) window and then the WoW "what were you doing when it crashed" window comes up... any ideas or suggestions?

i have tried starting a new ubuntu os on my harddrive to use for wine only (and the programs that need it) after that it still is giving me trouble.  so it makes me wonder if the card is a problem or if i am the problem... see how WoW can make you crazy when not playing?   lol

---

### Post by cariboo on 2009-02-10
It looks like Nvidia hasn't built a new Linux  driver for your video card yet. There was a new driver released today,  you can get it [here]("http://www.nvnews.net/vbulletin/showthread.php?p=1927376"), but it doesn't look like there is any support yet.

Jim

---

### Post by Rrasyrogenees on 2009-02-10
i need a third party driver... anyone out there got an extra they can spare?

---

### Post by RomeReactor on 2009-02-10
Hi. As far as I know, the 9800 GT is [supported in the nVidia 180 series]("ftp://download.nvidia.com/XFree86/Linux-x86_64/180.11/README/appendix-a.html") drivers, including the one found in Intrepid's repositories; so if you have Ubuntu 8.10 you can search for **nvidia-180-modaliases** and **nvidia-glx-180** in Synaptic.

---

### Post by Rrasyrogenees on 2009-02-10
ok... thanx RomeReactor and i did find the drivers and installed them.  WoW still gives me the "what the f*** did you do to screw up this time" window, but at least my graphics weren't changed like before (resolution stayed the same and i didn't get the scrambled window with it... i didn't have to force quit WoW this time as well).  is there something else i may be missing here?

it was suggested to me earlier by a computer shop worker that what is happening is that wine wants to run the show and maybe it is not letting my card work properly.  if i knew how to tweak things i would be doing much better i think.

so, now i get the opening window then i get the crash window... still no WoW for me :cry::-({|=

---

### Post by RomeReactor on 2009-02-10
I don't play WoW, but try running it from the terminal; if you get error messages, please post them so more people can see them. Meanwhile, maybe this [troubleshooting documentation]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting") page can help. Also, try searching the [Wine section]("http://ubuntuforums.org/forumdisplay.php?f=313") of the forums; there are many Warcraft threads.

---

