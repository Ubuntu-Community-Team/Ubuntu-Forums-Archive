---
title: "Customizing Help: GTK1/GTK2/Metacity ??"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by Tayl on 2010-01-04
Hey all.

I'm currently browsing [[COLOR="RoyalBlue"]gnome-look[/COLOR]]("http://www.gnome-look.org") and I'm getting a tad confused on what to customize with what. What are GTK1/2, Metacity etc? And how do I know which one of those I need? 

And how do you install Icon Themes? I browsed the appearance section of my install but within the icons area, it's the only part I can't see an install button. Say for example, I wanted to install: [[COLOR="RoyalBlue"]Icon theme I'd like[/COLOR]]("http://www.gnome-look.org/content/show.php/LaGaDesk-BlueNight?content=109343"), how do I do that?

Regards,

Tayl.

---

### Post by Lord Stig on 2010-01-04
I'm not an expert, but I look under GTK 2.0 themes. I don't know what it means but they work for me!
Metacity is a window manager - it's responsible for drawing the borders around the windows, where its titlebar and minimise, restore and maximise buttons are.

I'm assuming you are using Gnome (the default for Ubuntu) not KDE (the default for Kubuntu) or any other non-default GUI.

The manual way to install an icon theme is to browse your home directory through your file manager with view hidden files enabled (press Ctrl H to turn on or off). There's a (hidden) folder in there called .icons where you can just copy your icon file.

Hope that helps.

---

### Post by Tayl on 2010-01-04
Thank you very much, that helps a great deal. Certainly gives me a better insight into it all. I went with GTK2 originally because, with most things containing numbers, I treat it like versions and always go for the latest. 

Tayl.

---

### Post by bobin on 2010-01-04
GTK changes the look of your desktop. If you are using a emerald(controls window borders, supports translucency etc) based theme then the settings for window borders will not be that of the GTK. In every GTK theme you can customize the icons, wallpaper, border, mouse appearance

---

### Post by Methuselah on 2010-01-04
IIRC, on the dialog to install a theme there is a customize botton beside the install button.
If you click that you can select an icon tab in the window that comes up and I think you cna drag and drop downloaded icon sets into this window.
I hope I am right about that but I seem to remember doing so.

GTK 2.0 themes affect how your widgets (buttons, check boxes etc.) look.
Metacity themes will be more concerned with window decorations (frame, title bar, title bar buttons).

If you have desktop effects I'd recommend installing compiz fusion icon (look for it in software store).
You'll really be using emerald themes if you have a 3D desktop though I think you can opt to use another window decorator through compiz fusion icon.

Most of the gdm (login screen) themes probably won't work with Karmic's GDM but will work with previous versions. 

GDM - login screem
Metacity - Gnome Window Manager
Emerald - Compiz window decorator (window border/frame)
GTK 2.0 - Widget tookit
Sometimes you'll find themes that contain most of these components in a uniform style.
Hope that helps straighten things out a bit

Finally, be careful about running programs and packages from gnome-look.
Prefer archives you can unzip and poke around in to see that they contain mostly images, and non-executable text files.
While it is rather rare, it is possible for malware to be hidden in gnome-look packages.

---

### Post by Tayl on 2010-01-04
Thank you for the heads up Methuselah, and I'll be sure to take your warning into consideration :).

Tayl.

---

