---
title: "List all files in subfolders"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Clippy on 2009-04-07
Hi all,

This is probably not a smart question!  I have a folder containing 53 subfolders, each of which contains 2-4 jpgs.  I want to print all of these jpgs, but I really don't feel like doing it one at a time.  So, how do I:

a) Painlessly copy all of the jpgs in the different subfolders to a single folder (note that most of the jpgs currently have one of only four names: 1.jpg, 2.jpg, etc.)

b) Print all the jpgs in some sort of clear order so that I don't have to sort them by hand after.

I was thinking that once I get all the files into one folder, I could just convert them into one large .pdf and print that, but there is probably a better way as that will likely reduce the image quality.

Any help is appreciated!

Cheers,
Clippy

---

### Post by iaculallad on 2009-04-07
> **Clippy said:**
> 

a) Painlessly copy all of the jpgs in the different subfolders to a single folder (note that most of the jpgs currently have one of only four names: 1.jpg, 2.jpg, etc.)

```
cp `find /home/username/ -name "*.jpg"` ~/where_to_copy
```

---

### Post by Anthon on 2009-04-07
Since your filenames are limited, to flatten the namespace into a single folder without overwriting files with others with the same name you would need to make new filenames that e.g. consist of the directory_originalname. Assuming your files are under a directory X and next to directory is a directory name "tmp":
cd X
for i in *; do cd "$i" ; for j in *.jpg ; do ln -s  "$j" ../../tmp/"$i"_"$j" ; done ; cd ..; done

That will get you one directory with symbolic links to the files. How to print the JPGs from there depends on what program you want to use for that and what kind of commandline option it has for doing so.

---

### Post by Clippy on 2009-04-07
Thank you to both of you for your help!

The second solution given produced the desired result, a directory of appropriately named symbolic links to the files.  Unfortunately, beginner that I am, I'm not sure where to go from there.  How can I use the symbolic links, given that when I attempt to access them I only get error messages?  Is there a way to turn these into hard links so that I can convert or print them?

---

### Post by Anthon on 2009-04-07
What kind of program are you using so that it would need hardlinks? What messages do you get? ( I assume you know you cannot move/delete the original files to which the soft links point without breaking things).

---

### Post by Clippy on 2009-04-07
> **Anthon said:**
> What kind of program are you using so that it would need hardlinks? What messages do you get? ( I assume you know you cannot move/delete the original files to which the soft links point without breaking things).

At this point I don't know what program I want to use - I'm planning to print the .jpgs, possibly on a remote Windows machine (my printer is unreliable) so if nothing else it would be nice to be able to transport the renamed files via USB stick.  Also, when I tried using imagemagick to convert the symlinked files to a single pdf in the terminal, I got the following error for each file: 

```
convert: unable to open image `directory_name_X.jpg': No such file or directory.
```
  

I get two error messages when I try to open a symlinked file (i.e., by double clicking).  The first says

> The Link "directory_name_X.jpg" is Broken. Move it to Trash?  This link cannot be used, because its target "X.jpg" doesn't exist.

After a few seconds, the second message appears:

> Opening "directory_name_X.jpg"  You can stop this operation by clicking cancel 

but it never does anything even after several minutes.

---

