---
title: "Missing Wine shortcuts in applications menu"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-02-27
I'd uninstalled and completely deleted Wine a few weeks ago when I was trying a windows programme on it that just didn't run. I've reinstalled it to try any programme, but now find that the shortcuts are missing. I've tried editing the main menu and it's not there either.

I read something elsewhere about having to re-create them. I'm not sure how to do this (anyway, with a fresh installation shouldn't the install have created new shortcuts?).

---

### Post by mc4man on 2009-02-27
If you aren't seeing *any wine entry* in your Applications menu then post the result of running this in a terminal as there is an easy resolution.
If you are seeing wine but nothing else, note that and post anyway.

```
cat ~/.config/menus/applications.menu
```

---

### Post by paulchinnz on 2009-02-27
Thanks. No wine entry at all.

paulchinnz@Thermopylae:~$ cat ~/.config/menus/applications.menu
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<Deleted/>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<DirectoryDir>/home/paulchinnz/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/paulchinnz/.local/share/applications</AppDir>
		<Exclude>
			<Filename>wine.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Development</Name>
		<DirectoryDir>/home/paulchinnz/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Menu>
		<Name>System</Name>
		<AppDir>/home/paulchinnz/.local/share/applications</AppDir>
		<Exclude>
			<Filename>bluetooth-analyzer.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<Include>
			<Filename>ooo-math.desktop</Filename>
		</Include>
		<AppDir>/home/paulchinnz/.local/share/applications</AppDir>
		<Include>
			<Filename>ooo-template.desktop</Filename>
		</Include>
	</Menu>
</Menu>

---

### Post by mc4man on 2009-02-27
Well I wish you had kept the formatting, only because it's a touchy menu to edit in and if done wrong you'll need to delete it. (which may bring back wine, may not

(to keep formatting, after pasting into your reply you would highlight the text you pasted and click on the little quote button in the upper panel. (fourth from right

In any event you need to remove the <Deleted/> under the <Name>wine-wine</Name> entry

> <Name>wine-wine</Name>
[COLOR="Red"]<Deleted/>[/COLOR]

You also have this

> <Exclude>
<Filename>wine.desktop</Filename>
</Exclude>

I wouldn't worry about that now, "excludes" are something that can be returned from edit menus or if need be manually edited like this

> <Include>
<Filename>wine.desktop</Filename>
</Include>

Keep the formatting in the file as it is, if unsure repost as I described

To edit do this
```
gedit ~/.config/menus/applications.menu
```

---

### Post by paulchinnz on 2009-02-27
> <!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<Deleted/>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<DirectoryDir>/home/paulchinnz/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/paulchinnz/.local/share/applications</AppDir>
		<Exclude>
			<Filename>wine.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Development</Name>
		<DirectoryDir>/home/paulchinnz/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Menu>
		<Name>System</Name>
		<AppDir>/home/paulchinnz/.local/share/applications</AppDir>
		<Exclude>
			<Filename>bluetooth-analyzer.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<Include>
			<Filename>ooo-math.desktop</Filename>
		</Include>
		<AppDir>/home/paulchinnz/.local/share/applications</AppDir>
		<Include>
			<Filename>ooo-template.desktop</Filename>
		</Include>
	</Menu>
</Menu>

Thanks for the tip about keeping formatting. So when I delete <Deleted/> do I get rid of the line as well or keep an empty line there?

(Tried the quote button, no luck)

---

### Post by mc4man on 2009-02-28
Just remove the <Deleted/> (it usually doesn't matter if you backspace the line, though you can

(in all likelihood if you just browsed to home folder -> .config/menus and deleted the applications.menu then when you click on Applications all would be returned, better to do it this way first.

(just noticed - when you copy and paste from a cat command you get what you've posted, if you copy and paste from a gedit command then the formatting stays, sorta makes sense

---

### Post by paulchinnz on 2009-02-28
Thanks removing <Deleted/> worked. I couldn't find /.config/menus although I did find a couple of application.menu files, both that had only been last altered 2008 i.e. well before I fiddled with wine.

Thanks again for your help. I'd amend this thread as solved, but can't find the function under my thread tools. Any idea where it is?

---

### Post by orethrius on 2009-02-28
> **paulchinnz said:**
> Thanks again for your help. I'd amend this thread as solved, but can't find the function under my thread tools. Any idea where it is?

I'm pretty sure that functionality was removed a couple updates ago, perhaps with the move to vBulletin.  I imagine you can edit the first post and manually alter the title to read [SOLVED] at the beginning.

---

### Post by mc4man on 2009-02-28
> I couldn't find /.config/menus
It's a 'hidden' directory in your home folder. (all folders with a . in front are hidden.
For a one time view you'd either go Ctrl+h when in your home folder or view -> 'show hidden files'

To enable persistently then you need to set in 'file management' -> views,  which has not been enabled by default. 

To enable go in a terminal
```
alacarte
```
highlight preferences and you'll see 'file management' in the right side column, click to enable. Then it can be found in System -> preferences menu (Lots of useful settings in there

To open 'file management' without enabling as a menu choice go this in a terminal
```

nautilus-file-management-properties
```

---

### Post by paulchinnz on 2009-03-02
Thanks ... the things I'd forgotten from Windows already. Enabled hidden files via 'view' in the local folder menu, but thanks for the tip about file management.

---

### Post by davidsrsb on 2009-03-02
See my thread [http://ubuntuforums.org/showthread.php?t=1081979](http://ubuntuforums.org/showthread.php?t=1081979)
I had to delete some files in .config and .local

---

