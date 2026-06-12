---
title: "Changed monitor, display corrupted"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by thornate on 2009-01-25
I recently changed the monitor on my computer and now the display is corrupted; the colours are all off. Take a look at the attached picture - that's the default Ubuntu desktop pic behind the dialog. It's difficult to see in the picture but the dialog itself is not the right shade of grey and the text is difficult to read because it varies in colour from white to grey to black.

My graphics card is an ATI Radeon 3850. I had not been using the drivers for it because videos do not show properly when I do. Installing the drivers via the Hardware Drivers dialog fixed this problem (though this now means that I can't watch videos).

Does this make sense to anyone that by merely changing the monitor, the display can become corrupted like this? Is there any way to fix this without using the graphics card driver?

---

### Post by starcannon on 2009-01-25
Does the ATi driver have its own xconfigurator?(I use Nvidia)
If so run that.
If not you could try:
```

sudo dpkg-reconfigure xserver-xorg

```post back if that didn't work. I'm sure one of us will be able to help you solve it.

---

### Post by thornate on 2009-01-25
How do I tell whether it has an xconfigurator? What would it do?

I fiddled with the settings in  dpkg-reconfigure xserver-xorg but it didn't change anything.

---

### Post by tsali on 2009-01-25
> **thornate said:**
> How do I tell whether it has an xconfigurator? What would it do?

I fiddled with the settings in  dpkg-reconfigure xserver-xorg but it didn't change anything.

What does "I fiddled with the settings in dpkg-reconfigure xserver-xorg but it didn't change anything" mean? That's a simple command line string. What settings?

Try this:

Uninstall the ATI drivers. There is a text based graphical package manager called "aptitude" that can help you. Simply type:

```
sudo aptitude
```

Looked under installed programs to find your ATI driver package, then remove it (follow prompts and menus)

Once those are removed, reconfigure the xserver again as follows:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Hopefully, you will get a serviceable image. If so, THEN REBOOT. (some will say this isn't necessary, but it works to reinitialize all services correctly)

Once rebooted, install the ATI drivers.

---

### Post by thornate on 2009-01-25
Yup, had already done all of the above. There was only one setting that had anything to do with video (the rest were to do with the keyboard) and I tried both options and rebooted. 

BUT 

It's irrelevant now anyway. Some hardcore googling actually managed to solve my video problem (which is apparently common with some ATI cards and Compiz). So now I'm working fine with the driver. Thanks anyway.

---

