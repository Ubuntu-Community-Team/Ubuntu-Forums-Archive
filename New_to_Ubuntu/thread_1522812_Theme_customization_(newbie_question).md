---
title: "Theme customization (newbie question)"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by michaelmouf on 2010-07-02
Hello,
I have ubuntu lucid. I want to create a custom theme where the panels (**only the panels**) are from the Dust theme, and everything else is from the Ambiance theme.Anyone know how do I go around doing this? Sorry for the newbieness, but I'm completely new to both ubuntu and linux.

---

### Post by rcayea on 2010-07-02
Changing the Theme

When you are using your applications, the visual appearance of the buttons, scroll bars, widgets, and other bits and pieces are controlled by the Theme. The built-in theming system can make your applications look radically different, and Ubuntu ships a number of themes with it that you can try. 
Choosing a New Theme

To choose a new theme click System > Preferences > Theme. Inside the dialog box that pops up are a number of themes that you can choose. Just click on a theme and the desktop will be adjusted automatically. You can further customize your theme by clicking the Theme Details button. A new dialog box appears that has tabs for the different parts of the theme you can configure. Click each tab and select an entry from the list to create your own perfect theme. 
Installing New Themes

To install a new theme first head over to [http://art.gnome.org/](http://art.gnome.org/), and find a theme that you like. You need to look for Application Themes when browsing the site. When you find a theme that you like, download it to your computer. Now Click System > Preferences >  Themes and click the Install Theme button. Using the file chooser, find the theme that you just downloaded and it will install automatically. Now select your new theme from the list. 

I got this information from this link:
[https://help.ubuntu.com/6.06/book/book/ubuntubook-ch3-html/UsingUbuntuontheDesktop.html](https://help.ubuntu.com/6.06/book/book/ubuntubook-ch3-html/UsingUbuntuontheDesktop.html)

---

### Post by mcduck on 2010-07-02
> **michaelmouf said:**
> Hello,
I have ubuntu lucid. I want to create a custom theme where the panels (**only the panels**) are from the Dust theme, and everything else is from the Ambiance theme.Anyone know how do I go around doing this? Sorry for the newbieness, but I'm completely new to both ubuntu and linux.

You are going to need to dig into some configuration files to do that, but it's definitely possible, and not too hard at all, even though it might seem a bit complicated if you are new to Ubuntu.

First thing you'll need to do is to remove any panel theming from the Ambince theme. GTK themes are defined in text files, and the file for the Ambiance is /usr/share/themes/Ambiance/gtk-2.0/gtkrc. Find the line that says *bg_pixmap[NORMAL] = "panel_bg.png"* and comment it out by adding a "#" in the beginning of the line. Then save the file, and reload the theme (by changing to any other theme and back to Ambiance again).

After that's done you'll just need to find the Dust themes panel background image (it's in /usr/share/themes/Dust/panel_background.png) and drag&drop it into your panel to set it as the panel background.

That's it. As long as the GTK theme you are using doesn't define any panel background you can use any background image you want in your panels. :)

edit: alternatively you can just make a copy of the Ambiance theme, give it a new name, and replace the panel image file with whatever you want. But personally I prefer removing panel background from GTK themes and defining the background directly from panel's settings instead, as that allows you to set the background image to properly scale for different panel sizes and rotate correctly for vertical panels if you need such things. If the panel background comes from the GTK theme these options are not available and larger than normal (or vertical) panels will always end looking ugly.

---

### Post by michaelmouf on 2010-07-03
Thanks a lot Mcduck! The reason I wanted the Dust panels was because of the ugliness of big/vertical panels under Ambiance. Also, thank you for explaining the steps as you wrote them; I learned something that way.

---

### Post by mcduck on 2010-07-04
No problem. 

And since the large/vertical panel ugliness was your problem, here's how to get the panel background to scale and rotate correctly (this of course requires that the background is set in the panel itself and not in the GTK theme, like I said in my above post):

1. Press Alt-F2 and run *gconf-editor*.

2. Use it to browse to apps/panel/toplevels/*name_of_your_panel*/background

3. Enable or disable the *fit*, *stretch* and *rotate* options to get the result you want. 

*fit* will scale the image to panel height, maintaining it's aspect ratio, and then tiling when the image when necessary.

*stretch* will ignore the original images aspect ratio, and stretches the image so that it fills the panel fully without any tiling.

*rotate* allows the background image to rotate with the panel, you need this for vertical panels, for horizontal ones it makes no difference if this is enabled or disabled.

4. Repeat for every panel you have. :)

---

### Post by warfacegod on 2010-07-04
> To install a new theme first head over to [http://art.gnome.org/](http://art.gnome.org/), and find a theme that you like. You need to look for Application Themes when browsing the site. When you find a theme that you like, download it to your computer. Now Click System > Preferences > Themes and click the Install Theme button. Using the file chooser, find the theme that you just downloaded and it will install automatically. Now select your new theme from the list.


More often than not drag n' dropping the theme file into the Themes tab of Appearance will install it. Doesn't work with .deb packages.

---

