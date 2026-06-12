---
title: "Screen Resolution Problems"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by dameanone on 2009-04-10
Hello All!

New convert to Ubuntu, so I am an absolute noob. I cannot, no matter what I do change my screen resolution from 640x480 (4:3). It is so frustrating as I am running Ubuntu on a monitor that ran XP in a resolution of double that. Please help me out, this zoomed in view is killing me!

---

### Post by sahabcse on 2009-04-10
Hi

Select System>>Preference>>screen resolution

---

### Post by dameanone on 2009-04-10
Ok, I probably should have said I have tried that. The drop down menu will give me no other option.

---

### Post by Malalo on 2009-04-10
What do you see in System -> Administration -> Hardware Drivers ?
Do you see a "deactivated" driver for your video card ? If yes, try to activate it, then reboot.

---

### Post by dameanone on 2009-04-10
No Drivers are in use on this system.

---

### Post by dameanone on 2009-04-10
Is that a bad thing if no drivers are detected?

---

### Post by CatKiller on 2009-04-10
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by dameanone on 2009-04-11
Thank your for the reply. I brought up the xorg.conf as instructed but where do I input values? Again I have never used Ubuntu so I am unfamiliar with this.

---

### Post by CatKiller on 2009-04-11
> **dameanone said:**
> I brought up the xorg.conf as instructed but where do I input values?

They go in the "Monitor" Section, like so:

Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

Once you've saved the changes, Ctrl-Alt-Backspace will restart X so the changes can take effect. Don't forget to save anything that you want to before you press those keys, though.

---

