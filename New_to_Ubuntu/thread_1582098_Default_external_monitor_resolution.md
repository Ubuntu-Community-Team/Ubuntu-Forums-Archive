---
title: "Default external monitor resolution"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by rkakkar on 2010-09-26
Hi,

I have hooked up an external monitor to my laptop. My laptop has a max resolution of 1280x800 and my external monitor has a max resolution of 1920x1080.

now in display settings i have disabled my laptop's display and set my external's resolution as 1920x1080.

however whenever i reboot, although my laptop display is still disabled (which i want), my external monitor resolution is set to 1280x800 (which is my laptop's max) and i have to manually set it back to 1920x1080.

any idea how i can fix this?

---

### Post by JohnHeikkila on 2010-09-26
Where do you set the settings? If your laptop has a nVidia graphics card, you will be able to save the settings to Xorg.conf file. See screenshot.

[IMG]http://img205.imageshack.us/img205/307/nvidiasettingsscreensho.png[/IMG]

---

### Post by rkakkar on 2010-09-26
> **JohnHeikkila said:**
> Where do you set the settings? If your laptop has a nVidia graphics card, you will be able to save the settings to Xorg.conf file. See screenshot.

]

Nah .. I go to kde's display settings and set it up. Check the attached screenshot. I have a HP Compaq 6720s with inbuilt Intel graphics I think.

---

### Post by JohnHeikkila on 2010-09-26
Edit your Xorg.conf file
<gksu gedit /etc/X11/xorg.conf>
Then, find something similar like this:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800 +0+0"
    SubSection     "Display"
        Depth       24
```

As you can see the "Option" there, switch the '1280x800' to your screen dimensions and be sure to do this to the correct screen.

---

### Post by rkakkar on 2010-09-27
> **JohnHeikkila said:**
> Edit your Xorg.conf file
<gksu gedit /etc/X11/xorg.conf>
Then, find something similar like this:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800 +0+0"
    SubSection     "Display"
        Depth       24
```

As you can see the "Option" there, switch the '1280x800' to your screen dimensions and be sure to do this to the correct screen.

I can't find xorg.conf in the location you gave me ... maybe because i'm using kubunutu/kde?

$ locate xorg.conf
/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz

---

### Post by migs73 on 2010-09-27
> **rkakkar said:**
> I can't find xorg.conf in the location you gave me ... maybe because i'm using kubunutu/kde?

$ locate xorg.conf
/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz

I'm using Gnome Ubuntu and have the same X11 files so its not a KDE thing.

---

### Post by rkakkar on 2010-10-02
> **migs73 said:**
> I'm using Gnome Ubuntu and have the same X11 files so its not a KDE thing.

So where can I find the file John's talking about?

---

### Post by rkakkar on 2010-10-03
**bump**

---

### Post by P4man on 2010-10-03
By default, there is no xorg.conf anymore. Its no longer strictly needed, but you can still create one. Close X  (sudo service kdm stop) or boot in to recovery mode and run 

sudo Xorg -configure

That will create a default xorg.conf.new in the directory you are currently in. (your home, or /root if you booted in to recovery). move it to /etc/X11 and rename it to xorg.conf. Then try the changes suggested above.

---

