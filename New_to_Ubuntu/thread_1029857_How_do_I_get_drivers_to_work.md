---
title: "How do I get drivers to work?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by risingpowers on 2009-01-03
My screen resolution is stuck at 800x600. I've downloaded and installed the proper driver for my Intel 4 Series chipset through Synaptic Package Manager, but nothing shows up in Hardware Drivers. Xorg.conf says that I'm using the vesa driver.

---

### Post by risingpowers on 2009-01-03
Alright, maybe the title question is a bit noob-ish, but seriously, how do I enable drivers? I downloaded and installed them, and they're not doing anything...

---

### Post by risingpowers on 2009-01-03
Shameful bump.

---

### Post by HotShotDJ on 2009-01-03
Exactly WHAT "drivers" did you install using synaptic?  Intel video does not require any proprietary drivers, and therefore does not show up in Hardware Drivers (I really, REALLY wish that developers would change the name of that application so that it reflects what it actually is used for).

---

### Post by risingpowers on 2009-01-03
> **HotShotDJ said:**
> Exactly WHAT "drivers" did you install using synaptic?  Intel video does not require any proprietary drivers, and therefore does not show up in Hardware Drivers (I really, REALLY wish that developers would change the name of that application so that it reflects what it actually is used for).

xserver-xorg-video-intel

---

### Post by HotShotDJ on 2009-01-03
> **risingpowers said:**
> xserver-xorg-video-intelOk... have you restarted the xserver (or rebooted) since doing that?  If not, then do that first.

Next, I'd like you to open a terminal (Applications --> Accessories --> Terminal) and type```
xrandr -q
```and post the output.

---

### Post by risingpowers on 2009-01-03
Yes, I've rebooted the computer since the installation.

> Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0 

---

### Post by HotShotDJ on 2009-01-03
> **risingpowers said:**
> Yes, I've rebooted the computer since the installation.Hmmm... this is quite odd.  If you really do have an Intel accelerated graphics card, it should be detected.  What version of Ubuntu are you using?

---

### Post by risingpowers on 2009-01-03
> **HotShotDJ said:**
> Hmmm... this is quite odd.  If you really do have an Intel accelerated graphics card, it should be detected.  What version of Ubuntu are you using?

Ubuntu 8.10 (Intrepid)

---

### Post by HotShotDJ on 2009-01-03
Ok... quite honestly, I'm still perplexed.  Intel on-board video controllers should "just work."  Unfortunately, I'm going out with some friends, so I can't spend the time to see if we can get this solved.  But don't despair, other will be along, and I'll check back in when I get home.

---

### Post by risingpowers on 2009-01-03
I'm checking all of the necessary documentation to see if there's anything I can do myself, thanks for bothering with this thread. :D

---

### Post by risingpowers on 2009-01-03
I changed the xorg.conf file so that it matched what it SHOULD read (according to the driver README), and when I booted the system I got a white screen with gray dots that gradually changed to a dark gray. I suppose that's not really progress...

---

### Post by unutbu on 2009-01-03
Take a look at this thread: [http://ubuntuforums.org/showthread.php?p=6471949#post6471949](http://ubuntuforums.org/showthread.php?p=6471949#post6471949)
and in particular, Bigbob22's suggestion:
[http://ubuntuforums.org/showpost.php?p=6471846&postcount=6](http://ubuntuforums.org/showpost.php?p=6471846&postcount=6)

---

### Post by risingpowers on 2009-01-03
> **unutbu said:**
> Take a look at this thread: [http://ubuntuforums.org/showthread.php?p=6471949#post6471949](http://ubuntuforums.org/showthread.php?p=6471949#post6471949)
and in particular, Bigbob22's suggestion:
[http://ubuntuforums.org/showpost.php?p=6471846&postcount=6](http://ubuntuforums.org/showpost.php?p=6471846&postcount=6)

Thank you, but Bigbob's first suggestion did nothing and I can't find the program mentioned in his second suggestion.

---

### Post by risingpowers on 2009-01-03
Shameful bump.

---

### Post by unutbu on 2009-01-03
Do you perchance have an Intel GM45 graphics card?
If so, take a look at 
[http://ubuntuforums.org/showthread.php?t=946035&page=2](http://ubuntuforums.org/showthread.php?t=946035&page=2)
[http://www.claudiocamacho.org/?id=200812141525](http://www.claudiocamacho.org/?id=200812141525)

If you have this card, then I or others here at the forums can try to help you through the solution described at claudiocamacho.org. I have to go to sleep now, but I can try to help you tomorrow if no one picks this up before then.

---

### Post by risingpowers on 2009-01-04
> **unutbu said:**
> Do you perchance have an Intel GM45 graphics card?
If so, take a look at 
[http://ubuntuforums.org/showthread.php?t=946035&page=2](http://ubuntuforums.org/showthread.php?t=946035&page=2)
[http://www.claudiocamacho.org/?id=200812141525](http://www.claudiocamacho.org/?id=200812141525)

If you have this card, then I or others here at the forums can try to help you through the solution described at claudiocamacho.org. I have to go to sleep now, but I can try to help you tomorrow if no one picks this up before then.

It's an Intel 4 Series Express adapter, that's all I know. Nowhere do I see "GM45" on my system.

---

### Post by risingpowers on 2009-01-04
"sudo lshw -C display" yields this:

```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

