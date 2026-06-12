---
title: "Setting up VSOconvertx in wine"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Doug11 on 2009-02-11
I just installed vsoconvertxtodvd in wine. the installation went well but i can't get it to see my dvd drive. I went into configure wine but i'm not quite sure if I'm doing the right thing.

---

### Post by Temposs on 2009-02-11
In a terminal, type:

```
ls /media
```

You should see a couple cdrom entries, at least one with a number after it. Mine says cdrom0.

Now go into Configure Wine, and click the Drives tab. Under D:, check that the Drive Mapping listed is one that exists for you. Mine says /media/cdrom0, and I do have a cdrom0 when I check the media directory.

If all this checks out and it still doesn't work, then it may be an incompatibility with the program, for which there may or may not be a tweak/hack you can apply to get it working.

---

### Post by Doug11 on 2009-02-11
OK,,that helped,,I also had to go into the advanced tab and select what type of drive it was,,the default was a HD not a cd rom. Thanks.

---

