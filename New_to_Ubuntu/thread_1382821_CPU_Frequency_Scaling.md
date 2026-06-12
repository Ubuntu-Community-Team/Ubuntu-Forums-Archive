---
title: "CPU Frequency Scaling"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by herbertportillo on 2010-01-16
When I turn my computer on, the processor runs on the "Ondemand" setting by default. So my computer runs at 1GHz unless it needs to make the jump up to 1.8GHz or 2GHz due to the bigger strain on resources.

Is there a way I can change the processor's default operating frequency so that when I turn it on, it's always running at 2GHz? Any and all help is appreciated. Thanks.

---

### Post by warfacegod on 2010-01-16
I suggest checking your BIOS settings first. There may be a CPU scaling feature in there.

---

### Post by gradinaruvasile on 2010-01-16
> **herbertportillo said:**
> When I turn my computer on, the processor runs on the "Ondemand" setting by default. So my computer runs at 1GHz unless it needs to make the jump up to 1.8GHz or 2GHz due to the bigger strain on resources.

Is there a way I can change the processor's default operating frequency so that when I turn it on, it's always running at 2GHz? Any and all help is appreciated. Thanks.

Install the cpu frquency scaling monitor applet:
In a terminal:

```
sudo apt-get install gnome-cpufreq-applet
```

Then add it to your taskbar - right click, select it from the list. If you have 2 cpus add 2 monitor applets and select cpu0 on one and cpu1 on the other to monitor their frequencies. Basically every CPU core has to have its own monitoring applet - they can have different frequencies.

If you right click on the applet, you vill see all frequency levels and governors and can choose them yourself. Performance monitor is the one you want - that will keep the processor at full steam.

But i see nothing wrong in having it on ondemand - the speed steps up when needed, the computer consumes less power and the CPU is cooled better. 
If you have a laptop i strongly suggest leave it on ondemand.

---

### Post by herbertportillo on 2010-01-16
Yeah, I have that applet, and that's how I switch over to full processor use when I want that extra performance boost. The only thing is that when I turn on the computer, it starts on the "Ondemand" setting. I was wondering if there's some Terminal command I can type or some setting I can tweak so that when I turn it on, it's already on the "Performance" setting.

Oh, and I don't have a laptop. Regular desktop for me.

I also checked the BIOS, and the only processor setting that I can change there is whether to turn on or turn off "Cool n' Quiet" technology. I left than on. Even if I turned that off, I doubt the processor would run faster.

---

### Post by gradinaruvasile on 2010-01-16
There is a way:

On boot there is a script that sets the ondemand governor:

/etc/init.d/ondemand

move it out of the way (and in your home folder, it wont do anything just sit there, you can move it back if you want:

sudo mv /etc/init.d/ondemand $HOME/

restoring is:

sudo mv $HOME/ondemand /etc/init.d/

After moving the file reboot.

---