---

### Post by MenZa on 2009-01-04
If you were a bit more descriptive when posting in your thread, it might be easier to help - for instance, where did you get the content from your latest post?

---

### Post by risingpowers on 2009-01-04
> **MenZa said:**
> If you were a bit more descriptive when posting in your thread, it might be easier to help - for instance, where did you get the content from your latest post?

I typed this...

```
sudo lshw -C display
```

...into Terminal.

---

### Post by unutbu on 2009-01-04
risingpowers, have you been able to get back to a 800x600 graphical display, or are you still experiencing the white screen / gray dots? It appears you are able to get to a terminal, since you posted "lshw" output. Did you press Ctrl-Alt-F2 to get to a text terminal, or is the graphical display with the white screen semi-usable?

If you look in /etc/X11 there might be a backup copy of your old xorg.conf.
If you rename the backup xorg.conf, log out, then log back in, you might be able to restore your 800x600 display.

If you want assistance doing this, just ask.

You should also take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=946035](http://ubuntuforums.org/showthread.php?t=946035)

It appears that as of October of 2008, Intrepid + Mobile 4 Series Chipset Controller was unable to display at a resolution greater than 800x600. 

Of course, it never pays to believe whole-heartedly posts which say something is impossible (unless we're talking about math proofs :) ). It may just be the posters don't know the solution. Or maybe the state of affairs has changed since October. 

I'll keep looking, but at this point, I don't know.

---

### Post by risingpowers on 2009-01-04
> **unutbu said:**
> risingpowers, have you been able to get back to a 800x600 graphical display, or are you still experiencing the white screen / gray dots? It appears you are able to get to a terminal, since you posted "lshw" output. Did you press Ctrl-Alt-F2 to get to a text terminal, or is the graphical display with the white screen semi-usable?

If you look in /etc/X11 there might be a backup copy of your old xorg.conf.
If you rename the backup xorg.conf, log out, then log back in, you might be able to restore your 800x600 display.

I you want assistance doing this, just ask.

You should also take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=946035](http://ubuntuforums.org/showthread.php?t=946035)

It appears that as of October of 2008, Intrepid + Mobile 4 Series Chipset Controller was unable to display at a resolution greater than 800x600. 

Of course, it never pays to believe whole-heartedly posts which say something is impossible (unless we're talking about math proofs :) ). It may just be the posters don't know the solution. Or maybe the state of affairs has changed since October. 

I'll keep looking, but at this point, I don't know.

I created a backup before I modified my xorg.conf file. Once I replaced it with the backup in Terminal I was able to get 800x600 again, but this isn't the problem. The problem is that I'd like to display a resolution greater than 800x600.

---

### Post by risingpowers on 2009-01-04
If I search Google for this without any mention of the drivers, I see that there's many others having this problem. I'm downloading 9.04 Alpha 2 right now as that seems to have helped a few others.

---

