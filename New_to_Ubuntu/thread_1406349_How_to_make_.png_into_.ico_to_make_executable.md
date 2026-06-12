---
title: "How to make .png into .ico to make executable?"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-02-13
I have a .png (attached to this post). I want to make it either a panel or desktop icon to call Thunderbird-Eudora. How can I do this?

---

### Post by nexx on 2010-02-13
Use gimp to open your image, set the size of the image (if ico is to be used for a website it is 16px X 16 px or 32px X 32 px) and save as .ico
:p

---

### Post by Mark_in_Hollywood on 2010-02-13
I have no available selection under Gimp's "Save As" for a .ico extension

2 minutes later:

Sorry I see I have a Microsoft .ico extension.

---

### Post by Rhubarb on 2010-02-13
If you're using the icon on your Ubuntu dekstop / panel, you don't need to convert it into an .ico file.  Just leave it as png.
Ubuntu can use any picture as an icon.

---

### Post by lovinglinux on 2010-02-13
> **Rhubarb said:**
> If you're using the icon on your Ubuntu dekstop / panel, you don't need to convert it into an .ico file.  Just leave it as png.
Ubuntu can use any picture as an icon.

+1

Make sure the image has the size of the maximum displayed size you want, so it doesn't lose quality when sized up. You could also convert it to svg, so it can be scaled on demand. I suppose inkscape should be able to do that.

If you want to generate an ico to use on a web site as favicon, then go to [http://tools.dynamicdrive.com/favicon/](http://tools.dynamicdrive.com/favicon/)

---

### Post by Mark_in_Hollywood on 2010-02-13
How do I associate the icon with the program?

---

### Post by Rhubarb on 2010-02-14
That depends on where the program is located.
[LIST]
[*]In your applications menu?
[*]As an icon in the panel?
[*]As an icon on your desktop?
[/LIST]

If it's in your applications menu, you can configure the shortcut's icon by right clicking on "Applications" and selecting "Edit Menus".  From there find the application, click on properties, and click on the existing icon of the application button (top left of the "Launcher Properties" window).

If it's a shortcut on your desktop (a launcher) or in one of your panels, just right click on it, and select properties, and click on the existing icon of the application button (top left of the "Launcher Properties" window).

---

