---
title: "Command line print jpg to pdf"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by emsenn on 2009-01-17
I'm looking for a way, on the command line, to print a jpeg image to a PDF.  I can do it graphically if I open it in eye of gnome and print from there.  However, I'm looking to batch process, and the GUI way will not work.

Does anyone know how to, from the command line, print a jpg to a pdf?  Of course, other ways of converting a jpg to a pdf would also work.

---

### Post by kaibob on 2009-01-17
There are a lot of way to do what you want. The easiest is to use the mogrify command-line utility, which is a part of the imagemagick suite. Just open a terminal window, change to the directory that contains the JPG files, and enter:

```
mogrify -format pdf *.jpg
```

The above command retains the existing JPG files and creates new PDF files. If you have any problem with this, you can also use the convert utility from the imagemagick suite by way of the following command line:

```
for file in *.jpg ; do convert "$file" "${file/%jpg/pdf}" ; done
```

If imagemagick is not already installed on your computer, it's in the repo's.

---

### Post by emsenn on 2009-01-17
First one works great for my needs - thanks!

---

