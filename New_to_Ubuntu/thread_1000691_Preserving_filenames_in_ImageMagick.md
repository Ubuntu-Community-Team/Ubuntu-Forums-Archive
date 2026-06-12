---
title: "Preserving filenames in ImageMagick"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Tetenterre on 2008-12-03
Is there a way of using [COLOR="Red"]**convert**[/COLOR] so that it will preserve filenames in a batch conversion. I have tried

```
convert *.bmp *.png
``` 

as suggested in another thread, but it merely outputs the files as **-1.png, *-2.png*, etc.

Also, is there a way of getting [COLOR="Red"]**convert**[/COLOR] to work on subfolders?

---

### Post by kaibob on 2008-12-06
> **Tetenterre said:**
> Is there a way of using [COLOR="Red"]**convert**[/COLOR] so that it will preserve filenames in a batch conversion....

You can use the mogrify command-line utility to convert a series of image files to another format with the same base file name. To do this, open a terminal window and change to the directory that contains the image files. Then, enter the following:

```
mogrify -format png *.bmp
```

As you are probably aware, mogrify is a part of the imagemagick suite and performs essentially the same functions as the convert utility. The above command does not overwrite or change the original files in any manner. 

If you still want to use the convert utility, the following command line will do what you want:

```
for file in *.bmp ; do convert "$file" "${file/%bmp/png}" ; done
```

As always, test the above on some files to make sure all works as expected.

---

