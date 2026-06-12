---
title: "sluggish laptop"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by fugative on 2007-02-03
I have edgy on a HPzv5000 pavilion laptop and all was well until I got the wireless working. I did fwcutter and ndiswrapper methods, fwcutter didn't work but had the same side-effect as ndis; It made my machine sloooow! The spash screen hangs around for about 5 minutes after the the tool bars have loaded and it takes 3-5 minutes to get any program to start, I can go and make a cup of tea and come back to find openoffice or a terminal still not open. I checked the system monitor and there is no abnormal ram or cpu usage and only spikes when the program finally opens. Could it be hardware... no it doesn't do it with XP. It has an additional 512Mb of ram taking it to a total of 768 with 128 used by the graphics. 
Conflict? I've blacklisted the broadcom drivers, at least enough to make the ndis work, and it does get the full 11mbps that the bcm4303 is capable of although loading the pages is slow due to the problem. 
I'm on the verge of putting XP back on the thing if I can't solve it. An hour-and-a-half battery is no good when loading openoffice takes 5 minutes, and this is not an exaggeration.

I know someone can put me on the trail of the answer.      

Cheers

What stats do i need to post for a diagnosis.

---

### Post by jimbren on 2007-02-03
I don't know much about fwcutter, but if you installed the Ubuntu package, I would consider removing the package altogether, and then running apt-get fix to try and repair any broken or orphaned packages. 

From a terminal:

```
sudo apt-get remove --purge bcm43xx-fwcutter
```

then 

```
sudo apt-get install -f
```

This is kind of grasping at straws, but it can't hurt.

Please post back, I'm very curious to know how this ends up for you.

jimbo

---

### Post by fugative on 2007-02-04
No, completely fresh install. I've formatted this machine i don't know how many times over the last two months. Orphaned packages and the like are probably the problem but I can't find what and it's driving me spare. I set up my main machine *Shuttle XPC*  and I've spent more time working on it than with it. I so want total deGATESfication but if i can't get it working at least the laptop will have to get rewindowed. The *XPC*  is going well although i still have a few bits that don't work, scanner webcam etc. 

cheers for the suggestion

... and if I'd known about the purge command i might not have formatted  quite so often.

---

### Post by jimbren on 2007-02-04
but I was thinking that fwcutter install might have broken a package or something.  Probably grasping at straws, but it might be worth trying.  

jimbo

---

### Post by fugative on 2007-02-05
Nah, don't think so. FW left so much clutter in the firmware folder that i did a format and started clean. I didn't want to take any chances, you know with this Linux stuff the smallest thing can throw everything out of sinc. 

keep your thinking cap on Jim, mines got holes in it now.

cheers for the interest

---

