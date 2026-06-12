---
title: "ies4linux + gutsy"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by onegreenparker on 2008-01-30
Has anyone successfully got IEs4Linux working on Gutsy?

I had to run the install a few times before it was successful. The program starts but does not display correctly, on bothe the IE menus and the sites themselves, some items don't display.

I am using WINE 0.9.54

---

### Post by luisromangz on 2008-01-30
It work as perfectly here, and I am using the same Wine version as you.

---

### Post by onegreenparker on 2008-01-30
Hmmm, I'll have to play with some settings......any ideas?

---

### Post by onegreenparker on 2008-02-05
Fresh ies4linux on a different gutsy machine, and can't get the install to work! I've changed edgy to gutsy in sources.list, sudo apt-get update, but when I run 
```

./ies4linux

```

I get
```

/usr/share/ies4linux-2.99.0/ui/pygtk/ies4linux-gtk.py:399: GtkWarning: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
  gtk.main()
ui/pygtk/python-gtk.sh: line 6: 18319 Segmentation fault      (core dumped) python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

```

Any ideas?

---

### Post by Enissay on 2008-02-05
i had the same problem...
Googling i found this: 
Just type : 
> **[COLOR="Red"]./ies4linux --no-gui[/COLOR]** instead of **[COLOR="Red"]./ies4linux[/COLOR]**

---

### Post by onegreenparker on 2008-02-06
Thanks, the **--no-gui** option worked to get ies$linux installed.

But IE6 still does not display properly, the menu and some icons are invisible. I will install allfonts using the winetricks script and try again.

---

