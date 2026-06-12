---
title: "Hardware Drivers Dialog Hangs when I press Activate"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by coldReactive on 2009-09-29
I have an nVidia GTS 250, and when I press Activate in the hardware drivers dialog in Kubuntu, it just sits there and does nothing. ubuntu installs fine, and doesn't hang like this, but I don't want to go back to ubuntu.

---

### Post by Hospadar on 2009-09-29
I've noticed this problem before too.  For whatever reason, I find if I resize the window and change the size of the description window a little before I hit accept I get much better results.

If that doesn't work you can always install the packages directly through synaptic or the command line.  You want the nvidia-glx-<some number> packages.

---

### Post by coldReactive on 2009-09-29
> **Hospadar said:**
> I've noticed this problem before too.  For whatever reason, I find if I resize the window and change the size of the description window a little before I hit accept I get much better results.

If that doesn't work you can always install the packages directly through synaptic or the command line.  You want the nvidia-glx-<some number> packages.

Would be nice if synaptic didn't require all of that gnome stuff. apt-get search is not a valid command either.

---

### Post by coldReactive on 2009-09-29
searched in kpackagekit, and found them and installed them but... it still says they're not activated, and the dialog still hangs.

---

### Post by coldReactive on 2009-09-29
Abandoning KDE and will try Xubuntu next. I just don't want to be caught up with GNOME-Shell *shudder*

---

### Post by Rogue dog on 2009-10-15
This is solved very easy, see this post from the kubuntu forum, credit to leafhound.


> I have read back and know people are having issue with this, even if you click on the activate button nothing happens. however installing these drivers from the package manager or from Nvidia website is not the same.


So go to- Applications / System / Hardware Drivers

this pops up the window for your root pass, enter it

then the window with the activate button appears

now before I press on anything see the recommended driver in the window is highlighted in blue, this is in a small window within the main window, we need that small window to have a blue highlight around it before clicking on the activate button. and be sure to have internet connection up.

To do this click on the recommended driver until the highlight appears then we are ready to activate. see picture.

[img]http://i.imagehost.org/0792/NVidia.png[/img]

hope this helps

---

### Post by coldReactive on 2009-10-15
That's what I first tried back when I had Kubuntu 9.04, Rogue Dog, it didn't work.

Resizing the window didn't work either.

---

### Post by Rogue dog on 2009-10-15
> **coldReactive said:**
> That's what I first tried back when I had Kubuntu 9.04, Rogue Dog, it didn't work.

Resizing the window didn't work either.


Is there a recommended driver in the window box and what distro version did it not install?


when the activate button is pressed jockey-kde retrieves the driver from the source (net)

If it works in Ubuntu that's because it's jockey-gtk, you could install that and replace jockey-kde

I think it's 
```
jockey-gtk --replace
```

---

### Post by coldReactive on 2009-10-15
> **Rogue dog said:**
> Is there a recommended driver in the window box and what distro version did it not install?


when the activate button is pressed jockey-kde retrieves the driver from the source (net)

If it works in Ubuntu that's because it's jockey-gtk, you could install that and replace jockey-kde

I think it's 
```
jockey-gtk --replace
```

I'll give that a whirl in 9.10 if 9.10 fails me like it did 9.04.

---

### Post by hoppipolla on 2009-10-16
Aww I hope this works man, KDE really is wicked and I would vastly recommend it over XFCE personally. Keep at it :)

---

### Post by praveesh on 2009-10-16
> **hoppipolla said:**
> Aww I hope this works man, KDE really is wicked and I would vastly recommend it over XFCE personally. Keep at it :)

The latest drivers from the nvidia web site is sufficiently stable(there's a beta version though) . That didn't crash not even once . Installing that one from the terminal will automatically activate the driver  . No need of further activation and no need of jockey . There's already a thread  about installing the drivers directly from nvidia . And if you want to get performance as well as desktop effects, you will probably need the latest driver. Hopes this helped.

---

### Post by coldReactive on 2009-10-16
> **praveesh said:**
> The latest drivers from the nvidia web site is sufficiently stable(there's a beta version though) . That didn't crash not even once . Installing that one from the terminal will automatically activate the driver  . No need of further activation and no need of jockey . There's already a thread  about installing the drivers directly from nvidia . And if you want to get performance as well as desktop effects, you will probably need the latest driver. Hopes this helped.

What DM does KDE use? Obviously not GDM. I have instructions written down for how to install the binary (7 steps in all.)

One of the lines is to turn off GDM via **/etc/init.d/gdm stop**, but what would it be for KDE?

---

### Post by lovinglinux on 2009-10-16
I had this issue with jockey not being able to complete. So I went to Adept and installed nvidia-185-kernel-source, nvidia-185-modaliases, nvidia-glx-185 and nvidia-kernel-common, then rebooted.

It worked.

> **coldReactive said:**
> What DM does KDE use? Obviously not GDM. I have instructions written down for how to install the binary (7 steps in all.)

One of the lines is to turn off GDM via **/etc/init.d/gdm stop**, but what would it be for KDE?

**/etc/init.d/kdm stop**

---

