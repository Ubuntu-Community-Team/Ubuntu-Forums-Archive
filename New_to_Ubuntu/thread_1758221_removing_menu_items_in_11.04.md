---
title: "removing menu items in 11.04"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by logikism on 2011-05-14
in the applications menu on the left i want to remove some icons. 

ie; i installed apps in wine and removed them and the shortcuts are still there.

how can i get rid of them?


thanks in advance!

---

### Post by frankbooth on 2011-05-14
Launch a terminal and type:
```

cd /usr/share/applications/

```

in there you should find all menu entries, see if you can find your wine applications in there by typing:
```

ls

```
followed by (**use this command with caution**):
```

sudo rm wineapplicationsname.desktop

```

Once removed it should not show in the menu/dash once you relog.
Let us know if it worked :) I'm *not* 100% sure it will.

---

### Post by logikism on 2011-05-14
thank you!

i see the menu entries but

ive uninstalled the app from wine,

it doesnt show the one i wanna get rid of though it is there in the menu

and to be honest the last command i dont understand

i got as far as listing the menu entries





+++ooooh i get the last command now!
 the entry i want to remove isnt there now though!
maybe i should install it again> removed menu entrie then uninstall from wine?

---

### Post by logikism on 2011-05-14
nope that didnt work either

---

### Post by frankbooth on 2011-05-14
Try this, launch a terminal and write:
```

nautilus ~/.local/share/applications/wine

```

if the applications you've uninstalled have left any folders in there you can try to remove them, relog and see if they're still in the menu.

---

### Post by logikism on 2011-05-14
that brought me to it! i deleted the folder and its gone!!! 

thanks you so much!!! 

a little thing like that was annoying the hell outta me!

---

### Post by vanadium on 2011-05-14
A better approach (in general) is tu use alacarte, where you can disable menu items. This also works for the Unity dash.

---

### Post by logikism on 2011-05-14
i tried that first and it was no help and i dont really understand that app

---

### Post by wildmanne39 on 2011-05-14
> **logikism said:**
> i tried that first and it was no help and i dont really understand that app

Hi, most of the icons you can remove from the launcher by right clicking on it and uncheck where it says to keep in launcher.:)

---

### Post by ngubk on 2011-05-14
One more action to get rid of WINE: when you right click and choose 'open with' with any item, you can see a list of wine stuff there. It really is bugging me, To get rid of that, go to home/user/.local/share/application, find anything which has 'wine' in name and delete it.

---

### Post by vanadium on 2011-05-15
> **vanadium said:**
> A better approach (in general) is to use alacarte, where you can disable menu items. This also works for the Unity dash.

I was probably wrong here: while it will work for the Unity dash (i.e., the application will not any more show in the dash or the application lens), this will not remove the icon from the launcher. Indeed, removing icons from the launcher is just a matter of right-clicking and clearing the check-mark next to "keep in launcher".

---

### Post by wildmanne39 on 2011-05-15
> **logikism said:**
> in the applications menu on the left i want to remove some icons. 

ie; i installed apps in wine and removed them and the shortcuts are still there.

how can i get rid of them?


thanks in advance!

Hi,if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:)

---

