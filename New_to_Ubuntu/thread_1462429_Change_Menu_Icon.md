---
title: "Change Menu Icon"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by guguma on 2010-04-25
Hello All,

Using 9.10

I am trying to change the ubuntu menu icon (the one to the left of applications). I need to change one of the start-here.png or start-here.svg files but there are many of them and I do not know which one I should replace.

Thanks in advance.

---

### Post by cariboo on 2010-04-26
Could you maybe give us a link to the instructions you are following?

---

### Post by MichealH on 2010-04-26
> **guguma said:**
> Hello All,

Using 9.10

I am trying to change the ubuntu menu icon (the one to the left of applications). I need to change one of the start-here.png or start-here.svg files but there are many of them and I do not know which one I should replace.

Thanks in advance.


You will need to edit the icon files...

---

### Post by durand on 2010-04-26
I'm guessing that there's only one actual start-here.svg etc file and all the others are just symlinks of that (basically, virtual clones of the original). If you right click on the file, and click on properties, it should tell you which one's the original. Then, just replace that one with the one you want. It would need to be in the right file format I think, though you may be able to fix that in a theme config file.

---

### Post by cuberts on 2010-04-26
> **guguma said:**
> Hello All,

Using 9.10

I am trying to change the ubuntu menu icon (the one to the left of applications). I need to change one of the start-here.png or start-here.svg files but there are many of them and I do not know which one I should replace.

Thanks in advance.Note: This has been tested under Ubuntu 9.04 Gnome. The information might apply to previous versions of Ubuntu as well, but no guarantee is made.

There seem to be many different way to change the Ubuntu menu icon posted around the Web. I am posting the easiest way to accomplish this

 task.

Use the key combination of Alt+F2 to open the Run Application window. Enter gconf-editor and click Run.

Using the navigation on the left, double click apps. Scroll down and double click panel. Double click objects.

Browse through the items presented under objects by left clicking each one. You are looking for the following in the right part of the window:

object-type menu-bar (Menu Bar) or object-type menu-object (Main Menu)

Place a checkmark in the option for use_custom_icon. Double click custom_icon and enter the path to the custom icon. Click OK.

The panels should refresh, showing the new icon.

---

### Post by durand on 2010-04-26
> **cuberts said:**
> Note: This has been tested under Ubuntu 9.04 Gnome. The information might apply to previous versions of Ubuntu as well, but no guarantee is made.

There seem to be many different way to change the Ubuntu menu icon posted around the Web. I am posting the easiest way to accomplish this

 task.

Use the key combination of Alt+F2 to open the Run Application window. Enter gconf-editor and click Run.

Using the navigation on the left, double click apps. Scroll down and double click panel. Double click objects.

Browse through the items presented under objects by left clicking each one. You are looking for the following in the right part of the window:

object-type menu-bar (Menu Bar) or object-type menu-object (Main Menu)

Place a checkmark in the option for use_custom_icon. Double click custom_icon and enter the path to the custom icon. Click OK.

The panels should refresh, showing the new icon.

Oh that's pretty cool! I have not heard of this before. Thanks!

---

### Post by guguma on 2010-04-29
Hello All,

I managed to change the menu icon by making a similar directory structure under 

```
$HOME/.icons/-theme used-
```

and placing a custom start-here.svg file under the appropriate directory.

Thanks for all the replies

---

