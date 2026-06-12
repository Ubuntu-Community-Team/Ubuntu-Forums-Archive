---
title: "No icons in context menu for 9.10"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by The Funkbomb on 2009-11-12
I just used Nautilus-actions to make a shred button.

Something I didn't notice is when I right click, the words show up but no icons in the context menu.

I assigned the gtk-warning icon just to be safe but when I right clicked, none of them were there.

I have a 9600gt so I don't think it's a gpu problem.  Maybe a theme problem or a Compiz bad reaction?

---

### Post by nhasian on 2009-11-12
go to System-> Preferences-> Appearance-> Interface then tick the box for Show icons in the menus.

---

### Post by kelvin.illa on 2009-11-12
I can't know if you already tried this, but I think sometimes the most obvious solutions aren't noticed; this happens a lot to me.

Have you gone to the "appearance" preferences? There's a tab there that writes "interfaces" which has a checkbox that writes "Show icons in menus" under the heading "Menus and Toolbars." Check that box, then close the window, and see if it works.

---

### Post by The Funkbomb on 2009-11-12
Amazing.  I never even noticed that.  I don't know why it would be off.

Thanks!

---

### Post by mocoloco on 2009-11-15
It was off because that's unfortunately the new default in Gnome 2.28.  We're [not the only ones]("http://jeremy.visser.name/2009/09/23/how-to-fix-menu-icons-in-gnome-2-28/") who dislike this change. They also disabled [icons on buttons]("http://www.osnews.com/story/21935/GNOME_To_Drop_Icons_in_Buttons_Menus"), and there's not a checkbox to add them back, although you can change it in gconf.

Does anyone where to set using icons in menus as the default for *all* users, rather than have to change it for each user?

---

### Post by coldReactive on 2009-11-15
> **mocoloco said:**
> Does anyone where to set using icons in menus as the default for *all* users, rather than have to change it for each user?

Think you have to symlink the settings. Though, I'm not sure how to do so.

Also, I've heard you won't be able to "fix" this issue in the future, the appearances item for adding back the icons in the menus is going to be dropped soon it seems.

---

### Post by mocoloco on 2009-11-15
> **coldReactive said:**
> I've heard you won't be able to "fix" this issue in the future, the appearances item for adding back the icons in the menus is going to be dropped soon it seems.

Too bad. I have my personal preference, but they're also useful as a possible accessibility help, for people who are dyslexic or who can't read (like my 4-year-old who can still find the print button in firefox thanks to the menu icon).
The most blaring issue with it right now though I think is the System menu looking out of place next to the icon-ed Applications and Places menus.  Why are exceptions made for only two of the three to have icons?  Sigh.

---

### Post by svaens on 2009-12-03
What sort of messed up idea is that, removing the icons. geez.

---

### Post by mocoloco on 2009-12-03
To answer my own question on changing the default for all users: edit /usr/share/gconf/defaults/10_libgnome2-common and add this line
```
/desktop/gnome/interface/menus_have_icons       true
```
It won't affect existing users since their own gconf settings will have already been set in their home directories, but for all new users it will give icons by default.  I've made that change along with some others on a custom Ubuntu CD I use.

Oh and if you want buttons to have icons too then in that same file add
```
/desktop/gnome/interface/buttons_have_icons       true
```

---

### Post by abchernin on 2010-12-14
[SIZE=1]As this is the first thread to pop up in Google under "*ubuntu no icons in context menus*" query results, I thought it appropriate to post an entry-user-friendly how-to here.[/SIZE]

[SIZE=2]**In ****Ubuntu 10.10**, _System->Appearance_ window has no _Interface_ tab. Therefore, the solution is to manually change the settings. 
Run [/SIZE][FONT=Courier New][SIZE=2]gconf-editor[/SIZE][/FONT][SIZE=2]. Go to [/SIZE][FONT=Courier New][SIZE=2]desktop/gnome/interface[/SIZE][/FONT][SIZE=2] and tick [/SIZE][FONT=Courier New][SIZE=2]menus_have_icons[/SIZE][/FONT][SIZE=2] and [/SIZE][FONT=Courier New][SIZE=2]buttons_have_icons[/SIZE][/FONT][SIZE=2]. That's it. [/SIZE]

[SIZE=1]P.S. They should really address this issue at Canonical. I understand it's downstream, but ways have been found for other stuff, haven't they? For example, introduce a notifier similar to [/SIZE][FONT=Courier New][SIZE=1]jockey-gtk[/SIZE][/FONT][SIZE=1].[/SIZE]

---

### Post by regsnerven on 2011-11-29
In 11.10 gconf is not used anymore.

Therefore you either use "dconf-editor" or these commands to enable icons for context menu and/or buttons

Context menus:
dconf write /org/gnome/desktop/interface/menus-have-icons true

Buttons:

dconf write /org/gnome/desktop/interface/buttons-have-icons true

Gr33tZ
Rn

---

