---
title: "Remove unwanted programs from applications"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by henry cow on 2010-04-26
How do I remove unwanted Applications from the drop-down list?

Is there anything comparable to Windows "Add/Remove Programs"?

thanks

---

### Post by WinterRain on 2010-04-26
You can remove apps from the ubuntu software center.

---

### Post by joes7 on 2010-04-26
```
Applications----->Add/Remove Applications
```

That's all!:guitar:

---

### Post by WinterRain on 2010-04-26
> **joes7 said:**
> ```
Applications----->Add/Remove Applications
```

That's all!:guitar:

There is no add/remove any more. It's called ubuntu software center. The OP is using the latest ubuntu.

---

### Post by warfacegod on 2010-04-26
Add/Remove is still available in Ubuntu Software Center.

henry cow, if you want to simply remove the apps from the menu without uninstalling them, right click your Apps, Places, System menu> select Edit Menus> uncheck the items you don't want.

---

### Post by Dalek Draco ON LINUX on 2010-04-27
> **henry cow said:**
> How do I remove unwanted Applications from the drop-down list?

Is there anything comparable to Windows "Add/Remove Programs"?

thanks


To remove the program completely, go to ubuntu software center and uninstall it. Or open synaptics manager and uninstall it from there.

To just remove it from your menu's area, right click on the applications toolbar and select edit menus, and then uncheck the desired program.

---

### Post by cojon on 2011-01-08
> **joes7 said:**
> ```
Applications----->Add/Remove Applications
```

That's all!:guitar:

Thank you for the help, but could you include all the missing information? For the life of me I can't understand what this means.

"Applications----->Add/Remove Applications"

I typed it into terminal but that only brings back a message that no such directory exists. It is certainly not anywhere on my menu, and Google returns only unfathomable mysteries as well. 

I would like to remove some unwanted software from Ubuntu 10.10 but I don't seem to be able to figure out how it is done. These things are cake and pie in Windoze, but mysteries to beginners in Ubuntu as the method is apparently a vastly different one and difficult to clearly present.

---

### Post by jonbonjovi on 2011-01-08
Open "System -> Administration -> Synaptic package manager". Then press ctrl+f or click on "search" (top-right) and type the name of the software you want to remove. Click on the little square near the name of the package and select "remove" or "completely remove" (if you don't plan ti re-install it later). Finally, click on "apply".

Or simply, open a terminal and type:
```
sudo apt-get remove nameoftheprogramyouwantoremove

```
It'll ask you to type the password, type it (you don't see anything while you type, no dots, no aterisks, nothing. it's normal) and hit "enter".

---

### Post by uRock on 2011-01-08
If you are just looking to take programs off of the menu, then open the menu and right click the menu and you will see the opion to edit the menus.

If you want to uninstall programs, then you can do it via terminal, Ubuntu Software Center, or Synaptic Package Manager. Add/Remove was for older distro of Ubuntu and has been replaced with the much more efficient Ubuntu Software Store.

---

