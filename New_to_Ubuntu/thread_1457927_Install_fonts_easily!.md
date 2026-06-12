---
title: "Install fonts easily!"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by kapi on 2010-04-19
Ok, first download your font to the local machine.

I use [http://1001freefonts.com](http://1001freefonts.com)

now unzip/extract the contents to the same folder or wherever you prefer.

Now In Nautilus open the fonts folder as administrator.

home/usr/share/fonts

Now simply drag the extracted ttf fonts to the fonts folder.

That's it! Couldn't believe it was so simple.

The fonts I've tried so far seem to work perfectly in GIMP so I'm happy

Hope this helps

---

### Post by scottiw2000 on 2010-04-19
There's also a nautilus script available on [www.gnome-look.org](www.gnome-look.org) that makes the process even quicker. With the "install-font" script, all you have to do is:

1. right-click on the font file wherever you have downloaded it;
2. go to "scripts" in the right-click menu;
3. select "font installer"

A nice little dialogue box should soon appear confirming that the font is installed. The script can be downloaded from [http://gnome-look.org/content/show.php/Install+Fonts?content=93625](http://gnome-look.org/content/show.php/Install+Fonts?content=93625) . 

Installing the script is super easy. All you do is copy it to ~/.gnome2/nautilus-scripts. Then right-click on the script file, select "properties", then "permissions" and make sure the "allow executing file as program" check-box is checked. Then you're good to go. The script will show up automatically in the "scripts" sub-menu of the right-click menu in Nautilus.

---

### Post by Paddy Landau on 2010-04-19
The font name is
[FONT=Courier New][SIZE=3]/usr/share/fonts[/SIZE][/FONT]
(no 'home' in front of it), or any subfolder within that, e.g.
[FONT=Courier New][SIZE=3]/usr/share/fonts/1001fonts[/SIZE][/FONT]

You may need to enter the command
[FONT=Courier New][SIZE=3]sudo fc-cache -f[/SIZE][/FONT]
(or log out and back in again) for it to take effect, and you will need to restart OpenOffice and possibly other programs.

But you're right, it's really easy.

---

