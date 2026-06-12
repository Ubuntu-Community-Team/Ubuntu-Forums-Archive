---
title: "Places Menu Icons"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by RealG187 on 2009-03-11
I am changing my icon themes and have successfully changed the icon used for folders in Nautilus and on the desktop but when I goto the places menu the folder icon beside Documents, Music, Pictures, and Videos is still the same, how do I change those icons?

I changed folder.png in ~/scalable/places but it changed the Nautilus icons, not the ones under the places menu :(

---

### Post by ibuclaw on 2009-03-11
From a quick look around on my icon theme set, you either need to have the icons in the **24x24/places** directory, or, at least have the places folder declaration look like this in the **index.theme** file.
```

[128x128/places]
Size=128
Context=Places
Type=**Scalable**

```

Regards
Iain

---

### Post by RealG187 on 2009-03-11
Wow coinscidence, I just checked my usercp and seen there was a reply. I'll try that when I get home...

---

### Post by RealG187 on 2009-03-11
I have folder.png in /24x24/places but it still shows a different icon.

[http://operation420.net/IconsBackup.tar.gz](http://operation420.net/IconsBackup.tar.gz)
Here is the theme I have (not this file does not have folder.png in the 24x24/places folder because this backup was made before I put it in. Maybe someone could get it to work.

---

### Post by ibuclaw on 2009-03-11
Hi, sorry for the delay, as you may or may not know, the forums have been down.

I will have a look at the icon set now for you, and post here anything I notice.

Regards
Iain

---

### Post by RealG187 on 2009-03-11
Yes I did notice the forums have been down

---

### Post by ibuclaw on 2009-03-11
Okies!

Follow these instructions:
```
cd ~/.icons/**FOLDER**/scalable/places
```
Where "FOLDER" is the folder where your icon set is.
```
ln -s stock_folder.png inode-directory.png
```
And that will fix your problem.

To set it, change icon theme to and from the one you want.

Regards
Iain

---

### Post by RealG187 on 2009-03-11
What exactly does the command "ln -s stock_folder.png inode-directory.png" do?

---

### Post by ibuclaw on 2009-03-11
> **RealG187 said:**
> What exactly does the command "ln -s stock_folder.png inode-directory.png" do?

It creates a symbolic link (or symlink for short) to the **stock_folder.png** icon.
A symbolic link is like a pointer. It is a file which points to another file on the filesystem.

So when you open the file "inode-directory.png" for viewing, you are infact opening "stock_folder.png"

The idea is simple, and it's used in effect all over the Linux filesystem, and Ubuntu is no different. And the only downside is that if the original file gets moved or removed, then all symlinks are effectively defunct too.

As an example, run -
```
ls -l /bin/
```
And you'll see some files highlighted in light blue. For example:
```
lrwxrwxrwx 1 root root       4 2008-10-31 23:32 sh -> dash
```
**sh** is a symlink pointing to the file **dash**.

Think of it like the command **cp** (to copy files), only this doesn't use up that extra space.

For a little bit more info
```
man ln
```

Regards
Iain

---

### Post by RealG187 on 2009-03-11
I know what a symbolic link is and I love them, if I want to share a file/folder temporarily with VMWare instead of sharing a the folder I make a symlink. Even handier if I want to share one file in a folder but not the whole folder.

So does that make inode-directory symlink to stock_folder?

---

### Post by ibuclaw on 2009-03-11
in short, yes....

---

### Post by RealG187 on 2009-03-11
I did it and the icons in the places menu are wrong and now all the Nautilus icons are really small

EDIT: I made stock_folder.png 128x128 and that made the icons normal size, but the ones in the places menu are still those 2D ones.

EDIT2: Now the icons in the places menu appear correctly, I am not sure what I done...

I am still having trouble with a few more icons, I used this theme with 8.04 and everything appeared good, I think 8.10 changed a few things...

---

### Post by RealG187 on 2009-03-12
Okay I think that problem is solved, next are the "Shut Down" icons like Shut Down, Restart, Suspend and Hibernate.

1.png is the theme applied to 8.04 it all works good.
2.png is when you click the icon in the top right of the screen in 8.10, in 8.04 clicking it brought up the screen in 1.png, but here it brings up a menu with no icons
3.png Shows the ACPI shutdown (which in 8.04 would come up instead of the menu), there are icons here like in 8.04 but they are the wrong ones, I assume 8.10 changed the paths/filenames of the icons...

---

### Post by Matt G Dalian on 2010-04-04
Hi,

I solved this problem (by accident) without using symbolic link.

You just have to edit the default Documents, Downloads, Pictures, etc. directories and you will get a small icon next to the folder names in your places menu.
You do this by editing .config/user-dirs.dirs

My description is here:
[http://ubuntuforums.org/showthread.php?p=9074493#post9074493](http://ubuntuforums.org/showthread.php?p=9074493#post9074493)

---

