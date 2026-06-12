---
title: "display will not load"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Mmmavis on 2010-03-11
Hi all I'm brand spanking new to Ubuntu but excited to learn all its secrets.

So I've got Ubuntu installed and running on my computer. I have begun to play with the look of it. First up, the screen resolution: It was stuck at 800 X 600, wouldn't go any higher than that. I figured out that it wasn't recognizing my video card, so I got a driver downloaded and installed to fix it, restarted, and it automatically came up with a higher resolution in place.

I wanted to see what resolution it is now at, so I went

System----->Preference------->Display

But when I try to click on display to bring it up I get the following error:

[B]Could not launch 'Display'
Failed to execute child process "gksugnome-display-properties" (No such file or directory)[/B]

Can anybody please tell me what this means and how I can get the display controls to open up?

---

### Post by Temposs on 2010-03-11
What kind of graphics card have you got?

---

### Post by ankspo71 on 2010-03-11
Hi,
I don't think gksu is required to change the display properties
so try using this command in the terminal:
```
gnome-display-properties
```if you need to run it with gksu then:
```
gksu gnome-display-properties
```To me it looks like something modified the shortcut in your menu, but failed to do so.

If the above commands work for you then...
You might be able to correct it if you try the following, :
Open the desktop entry with the text editor by pasting this into the terminal:
```
gksudo gedit /usr/share/applications/display-properties.desktop
```
next, change the command in bold below so that it matches either command from above:
> [Desktop Entry]
Name=Monitors
Comment=Change resolution and position of monitors
Exec=**gnome-display-properties**
Icon=gnome-display-properties
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Settings;HardwareSettings;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-control-center
X-GNOME-Bugzilla-Component=Screen resolution
X-GNOME-Bugzilla-Version=2.29.92
X-Ubuntu-Gettext-Domain=gnome-control-center-2.0Then save it, then the shortcut should be fixed.

PS. This is an exact copy from my version of Ubuntu, so ignore the version numbers (and the other lines too).
Or you could simply create a new shortcut in the applications menu.

Hope this helps.

---

### Post by ankspo71 on 2010-03-11
To have a peek at your display resolution, you can run the command 
```
xrandr
```
The "*" indicates your resolution and refresh rate.

---

### Post by Mmmavis on 2010-03-11
I typed in gnome-display-properties, it brought up a window that said 

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

Click yes, brings up a window titled NVIDIA X Server Settings. From there I can see the resolution: 1360 X 768. I can adjust it there as well.

I can either use this or decide to get a better driver, haven't decided yet.

But thank you very kindly, I learned a wee bit more about my Ubuntu. :KS

---

### Post by Temposs on 2010-03-11
Actually, I think if you are using Nvidia's drivers(pretty much necessary to get any 3d graphics), then you have to use their settings app. It works alright, but I like the Ubuntu Display app better.

---

