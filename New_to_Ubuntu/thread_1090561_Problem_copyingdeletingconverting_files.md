---
title: "Problem copying/deleting/converting files"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by mjawh on 2009-03-08
Hi, I'm new with Ubuntu, use version 8.04. I tried to copy some (many) mp3 files from a cd. It copied the first folder, then started to give errors on every next file: 

Cannot copy to ... (Music directory)
Error reading from file: Input/output error

Now I can't even delete those bad files because it says permission denied. Changing permissions for myself in properties doesn't help... The files on the CD are not damaged, I checked. Before deletion I tried to convert some of them to ogg because the VLC player plays them with noise, but SoundConverter doesn't work on them, it either creates an empty file or doesn't create anything at all. Maybe because of this, I'm thinking now. (I tried other converters, too: none worked) I renamed one directory that had a space in its name, still doesn't work. I'm tired of googling and reading all day long, and nothing works, can somebody just tell me please what is wrong?!!!

---

### Post by cariboo on 2009-03-08
How  are you copying music files from cd to your hard drive. There are several applications for ripping cd's. Go to System-->Administration-->Synaptic Package Manager and click ther search button and enter cd ripper, this should give you a selection of ripping software try them all until you find the one that suits you.

To delete files you don't have permissions to, press Alt-F2 and type:

```
gksu nautilus
```

this will open the file manager as root, and allow you to delete the files.

Jim

---

### Post by hyper_ch on 2009-03-08
I guess if you copied them from CD they are marked as read-only.

---

### Post by mjawh on 2009-03-08
> **cariboo907 said:**
> How  are you copying music files from cd to your hard drive.

Normally, with Copy and Paste. I copied them to the CD from Windows. They were mp3, not cda. Does it make a difference to the system what type of files they are, mp3 or other, shouldn't it just copy the data?

Thanks, I'll try your advice. How do I unmark the read-only attribute when I get so far?

---

### Post by hyper_ch on 2009-03-08
have a look at the permissions properties of the file. What can owner, group, world do?

---

### Post by mjawh on 2009-03-08
Ok, now it lets me to delete the files and change permissions!

Other times I don't have to copy files from CD using a cdripper, or do I?

But the Soundconverter still doesn't work. It creates empty ogg files. Isn't 1.0.1 an old version? But I don't get a newer one.

---

### Post by hyper_ch on 2009-03-08
as a cd is read-only files you copy from a cd will by default be marked as read only.

Do you have ubuntu-restricted-extra or kubuntu-restricted-extra installed? if you want to play mp3s you need to have the codec.

---

### Post by mjawh on 2009-03-08
> **hyper_ch said:**
> Do you have ubuntu-restricted-extra or kubuntu-restricted-extra installed?

Is it an application or is it codec?


Anyway, I'm worried why the Soundconverter doesn't work because everyone says it's such a good one, and for me it doesn't work.

And what is the right way to copy files from a CD so that I don't get this input/output error I mentioned in the first post? Run the nautilus as su and copy then?

---

### Post by hyper_ch on 2009-03-08
start synaptic, search for those packages above and then you'll know what it is :)

---

### Post by mjawh on 2009-03-08
> **hyper_ch said:**
> start synaptic, search for those packages above and then you'll know what it is :)

:D It's working now!

Thanks!

---

