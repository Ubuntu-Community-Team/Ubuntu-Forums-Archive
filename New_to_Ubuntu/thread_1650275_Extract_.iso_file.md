---
title: "Extract .iso file"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by Linyx on 2010-12-21
[SIZE="2"]i Have some .ISO files, which i want to extract, although i don't want a Command-line for Extraction... Some days before whenever i right-Click on .ISO file, it give me an option ,something like "Archeive.." which i didn't remember Exactly,
but that tools allows me to extract file to destination..
So i want that option to come back.....


Any suggestions?[/SIZE]

---

### Post by ppv on 2010-12-21
Can you try opening it with the archive manager. You could first open the archive manager and then use the open file option to select your file.

---

### Post by Verbeck on 2010-12-21
right click>open with other application>archive manager

---

### Post by Linyx on 2010-12-21
> **ppv said:**
> Can you try opening it with the archive manager. You could first open the archive manager and then use the open file option to select your file.

[SIZE="2"]Thanks for reply, i don't have Archive-manager, but i have Archive-mounter instead....let me install it from Synaptic,.....BRB[/SIZE]

---

### Post by seawolf167 on 2010-12-21
You'll have to mount the iso image then copy the contents to a new directory.

The command line option goes something like this:

```
mount -o loop -t iso9660 /path/to/file.iso /mount/location
```But an easier GUI way to do this is to get the program gmountiso and have it do the heavy lifting for you 

```
sudo apt-get install gmountiso
```All you have to do then is browse to and select the iso you want to mount and where you want to mount it the copy the contents out.

---

### Post by kgarbutt on 2010-12-21
You can probably use Furius ISO Mount to mount it, and then you can use Nautilus to view the files.

Check Furius out using the terminal:

apt-cache show furiusisomount

Install using the terminal:

sudo apt-get install furiusisomount

---

### Post by Linyx on 2010-12-21
[SIZE="2"]thanks seawolf167, but i want to Get back **Archive manager**....

I searched via synaptic,,..No Luck :([/SIZE]

---

### Post by Verbeck on 2010-12-21
> **Linyx said:**
> [SIZE=2]thanks seawolf167, but i want to Get back Archive manager....

I searched via synaptic,,..No Luck :([/SIZE]
search for file-roller
or run[I] 
sudo apt-get install file-roller
[/I](confusing name, isn't it)

---

### Post by beew on 2010-12-21
Install acetoneiso from the repository or better, a ppa for an up to date version. It has a function for extracting iso content to folder (and many more features)

Archive Manager is called "file-roller" in Synaptic. It is a piece of crap IMO. I use p7zip for archiving. It has a gui called Q7Z which you can download from sourceforge. Works much better.

---

### Post by Linyx on 2010-12-21
[SIZE="2"]Thanks to both :p , file-roller Solved it[/SIZE]

---

