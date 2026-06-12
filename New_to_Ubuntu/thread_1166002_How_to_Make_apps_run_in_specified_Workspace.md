---
title: "How to Make apps run in specified Workspace?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-21
Hi there
I have installed Compiz Manager now i want to make apps run in specified workspace or Virtual Desktop.

For example, i want Firefox to run in one Desktop(Workspace), Transmission in other, Nautilus in 3rd and pigin in 4th may and so on.

How to do that? Is that possible?

---

### Post by bacardiandwatermelon on 2009-05-21
If you right click the app and then select move to another workspace does that work?

---

### Post by raziiq on 2009-05-21
infact i m talking about whenever i reboot my pc and i click that app, it should open in my specified workspace. I dont want to set the workspace for that app again n again. Just like in Mac OS X Leopard we can use Spaces and then in its setting we can add apps and then can specify in which space they will open.

Is it possible in uBuntu??

---

### Post by lovinglinux on 2009-05-21
Use the "Place Windows" compiz plugin.

---

### Post by raziiq on 2009-05-21
can you please explain me how to use this Place Window plugin, its looks quite complex to me, cant get it

---

### Post by lovinglinux on 2009-05-21
> **raziiq said:**
> can you please explain me how to use this Place Window plugin, its looks quite complex to me, cant get it

Click the "Place Windows" plugin button, then click the "Fixed Window Placement" tab, then click the "New" button in the "Windows with fixed viewport", then click the "+" button in the "Edit" window, then click the "Grab" button in the "Edit Match" window, then click over the program window you want to place on a specific port (Firefox for example). It should capture the program class (there are other types too, like title for example), then click "+ Add" button. It should add something like "class=Firefox". Then select the "X viewport positions" value, which correspond to the horizontal line of workspaces. If you don't use more than one row of workspaces, then you can leave the  "Y viewport positions" alone. Click "Close" and you should get something like the screenshot attached:

Please let me know if this is clear enough or if you need further assistance.

---

### Post by raziiq on 2009-06-03
thanks for the help, it worked like a charm

---

### Post by lovinglinux on 2009-06-03
> **raziiq said:**
> thanks for the help, it worked like a charm

You are welcome.

---

### Post by charonred on 2009-07-27
I tried that too, and it worked; only drawback is I could no longer 'roll-up' the window by clicking on titlebar and rotating mouse wheel (shade I think it was called) - rolling the window as such is something I do regularly, so is there another solution, or fix?

---

### Post by VCoolio on 2009-07-27
have a look at [devilspie]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/"), it's kinda old but still works fine. Don't worry, it's very low on resources, no harm in running it. The link uses as an example firefox opening on 2nd workspace, so good luck.

---

