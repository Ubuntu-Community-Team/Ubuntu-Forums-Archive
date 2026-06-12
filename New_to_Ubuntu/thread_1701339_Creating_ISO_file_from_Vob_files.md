---
title: "Creating ISO file from Vob files"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by boldhoof on 2011-03-06
Hi

I have tried and tried, but seem to fail. I have a number of DVD files, that I created under windows, and had on a external drive. Now I want to burn them using Xubuntu, but can't find a program to burn the vob files etc as I want to keep the structure of the menu's I made. I notice i can burn ISO files, but can't figure out how to create an iso to burn. Anyone help please.

Thanks

---

### Post by vanadium on 2011-03-06
I guess this means you have the DVD structure on disk, i.e. VOB, IFO and other files in a directory VIDEO. It should be possible to burn these to a Video DVD using the common tools such as Brasero under gnome.

If the DVD is in a folder DVD in the current directory, then following command will make the ISO
```

mkisofs -dvd-video -o movie.iso DVD/

```

---

### Post by boldhoof on 2011-03-06
Thanks for the pointer. I am slowly learning how to use the command line. I have also been looking at Linux Nero.

---

