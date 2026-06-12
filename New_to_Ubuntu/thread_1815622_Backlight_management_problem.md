---
title: "Backlight management problem"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by nishant032 on 2011-07-31
I have been converted to Ubuntu since a week and I am totally in love with it apart one single thing: I have a backlight manaegement issue that makes my screen look like its refresh freq is too low. I have an Acer Aspire 4736Z.

The actual refresh freq is 60hz, can't go any higher (and doesn't need too) and here you have the output of 
```
lshw -C video
```
if it can be of any help.

```
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:90000000-903fffff memory:80000000-8fffffff ioport:6120(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:94400000-944fffff
```

Any idea/suggestion? Thanks

---

### Post by MyR on 2011-07-31
It will show the configured refresh rate in system > preferences > monitor

The backlight is always on, so it has nothing to do with the refresh rate.  If the backlight is flickering, that's an entirely different problem.

With integrated video card like yours, a slow system will cause the fps to decrease; perhaps you have some programs that are using too many resources.  Take a look in the system monitor to see if there is a program using a high % of the CPU.

And welcome to the world of open source software!  Hope this helps.

---

### Post by hreichgott on 2011-07-31
Is the brightness increasing/decreasing randomly? Acer Aspires have this power management "feature" that tries to save battery life by dimming the brightness whenever it thinks you don't really want to see your screen all that well. It seems to drive a lot of people crazy (including me.)

To turn off this feature:
1. Go to Preferences > Power Management and look at both the AC and Battery Power tabs. Make sure brightness is set to 100% and "Dim display when idle" and "Reduce backlight brightness" are all unchecked in both tabs.
2. Go to the control settings for your graphics card (for my Radeon card with Catalyst driver, it's Preferences > ATI Catalyst Control Center), find the power management settings and uncheck the "Vari-Bright" option.

---

### Post by nishant032 on 2011-08-02
@hreichgott

firstly the screen brightness is fine, it just goes dark before the screensaver starts, as it should be. personally having an Intel graphic card I couldn't find any app in my menu where i can disactivate that control. The only thing i could do was to disable the "power saving" thing in the Preferences > Power Management , the other I couldn't fin :(

any other idea? flickering is still happening

---

