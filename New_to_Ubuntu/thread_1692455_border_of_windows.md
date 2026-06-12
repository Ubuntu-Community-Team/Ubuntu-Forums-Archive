---
title: "border of windows"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by flee0308 on 2011-02-21
I am not sure what exactly it is called, so I will call it borders. In every window you open, there will be 4 borders: top, left, bottom, right. By dragging these borders, you can change the size of the window.

Now, I feel that these are too small, making it hard for me to change the size of a window. How can I increase the size of these borders?

---

### Post by sites on 2011-02-21
From gnome-panel... System -> Preferences -> Appearance Preferences

On the Theme tab, choose Customize...

On the Window Border tab you can try different selections.

Not sure if this will give you the borders you want, though.  Are you using compiz or metacity?

---

### Post by BananaPeal on 2011-02-21
try to aim for the bottom right corner, it's a little fatter there!

---

### Post by thefasterblueone on 2011-02-21
Here is a how-to. Your numbers maybe different.

```
1. Open a new Terminal session (Applications > Accessories > Terminal) and enter the following: -

    sudo gedit /usr/share/themes/[theme name]/metacity-1/metacity-theme-1.xml 

(note: theme names are capitalized, e.g.: Radiance, Ambiance, etc.)

2. Scroll down to lines numbered 14-16  in the Gedit window that opens.(Don’t see any numbers? Hit Edit > Preferences > View and check ‘Display line numbers’.)

Change the “value” at the end of the three lines in question from “1&#8243; to “0&#8243;.

Thusly: -

<distance name=”left_width” value=”1&#8243;/>
<distance name=”right_width” value=”1&#8243;/>
<distance name=”bottom_height” value=”1&#8243;/>

becomes: -

<distance name=”left_width” value=”0&#8243;/>
<distance name=”right_width” value=”0&#8243;/>
<distance name=”bottom_height” value=”0&#8243;/>

3. Save the file and then change your theme using Appearance Preferences.

If you modified a theme that you were already using, you must “refresh” the theme by changing to a different theme, then changing back.

4. To revert back to normal, follow steps 1 & 2 to change the values back to 1.

To overcome the “bug” of not being able to resize the window by grabbing it, you can use:

Alt + F8 or Alt + Right mouse scroll or Right-click title bar > Resize
```

---

### Post by flee0308 on 2011-02-21
> **sites said:**
> From gnome-panel... System -> Preferences -> Appearance Preferences

On the Theme tab, choose Customize...

On the Window Border tab you can try different selections.

Not sure if this will give you the borders you want, though.  Are you using compiz or metacity?

Nope, I mean like what BananaPeal was saying, I want to increase the skinny border so that I can change ths size of my window easier. You know, the border where if you place your mouse there, your cursor changes to an arrow with 2 heads?

I am using Compiz.

---

### Post by rg4w on 2011-02-21
Post #4 above is what I've done, but rather than set the border size to 0 I set it to 4, which feels pretty good and is easy to grab.

---

### Post by flee0308 on 2011-02-21
> **thefasterblueone said:**
> Here is a how-to. Your numbers maybe different.

```
1. Open a new Terminal session (Applications > Accessories > Terminal) and enter the following: -

    sudo gedit /usr/share/themes/[theme name]/metacity-1/metacity-theme-1.xml 

(note: theme names are capitalized, e.g.: Radiance, Ambiance, etc.)

2. Scroll down to lines numbered 14-16  in the Gedit window that opens.(Don’t see any numbers? Hit Edit > Preferences > View and check ‘Display line numbers’.)

Change the “value” at the end of the three lines in question from “1&#8243; to “0&#8243;.

Thusly: -

<distance name=”left_width” value=”1&#8243;/>
<distance name=”right_width” value=”1&#8243;/>
<distance name=”bottom_height” value=”1&#8243;/>

becomes: -

<distance name=”left_width” value=”0&#8243;/>
<distance name=”right_width” value=”0&#8243;/>
<distance name=”bottom_height” value=”0&#8243;/>

3. Save the file and then change your theme using Appearance Preferences.

If you modified a theme that you were already using, you must “refresh” the theme by changing to a different theme, then changing back.

4. To revert back to normal, follow steps 1 & 2 to change the values back to 1.

To overcome the “bug” of not being able to resize the window by grabbing it, you can use:

Alt + F8 or Alt + Right mouse scroll or Right-click title bar > Resize
```

> **rg4w said:**
> Post #4 above is what I've done, but rather than set the border size to 0 I set it to 4, which feels pretty good and is easy to grab.

Weird, changing the number doesn't seem to help. I changed it to both 0 and 4, refreshed my theme, and the border is still the same size. Ah well, at least I now know I can use alt+right click to resize.

---

### Post by rg4w on 2011-02-21
You might want to double check that you've edited the right theme file, and the right section of the file.  The first several sections of most of the theme files look almost identical, but govern different window modes.  IIFC it's the first section where those values appear which governs the settings for the default window state.

---

### Post by flee0308 on 2011-02-23
> **rg4w said:**
> You might want to double check that you've edited the right theme file, and the right section of the file.  The first several sections of most of the theme files look almost identical, but govern different window modes.  IIFC it's the first section where those values appear which governs the settings for the default window state.

I am pretty sure I wen tto the right theme, since I typed in Macbuntu in the [insert theme name], and opened a text file similar to the one in the spoiler tag. What's IIFC anyway?

---

### Post by migs73 on 2011-02-23
I think it was a typo and should be IIRC (If I Remember Correctly).

Mike

---

### Post by poundy123 on 2011-02-24
i think this is the right forum for me but basically, at the top of my windows i am missing the close, minimize and maximize buttons, making it difficult for me to close windows easily, this also means i cant access the top left of the taskbar when any windows are open, any help will be welcomed :)

---

### Post by Chris Edgell on 2011-02-24
Poundy123,  Try pressing the Alt key and at the same time left click on the mouse (anywhere on the Firefox window) and drag it clear of the top panel.

---

