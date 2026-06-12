---
title: "Changing themes in 10.04"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by Joesrevolution on 2010-09-29
I have tried dragging and dropping tar.gz files into the themes window (which told me that pretty much everything was unreadable) and I have tried running emerald with Compiz (which was beyond buggy after closing terminal) I was wondering if there was an easy way to change these themes!?

---

### Post by marshmallow1304 on 2010-09-29
If the themes don't work with drag-and-drop, that probably means either
1) They're not Gnome themes.
2) They weren't packaged properly by the creator.

You may have to install them manually.  Look for a readme in the theme archive or instructions on the download page.

---

### Post by mcduck on 2010-09-29
> **Joesrevolution said:**
> I have tried dragging and dropping tar.gz files into the themes window (which told me that pretty much everything was unreadable) and I have tried running emerald with Compiz (which was beyond buggy after closing terminal) I was wondering if there was an easy way to change these themes!?

Emerald probably wan't buggy, if you start something from a terminal and then close the temrinal whatever you started will usually close as well.

To actually use Emerald instead of just testing if it starts or not, you need to configure it in Compiz options (in CompizConfig Settings Manager, under the Window Decorations"-plugin set the command to "/usr/bin/emerald)

What comes to other themes, the above poster got it right. If the theme doesn't install by drag&drop, it's either a different type of theme or packaged in wrong way. Check the theme type and if necessary, extract the theme yourself. (Metacity & GTK themes into ~/.themes and icon themes into ~/.icons. Or /usr/share/themes and /usr/share/icons for system-wide install.)

---

### Post by 0N3 on 2010-09-29
This method will make it available to your user only

1)Extract the theme to your desktop and copy it 

2) go to home folder and hit ctrl + h to show hidden files and folders loook for the .themes folder and paste it into there
This method will make it available to your user only

This method will make it available to everyone guessing the files on your desktop extracted

1) cd Desktop

2) sudo mv filename /usr/share/themes

---

### Post by Joesrevolution on 2010-09-29
> **mcduck said:**
> To actually use Emerald instead of just testing if it starts or not, you need to configure it in Compiz options (in CompizConfig Settings Manager, under the Window Decorations"-plugin set the command to "/usr/bin/emerald)

Okay, I did all of that and still when i close the terminal it all goes back to default.

---

### Post by mcduck on 2010-09-29
> **Joesrevolution said:**
> Okay, I did all of that and still when i close the terminal it all goes back to default.

It will close any time you start it from a terminal. Just like I said. That's how programs started from a terminal work, they run as subprocesses of the terminal iteslf and will close together with it.

If you have it configured in Compiz options now just log out and back again and Emerald will be loaded automatically for you.

---

