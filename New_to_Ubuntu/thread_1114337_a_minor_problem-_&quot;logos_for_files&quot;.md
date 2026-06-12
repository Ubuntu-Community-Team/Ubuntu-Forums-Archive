---
title: "a minor problem- &quot;logos for files&quot;"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-04-02
Sometimes programs icons do not look like the program.  they look like a blue diamond with gears.  Also, if you create a link in the menu it looks something like a spring with a board on top.  Is there any way to change this?  I would like to have the program logo displayed instead of this- custom logo, as the programs in question don't come with one.  I know this is is minor, but I locate most of my programs by looking at the icons.

---

### Post by 123456789123456789123456 on 2009-04-02
What programs are doing this?

create an icon, I don't yet know how to customize the icon of files yet, though I believe you would right click on the program, go down to properies.  But I would find a picture you would like to use to represent the program, either from internet, or from the computer hard drive.  copy it, so that when you can edit the icon used, you can use the picture you chose instead.

To find out exactly where and how this is done, I would need to do more research.

---

### Post by qwertyuiop96 on 2009-04-02
The ones that are doing it are ones I manually installed (not with apps>add/remove...)  A list- Google Earth, SweetHome 3d, and Foldit.  All, I believe, have logos- they just aren't used.

---

### Post by qwertyuiop96 on 2009-04-02
Correction- not Google Earth, it was Picasa.

---

### Post by CatKiller on 2009-04-02
If the launchers without the icons are in the menu, right-click on the menu and select Edit Menus. Find the launcher without an icon (the blue diamond with the gears is the default for a program to be launched with Wine, I believe, and the springboard is the default launcher icon) and select it, and then select Properties. Click on the icon. This should bring up a dialogue to let you select the icon that you want. If these programs come with their own icons somewhere, it's just a question of knowing where they are in the filesystem tree. Otherwise, you can download an icon that you like and select that. There are some icons in /usr/share/pixmaps, and theme-specific icons are kept in /usr/share/icons.

If the launchers are somewhere else - on your Desktop, for example - they can be changed in a similar way by right-clicking on them and selecting Properties.

Programs that are run with Wine are often kept in a pretend Windows environment in your Home folder (~/.wine). The Windows icons may be in there somewhere, and might be usable. I don't know if this is true of Google's programs that use Wine, since I haven't used them. Perhaps someone who has will be able to point you to their location.

---

### Post by qwertyuiop96 on 2009-04-03
CatKiller- The icon choosing is not available- I can choose command, type, name, and comment.  Also, I am not using Wine- Google Earth and Picasa are both available for Linux.

---

### Post by karlr42 on 2009-04-03
Re-read the post. You click on the icon itself in that dialogue to choose a new one.

---

### Post by qwertyuiop96 on 2009-04-03
It acts the same as if I click on the text- attached is the dialog I get.

---

### Post by qwertyuiop96 on 2009-04-03
never mind- I figured it out.

---

### Post by CatKiller on 2009-04-04
Glad you worked out what I meant.

> **qwertyuiop96 said:**
> Also, I am not using Wine- Google Earth and Picasa are both available for Linux.

Actually, they aren't. Or rather, they don't run natively. The Linux versions are the Windows versions, but bundled with Wine.

---

### Post by qwertyuiop96 on 2009-04-04
> **CatKiller said:**
> Actually, they aren't. Or rather, they don't run natively. The Linux versions are the Windows versions, but bundled with Wine.

That's interesting- I didn't know thet as I don't seem to have Wine...  Something to mull over.

---

