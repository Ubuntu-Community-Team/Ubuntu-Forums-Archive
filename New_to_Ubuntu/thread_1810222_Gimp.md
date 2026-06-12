---
title: "Gimp"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by weezyrider on 2011-07-22
I'm trying to use it and it has some features that I like. However,
Today I was trying to save a picture as a BMP. I needed it as a BMP to import into SVG. Absolutely NO GO.

1. Mouse works fine in Gimp - select and use all tools, etc. 

2. The Wacom Bamboo tablet works the same - select and use all tools.

Except when you go to save as. You get the dialog box, and you can type in the name you wish to call the image, but that's it. You can't choose another folder, another file extension or anything. The mouse won't work, the tablet won't work, you can move a bit by the arrow keys and that's it! Save a copy is just the same. No selections will work.
Tapping cancel with the arrow won't work. All you can do is close the dialog box.

I finally had to just type in the extensions I wanted. One was PSD, and the other BMP. It did save in those formats, but apparently there is a dialog for BMP that I never saw.

Why the heck wouldn't the stupid Gimp do a save as?

I played around with SVG, and it didn't have a problem with save as.

This is 10.10 Ubuntu

The images did save in the typed in file format. I had to drag them to the pictures folder as the images were saved in documents.

---

### Post by SoFl W on 2011-07-22
> **weezyrider said:**
> Why the heck wouldn't the stupid Gimp do a save as?
This is 10.10 Ubuntu

What version of GIMP?

---

### Post by coffeecat on 2011-07-22
> **weezyrider said:**
> Absolutely NO GO.

Works for me.

Save as from file menu. Then, in Save Image window, "Select file Type (by extension)" and drop the arrow down. Scroll down to "Windows BMP image", click on save and image is saved.

---

### Post by SoFl W on 2011-07-22
In your "stupid GIMP", when you save a file do you have the selections "_B_rowse for other folders" and "Select File _T_ype (By Extension)"?  (see attached)

---

### Post by weezyrider on 2011-07-22
> **SoFl W said:**
> In your "stupid GIMP", when you save a file do you have the selections "_B_rowse for other folders" and "Select File _T_ype (By Extension)"?  (see attached)


Yes, but they are greyed out.  And they are in different places than yours. Folder is on the top and file format is under the list of folders. You simply cannot select/click on them.

It's Gimp 2.6/Meerkat

I bought a book on using Gimp and was enjoying some new techniques.

I tried saving and reopening the image, flattening the image, making sure there was no active selection. The only save that will go from Gimp's menu is their own file format which is useless anywhere else. Unlike a RAW file, I can't open this file in another program and change it.

---

### Post by Mr. Shannon on 2011-07-22
I don't know about the other issues but gimp will save the file to the format that you put after the name.  So if you name it mypicture.bmp then it should save it as bmp.  You don't actually have to choose the file type in the box at the bottom.

---

### Post by weezyrider on 2011-07-22
> **Mr. Shannon said:**
> I don't know about the other issues but gimp will save the file to the format that you put after the name.  So if you name it mypicture.bmp then it should save it as bmp.  You don't actually have to choose the file type in the box at the bottom.

It did do that, but the BMP format has some choices - like for windows, 16 bit, 2 bit, 32 bit.
The dialog box for that did pop up, but complained that the save as wasn' t done by the usual protocol. There is absolutely no way to add those by just typing in the file format. You need the dialog box

Also tiff has some choices on compression

---

### Post by Favux on 2011-07-22
Have you tried going into Synaptic Package Manager and telling it to reinstall Gimp?

If that doesn't work and uninstalling and reinstalling Gimp doesn't work then you might have corrupted user configuration files in ~/.gimp-2.6.  So you'd have to delete them after a complete uinstall before reinstalling.

---

### Post by weezyrider on 2011-07-23
Haven't touched any files except to get the tablet to run. I bought the book "Beginning Gimp" by Akkana Peck and just noticed that none of the save files menu look like what she has in the book, although the book was mostly for 2.4

About the tablet. It works fine in Ubuntu and other programs like the vector program for Ubuntu. a version of Paint, text editor, and the browsers. Why doesn't Gimp pick that up as well? If the tablet is already enabled in the OS, why does it need to be re-enabled in Gimp?

I'll try Synaptic.

---

### Post by weezyrider on 2011-07-23
Just tried reinstalling. Still doesn't work. However, when checking input devices in preferences in the Gimp menu, the mouse and tablet are there, but they don't show up in the active controllers dialog box. Linux input does, and double clicking on that brings up a configure box which says the mouse and tablet are not available, permission denied. 

Gimp will be almost useless unless the mouse and tablet work on saving. They work in the program, but for any save function, they don't.

---

### Post by jcolyn on 2011-07-23
> **weezyrider said:**
> 
It's Gimp 2.6/Meerkat

I've never heard of Gimp 2.6/Meerkat or did you add Meerkat yourself.

Current version is 2.6.11

Mine works fine. Just checked it...

---

### Post by weezyrider on 2011-07-23
Meerkat is the version of Ubuntu, and Gimp is 2.6.11.

It also won't open files in the normal way. It uses Ubuntu's format. Look at the attachment in a previous post. 

I looked up info on making tablet work in Gimp. When I try to configure the input devices, the mouse and tablet are listed, but only linux input shows up, and says device not available - permission denied. 
How do I get permissions for the mouse and tablet?
They work in all other programs.

---

