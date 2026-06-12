---
title: "types of links other than hard and symbolic link"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by john77eipe on 2010-12-22
Hi,

I found the file "examples.desktop" and wonder what kind of file this is!!

```

eipe@eipe-john:/etc/skel$ ls
examples.desktop
eipe@eipe-john:/etc/skel$ cat examples.desktop 
[Desktop Entry]
Version=1.0
Type=Link
Name=Examples
Comment=Example content for Ubuntu
URL=file:///usr/share/example-content/
Icon=folder
X-Ubuntu-Gettext-Domain=example-content

```

---

### Post by matt_symes on 2010-12-22
Hi

Have a read of this...

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

Kind regards

---

### Post by QLee on 2010-12-22
If you navigate to that location, /etc/skel/ with your file browser (nautilus), you will see that the file type for "Examples" is desktop configuration file.

When a new user is created, the link to /usr/share/example-content is created on the Desktop.

---

### Post by john77eipe on 2010-12-22
yes. I know the purpose of that location. What I was wondering is about the type of that file. 
This is what i know:
1. Hard links cannot be created for directories.
2. Symbolic links are obviously visible as links.

I will read that link and see what that gives. :-)

Thanks.

---

### Post by mcduck on 2010-12-22
a .desktop file is not a link at all, just a regular text file, used as a launcher or a menu entry. (much like a shortcut or application launcher in Windows)

So, unlike hard and soft links, which operate at the file system level, these are just regular text files and any functionality they might have depends on the progams that read the contents of the file, and for example create a desktop icon for you based on that info.

---

### Post by QLee on 2010-12-22
[QUOTE=john77eipe]... What I was wondering is about the type of that file. 
...[/QUOTE]

As I mentioned the type of file it is, "file type is desktop configuration file", I don't know how to better explain it. Perhaps somewhere in the three posters replies you will find the answer you need.

---

### Post by john77eipe on 2010-12-22
Got it. This is a kind of file specific to the desktop environments like GNOME/KDE. I haven't been studying anything outside the core Linux, so missed it.

Thanks everyone.

---

