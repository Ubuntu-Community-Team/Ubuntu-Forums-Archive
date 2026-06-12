---
title: "Image Viewing through directories"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by manuleka on 2009-01-27
wondering if there's any image viewer that i can use that will enable me to browse through all my images if i just select a parent directory which contains all children and grandchildren directories of images and photos...

default ubuntu image viewer only views the current directory images... i'm after something that will run current currently contents and child directories

something lite and quick... any recommendations? cheers

---

### Post by kaibob on 2009-01-27
Feh will view image files recursively. To try this, open a terminal window and change to the top level directory that contains the imagefiles. Then enter:

```
feh -r *
```

Feh is in the repo's and takes up very little space. Features are:

[http://linuxbrit.co.uk/feh/wiki/FehFeatures](http://linuxbrit.co.uk/feh/wiki/FehFeatures)

---

### Post by manuleka on 2009-01-28
when you say terminal, does that mean i can only run it through terminal or is there a GUI version?

---

### Post by kaibob on 2009-01-28
> **manuleka said:**
> when you say terminal, does that mean i can only run it through terminal or is there a GUI version?
No, you do not have to open feh through the terminal, although you do have to specify a directory that contains image files. For example, say that you want to view image files in your ~/pictures directory. The command line--which could be placed in a panel launcher--would be:

```
feh ~/pictures
``` 

You could also start feh by way of a nautilus script or nautilus action or as a default nautilus open-with application. But, feh is a light and quick image viewer and nothing else. Perhaps another forum member will suggest a more full-featured image viewer that opens image files recursively.

---

### Post by manuleka on 2009-01-28
i manage to try out F-Spot Photo Manager to view photos... it's viewer works well

---

