---
title: "deleted `games' menu from applications want to recover"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by dineshs on 2010-03-03
Going to system-preferences-main menu I deleted games.How can I recover this?

---

### Post by Yogotiss on 2010-03-03
> **dineshs said:**
> Going to system-preferences-main menu I deleted games.How can I recover this?

You sure you don't mean ([COLOR="Blue"]Applications[/COLOR]>>[COLOR="blue"]Games[/COLOR])? Right click on the *Applications Places System *[***Text***] in the menu then select _***Edit Menu***_. A window should pop up showing you the different materials you can check and un-check to the menu.

---

### Post by dineshs on 2010-03-03
> **dineshs said:**
> Going to system-preferences-main menu I deleted games.How can I recover this?
After doing this (i actually deleted games from the list of items shown and not uncheck)the option games does not appear in the list of EDIT MENU

---

### Post by ad_267 on 2010-03-03
Under system - preferences - main menu, just click the "Revert" button.

---

### Post by dineshs on 2010-03-03
Still not OK

---

### Post by mc4man on 2010-03-03
You can try this but you must do the edit carefully or you'll lose the applications menu altogether ( and have to delete this file which it would be best not to do.

```
gedit ~/.config/menus/applications.menu
```

Then hopefully you'll see this section, if so delete **only what I've marked in red.**
If there, then carefully remove the red and save..


```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Games</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>

```

---

### Post by dineshs on 2010-03-03
ad_267,
Problem solved when I tried revert 2 times.Thanks for the help,also to mc4man

---

