---
title: "How to join images side by side?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by sundol on 2009-07-27
I have two .tiff files.
I want to join the bottom side of an image and the top side of the other image.

How to do this?

Thanks.

---

### Post by earthpigg on 2009-07-27
i have had outstanding success with 'hugin'. it is in the repos.

[link to contribution i made to wikipedia, thanks to hugin]("http://en.wikipedia.org/wiki/File:Panorama_cropped.png")

---

### Post by zeroseven0183 on 2009-07-27
You can use GIMP, crop the parts and create a new image out of it.

---

### Post by earthpigg on 2009-07-27
> **zeroseven0183 said:**
> You can use GIMP, crop the parts and create a new image out of it.

gimp is good for a lot but, unless it has features i am not aware of, this will not work unless he took the pictures with an absolutely perfect tripod.

---

### Post by kaibob on 2009-07-27
The montage utility from the Imagemagick suite is another option to consider. For example:

```
montage -tile 1x2 -geometry +0+0 image1.jpg image2.jpg newimage.jpg
```

[http://www.imagemagick.org/script/montage.php](http://www.imagemagick.org/script/montage.php)

---

### Post by sundol on 2009-07-27
> **kaibob said:**
> The montage utility from the Imagemagick suite is another option to consider. For example:

```
montage -tile 1x2 -geometry +0+0 image1.jpg image2.jpg newimage.jpg
```

[http://www.imagemagick.org/script/montage.php](http://www.imagemagick.org/script/montage.php)

Thank you. :D It works!!

---

