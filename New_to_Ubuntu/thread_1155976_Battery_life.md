---
title: "Battery life"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by darrel_h on 2009-05-11
I downloaded the ubuntu netbook remix onto my msi wind u100, removing widows xp.  Since then, it seems I actually get less battery life than I did before.  I have the 3 cell battery (that's what it came with and I haven't bought a 6 cell yet).  I have the 1.6 Ghz processor and downloaded the applet to adjust it's perfomance, but even on power save it still seems to only run about an hour and 15 minutes, maybe.  Does anybody have any suggestions?  
 
I think something may be affecting the firefox too, cause it takes a long time for pages to fully load when they have all that crap loading on the side bars.  Anyone know how to optimize that too?  Please remember I am a beginner to Linux, so please be patient.  If you need further info, i'll try to get it for you.  Thanks in advance for all your help.

---

### Post by Kosimo on 2009-05-11
Did you try powertop?

```
sudo apt-get install powertop

```

and then run it:
```

sudo powertop
```


Once you have it opened, it suggest you to enable some extra power saving features by hitting the right word.


It does works well for me

---

### Post by Kosimo on 2009-05-11
More information about powertop

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

[http://en.wikipedia.org/wiki/PowerTOP](http://en.wikipedia.org/wiki/PowerTOP)

---

### Post by pauna on 2009-05-11
> **darrel_h said:**
> I downloaded the ubuntu netbook remix onto my msi wind u100, removing widows xp.  Since then, it seems I actually get less battery life than I did before.  I have the 3 cell battery (that's what it came with and I haven't bought a 6 cell yet).  I have the 1.6 Ghz processor and downloaded the applet to adjust it's perfomance, but even on power save it still seems to only run about an hour and 15 minutes, maybe.  Does anybody have any suggestions?  


It is true that Linux power management is not yet as efficient as Windows' tools. However, I'm getting something like 4 hours from my EEE PC 901 with Jaunty NBR, so your 1hour+ seems very odd, it should be more like 2 hours even with a 3 cell battery.

So I second the use of powertop to see what hogs the battery juice. Do you have the ability to switch off some devices you're not using?

---

### Post by LowSky on 2009-05-11
running the PC with full brightness, WIFI on, Bluetooth on, steaming video, or accessing hte hard drive constantly is going to lower power consumption

With a 3 cell you should get about 2 hours. Also not running proper charging cycles with the battery can effect it. Remember to run a battery from full charge to about 10% before recharging it for a few times. Newer batteries have to "learn" and the more they are used the less you will get out of them.

---

### Post by darrel_h on 2009-05-11
thanks for the help.  i downloaded and ran power top but it doesn't seem to be doing much good.  it had me change the "wake up from idles" seconds from 5 to 15, now it wants me to enable usb suspend, but i use a usb mouse on this tiny machine, so i don't think it's letting me.  and my battery is still saying it's only gonna last 1hr 5min, and i just unplugged it from being charged all day.  i took a screenshot but now i don't know how to attach it to this reply.  if anyone thinks it'll help in giving me some advice, please let me know how to attach it.  thanks again.

LowSky, as for your reply, thank you.  i've actually had the netbook for quite some time and the battery used to last about 1hr 30 to 45 min, on average, but i did unplug it when i got home and i'm going to try your trick.

---

### Post by darrel_h on 2009-05-11
ok, so in addition to my last post, i unplugged the usb mouse, restarted my machine and it's still telling me a usb device is in use 100% of the time, gives me the option to enable usb suspend, but just keeps going in circles when i do, any suggestions?  also, i noticed that after i restarted and ran the power top again, it had me make the same changes as my last post, is this normal, that it doesn't save the changes?

i also looked at my lsmod and i can't make heads or tails from it.  other than the mouse, i am not connected (intentionally) to any outside devices other than my wireless router, so how can i check to make sure it's not trying to load a printer or cd rom or anything like that?  and if it is, how do i stop it?

---

