---
title: "Epson ink monitor"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by LanceyD on 2010-03-10
Need help installing some sort of GUI to tell me what my ink levels are.  Epson D68 Ubuntu 9.10
Mtlink doesn't work.  Style toolbox doesn't work.  I'm in lp group, got that python thing.
Typical Epson, all ink in cartiges are pretty full when you shake it, so i'm not replacing all of them. 
Driving me mad, just need to flipping print.
And yes i've searched the forums, there are few with similar problems but makes no sense to me.  Isn't there a point and click fix?

---

### Post by philinux on 2010-03-10
Mtink works on my r200 and it's worked ok for other older epsons.

Does it spit out an error or just not give ink levels.

---

### Post by halitech on 2010-03-10
I found when I had my Epson I had to run Mtink with gksudo in order to get proper readings. Maybe try that and see if it works.

---

### Post by Scunnered on 2010-03-10
Mtink works well for me for my Photo R265.  It took a lot of head scratching and kind assistance from others but we got there in the end.

Have a look at [http://ubuntuforums.org/showthread.php?t=1148178](http://ubuntuforums.org/showthread.php?t=1148178) which I hope will assist.

---

### Post by LanceyD on 2010-03-10
@philinux, mtlink doesn't list any D series Epsons.  Ive tried a few others that I thought would be similar but it's not showing any ink levels.

@halitech, just tried running it with gksudo, but nothing happens.  Tried running it as root ans lp

@Scunnered, i read that thread before i posted.  That's what made me install mtlink in the first place.

I had an older install of Ubuntu (9.04) a little while back on a different machine and i managed to get a GUI ink monitor working on the same printer through the pinter properties, I just can't remember how, it must have been with the stylus toolbox, all I know is it took me most of the day and i was pulling my hair out.

I had to fire up the laptop on XP and plug in the printer to see which ones to replace, really didn't want to do that, but needs must and all that.  Would like to sort this for the future though.

---

### Post by philinux on 2010-03-12
> **LanceyD said:**
> @philinux, mtlink doesn't list any D series Epsons.  Ive tried a few others that I thought would be similar but it's not showing any ink levels.

@halitech, just tried running it with gksudo, but nothing happens.  Tried running it as root ans lp

@Scunnered, i read that thread before i posted.  That's what made me install mtlink in the first place.

I had an older install of Ubuntu (9.04) a little while back on a different machine and i managed to get a GUI ink monitor working on the same printer through the pinter properties, I just can't remember how, it must have been with the stylus toolbox, all I know is it took me most of the day and i was pulling my hair out.

I had to fire up the laptop on XP and plug in the printer to see which ones to replace, really didn't want to do that, but needs must and all that.  Would like to sort this for the future though.

Install escputil.

```
sudo apt-get install escputil

then run

sudo escputil -i -r /dev/usb/lp0 

```

---

### Post by LanceyD on 2010-03-13
> **philinux said:**
> Install escputil.

```
sudo apt-get install escputil

then run

sudo escputil -i -r /dev/usb/lp0 

```

Thanks, that worked, gave me a text readout of the levels :D

Still bugging me how I managed a GUI readout last time.  I've marked the thread as SOLVED because I now have a readout, but still want to find another solution.

Bloody Epson, I had trouble with a brand new scanner too.  Anyway, thanks all.

---

### Post by arvevans on 2012-01-18
**escputil -i -r /dev/usb/lp0** does not work in 11.10 because there is no /dev/usb/lp0.  Instead, you just let it find the printer on it's own.
This works with my 11.10 Ubuntu and an Epson CX7400 connected via USB. 
For newer printers you do have to use the -u option.

---

