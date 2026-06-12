---
title: "NVidia GeForce 8200M G not working"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by josepria on 2011-04-12
Hello,

Not extremely familiar with Linux installing Ubuntu 10.10 and I just can't get my graphics to show correctly (3D rendering), When I installed Ubuntu everything looks decent with the generic driver but video is lagging and decent games wont even load correclty (tried guild wars using wine and the background animation didn't even move until I closed it). I downloaded the additional driver that popped up to download and my screen was divided in six little screens with my desktop on each one. I tried changing the display settings but it doesn't let me, max is 480X..., I re-installed ubuntu and now downloaded the driver from nvidia's website with the same result, I re-installed ubuntu and downloaded the rest of the updates and installed the nvidia drivers and the additional drivers and still, same result.

PLEASE HELP!!! I'm out of ideas and I really don't want to go back to windows again, it's the third time that I've tried linux and I always end up with an issue like this, but third time's the charm and with a little help I'm sure I'll be able to get this going with a little help from you guys.

By the way, I'm installing this in a Notebook HP Presario CQ60-418DX

Any help will be really appreciated thanks in advance...

---

### Post by earthpigg on 2011-04-12
instead of going to nVidia's website, try:

1) use tools provided by nVidia's website download to uninstall/undo whatever the stuff from their website did. it is fairly important that you undo ***everything*** done by the stuff form nVidia's website.
2) system -> administration -> additional drivers ***only***. 
3) if ***only*** using the official 'additional drivers' doesn't work, say so and we will go from there.
4) get out of the habit of going to a website to download software. often, in ubuntu, that will get you into trouble. we have about a dozen different and really good ways of finding/installing software on ubuntu, but the old 'go download from website' is very often utter crap.

---

### Post by josepria on 2011-04-13
This one the first attempt that I did, only this without going to the NVIDIA website, after that, I installed and downloaded all the updates before attempting to download this version, with the same result.
On my third attempt is when I actually went to the NVIDIA website for the driver...

I really don't know what else to try here.

Thanks for the help.

---

### Post by earthpigg on 2011-04-13
google is telling me that that video card has given many people headaches.

given that you have already tried their website, here is what my next approach would be:

system -> administration -> synaptic.

search for 'nvidia'.

i would then uninstall whatever "nvidia-___" stuff i currently had installed, and try other stuff. i would do this with the full realization that it may break the system, so i'd have my stuff backed up.

---

### Post by deconstrained on 2011-04-13
> **josepria said:**
> I really don't know what else to try here.
How about this: hit Alt-F2, enter the command "gksudo jockey-gtk". You get a nice, easy interface for finding and installing proprietary drivers.

> **earthpigg said:**
> we have about a dozen different and really good ways of finding/installing software on ubuntu, but the old 'go download from website' is very often utter crap.
It all depends on what you're installing.

Software drivers are better grabbed from repos because they've been tested and packaged and padded for easy installation and compatibility.

Apps like TrueCrypt, on the other hand...

---

### Post by josepria on 2011-04-13
Thanks, I'll give it a go tonight once I get out of work and see what happens, I'll keep you guys posted and hope that it works...

---

