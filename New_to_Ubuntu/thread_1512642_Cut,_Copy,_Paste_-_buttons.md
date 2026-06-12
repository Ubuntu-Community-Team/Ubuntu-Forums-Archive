---
title: "Cut, Copy, Paste - buttons?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Primus1 on 2010-06-18
New to Ubuntu Lucid.

Is there a way to put 'Cut' 'Copy' and 'Paste' buttons on the file browser? I searched and can't see any mention of it. Or if you can direct me to where I can read about it.

---

### Post by jms1989 on 2010-06-18
Hi, nautilus does not have a way to add cut, copy, and paste in the "task bar". To get those, you would either have to right click on a file, folder, or empty space, find them in the "Edit" menu, or use Ctrl-C for copy, Ctrl-X for cut, and Ctrl-V for paste.

Cheers!
jms1989

---

### Post by Primus1 on 2010-06-18
Thanks, yes I use the right click method so far, I like those buttons though, guess the same goes for 'Delete' ? pity.

---

### Post by ghostborg on 2010-06-18
[http://ubuntuforums.org/showthread.php?t=659294]("http://ubuntuforums.org/showthread.php?t=659294")

I found this link in another forum , it's from 2008 so there are differences in the xml code.

As Greenleaf suggests Make a backup of the file first... just in case

I opened a terminal and entered:
```
sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
```

I added the following:

	<separator/>
	<toolitem name="Cut" action="Cut"/>
	<toolitem name="Copy" action="Copy"/>
	<toolitem name="Paste" action="Paste"/>
        <toolitem name="Trash" action="Trash"/>
        <separator/>

To the section near the bottom to look like this:
<toolbar name="Toolbar">
	<toolitem name="Back" action="Back"/>
	<toolitem name="Forward" action="Forward"/>

	<toolitem name="Up" action="Up"/>
	<toolitem name="Stop" action="Stop"/>
	<toolitem name="Reload" action="Reload"/>
	<separator/>
	<toolitem name="Home" action="Home"/>
	<toolitem name="Computer" action="Go to Computer"/>
	<separator/>
	<toolitem name="Zoom" action="Zoom"/>
	<toolitem name="ViewAs" action="ViewAs"/>
	<toolitem name="Search" action="Search"/>
	<separator/>
	<toolitem name="Cut" action="Cut"/>
	<toolitem name="Copy" action="Copy"/>
	<toolitem name="Paste" action="Paste"/>
        <toolitem name="Trash" action="Trash"/>
        <separator/>

	<placeholder name="Extra Buttons Placeholder">
	          <placeholder name="Extension Actions"/>
        </placeholder>
</toolbar>


Saved and restarted, and when I opened Nautilus the buttons where there
and actually worked. They will be grayed out until you click on a file they can operate on.

---

### Post by ajgreeny on 2010-06-18
WOW!

Thanks for that ghostborg, it's an incredibly useful trick that I must make sure I keep a note of for future reference.

---

### Post by Primus1 on 2010-06-18
I'll save this as I don't know that I'd be up to doing it yet, definitely on the to do list.
Thanks.

---

