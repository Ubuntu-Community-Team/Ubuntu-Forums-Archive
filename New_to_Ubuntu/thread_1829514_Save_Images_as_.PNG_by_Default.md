---
title: "Save Images as .PNG by Default?"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by ZachGretzinger on 2011-08-20
Looking for a way (if it is possible) for any image I save online to be saved as .PNG by default.

Is this possible?

I'm using Ubuntu 11.04. My preferred browser is Google Chrome

Thanks!

---

### Post by Basher101 on 2011-08-20
It is not possible to save them from the net like that. But you can always open them with GIMP and then change the file extension to .PNG

---

### Post by Frogs Hair on 2011-08-20
Often , simply renaming the images .png after download works . I have found a some images that don't allow the change and in that case I use Gimp .

---

### Post by coffeecat on 2011-08-20
> **Frogs Hair said:**
> Often , simply renaming the images .png after download works .

Changing the filename extension does not convert the file. If you rename file.jpg to file.png, you simply end up with a jpeg with a png filename extension. This doesn't confuse Linux (or MacOS) because most apps use the file header to determine the file type. A Linux app will still treat the file as a jpeg despite the png extension. Windows is another matter; I haven't tried it but I guess it might get confused, because Windows does rely on the extension.

Unconvinced? Look at this:

```
coffeecat@oneiric-testing:~$ file testimage.jpg 
testimage.jpg: JPEG image data, EXIF standard 2.2
coffeecat@oneiric-testing:~$ mv testimage.jpg testimage.png
coffeecat@oneiric-testing:~$ file testimage.png
testimage.png: JPEG image data, EXIF standard 2.2
```

---

