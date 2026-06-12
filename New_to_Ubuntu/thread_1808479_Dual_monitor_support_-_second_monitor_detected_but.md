---
title: "Dual monitor support - second monitor detected but wont display"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by akbuddy on 2011-07-20
A quick question (hopefully) for the smart people out there...

I have been using Ubuntu for a couple years now and have been loving it. I recently upgraded to 11.04 and my notebook monitor works fine, but the second monitor that I have it connected to will not display. Under Monitor Preferences, it is detected and on, as it has always been. Checked it with another computer and the connection is fine.

Why is the second monitor detected but not displaying??

I am running a Dell Inspiron 1520 with integrated graphics card. Worked in 10.10/10.04/etc.

Any help would be greatly appreciated

---

### Post by Hoopz on 2011-07-20
You may have to hit a certain key combination on your notebook to send the signal out to the monitor. Try holding your fn key down and pushing f8

---

### Post by seawolf167 on 2011-07-20
As Hoopz said, see if there is a keystroke to enable the dvi/vga output from your laptop. It'll be something like [Function][F*something*]. It usually looks like a little hollow rectangle.

---

### Post by akbuddy on 2011-07-20
> **Hoopz said:**
> You may have to hit a certain key combination on your notebook to send the signal out to the monitor. Try holding your fn key down and pushing f8
Thanks for the suggestion. But hitting the Fn+F8 key merely changes my resolution to that of my second monitor (1024x768 ) without displaying anything on the second monitor. I have also tried rebooting in Ubuntu classic mode and disabling Unity, to no avail. Any other ideas?

---

### Post by akbuddy on 2011-07-20
I have performed an exhaustive search of this problem and it seems I am not the only one with an Intel graphics card with dual monitor display problems. Is it possible that I will need to load earlier software? I would try that, but I don't know which piece of code is causing this problem...

---

### Post by seawolf167 on 2011-07-20
Do you have any available drivers for your graphics card you can install? Click the power icon in the upper right, select system settings, then see if there are any drivers available under additional drivers.

---

### Post by akbuddy on 2011-07-20
Yes, I tried that. The only available driver is a 'Broadcom STA Wireless Driver'. I'm assuming this is for my WiFi connection, but it is disabled. I have also fully updated my system with the most recent recommended and pre-release updates and have looked in the Synaptic Package Manager for any other Intel graphics releases (there were lots so not all were installed). 

If you are aware of any other place I can download a more up-to-date driver it's something I was looking for but could not find. However, why would it have worked before the update to Natty?

---

### Post by eltonw on 2011-07-20
> **akbuddy said:**
> A quick question (hopefully) for the smart people out there...

I have been using Ubuntu for a couple years now and have been loving it. I recently upgraded to 11.04 and my notebook monitor works fine, but the second monitor that I have it connected to will not display. Under Monitor Preferences, it is detected and on, as it has always been. Checked it with another computer and the connection is fine.

Why is the second monitor detected but not displaying??

I am running a Dell Inspiron 1520 with integrated graphics card. Worked in 10.10/10.04/etc.

Any help would be greatly appreciated

IF this is of any help ....

With the *other* monitor connected and turned ON: Go to Applications => Themes and Tweaks =>Monitors. 

:arrow:*[COLOR="Green"]_Enable_[/COLOR]* the following:

[COLOR="Green"]Same image[/COLOR] on all monitors / [click on] [COLOR="Green"]Detect[/COLOR] monitors

[COLOR="Green"]Mirror Screens[/COLOR] = On [Select the resolution and refresh rate, do a test and save the one that displays correctly.

[COLOR="Olive"]**FWIW:**[/COLOR] I have used the above method to display my Asus EEE 1000 PC netbook on my 32" LCD HD TV. When I have the netbook connected, the only 'downside' is that the display does not fill its 10" screen. 
But that's no problem, since I'm using the TV screen as the 'main display'.

HTH....

---

### Post by akbuddy on 2011-07-20
Still no worky. I had a similar workaround with 10.10 and 10.04, but at the very least the monitor would come on with a reboot. Or it would come on when I started a movie.

For what it's worth, when I do not have the monitors set to the same resolution ('same image in all monitors'), the laptop will only select 60Hz and the other only 30Hz. Not sure what that means.

As you can see from the screenshot, when the second monitor is plugged in and both are set to max resolution, they are still both detected. I can move stuff over to the second monitor, but it just wont show. And it seems weird enough that 'printscreen' reveals both monitors...

---

### Post by anibalrojas on 2011-08-31
I am running Ubuntu 11.04 with both a Nvidia and an integrated Intel AGP in my laptop.

I am using an external monitor connected through a mini DisplayPort wired to the Intel card. It has been working since I installed Ubuntu 11.04 a month a go, today the external monitor stopped responding:

 - The external monitor reports no sync 
 - System > Preferences > Monitors reports the external monitor as attached and operational.
 - Print Screen includes the image of the external monitor
 - The laptop primary monitor works as expected.

After double checking the cables, connections and the external monitor I booted back in the previous Kernel (I suppose yesterday I got an kernel update) and the external monitor came back to life. I did the test forth an back a couple times and the behavior was consistent.

The offending Kernel is 2.6.38-11-generic.

Last known good Kernel is 2.6.38-10-generic.

So far I am sticking to the previous Kernel while using an external monitor.

Following are my graphics device info:

    anibal@collar-de-bolas:~ $ lspci | grep -i VGA
    00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)

    anibal@collar-de-bolas:~ $ sudo lshw -C video
    [sudo] password for anibal: 
      *-display               
           description: VGA compatible controller
           product: nVidia Corporation
           vendor: nVidia Corporation
           physical id: 0
           bus info: pci@0000:01:00.0
           version: a1
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
           configuration: driver=nouveau latency=0
           resources: irq:16 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
      *-display
           description: VGA compatible controller
           product: 2nd Generation Core Processor Family Integrated Graphics Controller
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 09
           width: 64 bits
           clock: 33MHz
           capabilities: msi pm vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irq:54 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)

---

### Post by anibalrojas on 2011-08-31
I just filled a bug for this, please go and check it if it applies to you:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838181](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838181)

---

