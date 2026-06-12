---
title: "Desktop folders, icons, launchers"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by klytu on 2010-05-18
Attempting to breathe new life into some older hardware, I tried out Lubuntu via a live-cd. I was impressed; even running from the live-cd it was very responsive on my old machine! I got compiz and some other desktop effects working as well. However, I had difficulty with something very simple. How can I get shortcuts to folders and launchers onto the desktop with it?

---

### Post by klytu on 2010-05-18
*Bump*

---

### Post by cubeist on 2010-05-18
right-click on your desktop and select "create launcher"

---

### Post by klytu on 2010-05-18
> **cubeist said:**
> right-click on your desktop and select "create launcher"

Running the Lubuntu Lucid live-cd, that option is not present with a right-click.

---

### Post by jee_bee on 2010-05-18
there is no way to create launch exept....

> lxshortcut -o ~/Desktop/urlaunchername.desktop

and it will pop a gui but its not working 4 me...
i mean i cannot exec my .sh from there......

---

### Post by kerry_s on 2010-05-18
for applications, copy the programs from /usr/share/applications & paste them in the desktop folder.

for folders you can create a *.desktop file
or
just do sym links, example:
ln -s ~/Video ~/Desktop/Video

---

### Post by klytu on 2010-05-19
> **kerry_s said:**
> for applications, copy the programs from /usr/share/applications & paste them in the desktop folder.

for folders you can create a *.desktop file
or
just do sym links, example:
ln -s ~/Video ~/Desktop/Video

OK, I understand this and thanks for the response. 

I was really looking for a way to do all this through the GUI. Is that just not available with LXDE?

---

### Post by kerry_s on 2010-05-19
> **klytu said:**
> OK, I understand this and thanks for the response. 

I was really looking for a way to do all this through the GUI. Is that just not available with LXDE?

like jee_bee said, there is lxshortcut, which is basic.

---

### Post by klytu on 2010-05-19
> **kerry_s said:**
> like jee_bee said, there is lxshortcut, which is basic.

Thanks ... this works well enough.

---

### Post by klytu on 2010-05-19
> **jee_bee said:**
> there is no way to create launch exept....



and it will pop a gui but its not working 4 me...
i mean i cannot exec my .sh from there......

Thanks, this worked for me. Do you mean that you couldn't run a script with the launcher you created?

---

### Post by jee_bee on 2010-05-19
runnig Lubuntu no i cannot (i probaly just didn find how...)  i cannot run a script in a terminal by clicking on it.....

if somebody got a solution let my know

---

### Post by torkna on 2010-05-22
I just installed lubuntu 10.04 today, and I found that if the program that you want is in the applications menu, you can right click on it and say, add to desktop. This puts an icon on the desktop. However, once there I can't figure out how to rename the Launcher, or change the icon. But it is a start, and the links do work.

---

### Post by jee_bee on 2010-05-22
to rename right click ur launcher and "rename"
and for the icon right click on it "properties" and click on the icon on the top left of the properties windows \\:D/



heuuu... basically same as windows..... to rename u can aslo hit F2

---

### Post by torkna on 2010-06-16
@jee_bee
I can do everything described, except it doesn't work. The rename dialogue pops up, and then I change the text, and then when I say ok, it doesn't change. As for changing the picture, it won't even let you click on the icon in the top left corner. I have done this all the time with regular Ubuntu, but for some reason Lubuntu does not have these desktop managing abilities, but hopefully it will improve with coming releases.

---

### Post by jee_bee on 2010-06-17
Lubuntu is now a thing of the pass for me...
too much trouble for a so litle difference from ubuntu
):P

---

### Post by kerry_s on 2010-06-17
> **jee_bee said:**
> Lubuntu is now a thing of the pass for me...
too much trouble for a so litle difference from ubuntu
):P

any *ubuntu is what you make of it, i switched from the normal gnome version back to lubuntu, then set it up like the ubuntu netbook version. i have openbox setup to maximize all programs & remove the decor(title bars).

anyways its like you say, its how much time you want to put into it.

---

### Post by klytu on 2010-06-17
> **kerry_s said:**
> any *ubuntu is what you make of it, i switched from the normal gnome version back to lubuntu, then set it up like the ubuntu netbook version. i have openbox setup to maximize all programs & remove the decor(title bars).

anyways its like you say, its home much time you want to put into it.

How did you get that menu on the right-hand side of first screen shot? Is that part of a particular package?

---

### Post by kerry_s on 2010-06-17
> **klytu said:**
> How did you get that menu on the right-hand side of first screen shot? Is that part of a particular package?

thats "netbook-launcher-efl" its the 2d version, light & fast.
its part of the ubuntu netbook remix system.
i'm using just the launcher & alacarte menu editor, i have recommends turned off in synaptic, so not to much gnome stuff.
the menu editor needs gnome-panel to work right, so i have that setup as a backup, but i'm not using it.

---

