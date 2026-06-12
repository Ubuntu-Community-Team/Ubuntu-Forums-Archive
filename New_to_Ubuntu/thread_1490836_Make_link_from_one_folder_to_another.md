---
title: "Make link from one folder to another"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by inameiname on 2010-05-22
I right click and 'create link' of one folder, and put it into another, however all that is watched are the files in that directory, not any subdirectories that are in there as well, including any files and folders inside directory I just made the link for.

My question is if I can make it so it looks inside subdirectories as well; otherwise I'll have to link every single thing from the folder I linked. Seems like unnessary step, especially if I may want to add more things into it later on.

---

### Post by cariboo on 2010-05-23
What are you trying to accomplish, by linking folders?

---

### Post by inameiname on 2010-05-23
I have a script that starts on login which changes wallpaper at random, and I was hoping I could link both "/usr/share/backgrounds/" (the default one which currently has several) and an easily more accessible folder, "~/Pictures/Backgrounds/" (for my friends and family who wish to add any new ones into), so it'd randomly choose any picture out of those two as my desktop background.

My current solution is to just link all 20 pictures which are in "/usr/share/backgrounds/" into "~/Pictures/Backgrounds/". This method seems to be working just fine.

My original hope was I could change in the script itself to immediately look in more than one directory, such as:

imagefolder = "/usr/share/backgrounds/"
imagefolder = "~/Pictures/Backgrounds/"

...but that doesn't work, and asking if I could in another posting on here, somebody told me it wasn't possible.

---

### Post by inameiname on 2010-09-08
I just found a better script to use. So I'll mark this as solved.

```

#!/usr/bin/env python

BACKGROUND_DIRS = ['/usr/share/backgrounds', '~/Pictures/Backgrounds']
EXTENSIONS = ['jpeg', 'jpg', 'bmp', 'png', 'svg']

import os, glob, random, itertools, gconf

files = list(itertools.chain(*[[os.path.join(dirpath, name)
                                for name in filenames]
                               for dirpath, dirnames, filenames in
                               itertools.chain(*[os.walk(os.path.expanduser(d))
                                                 for d in BACKGROUND_DIRS])]))
gconf.client_get_default().set_string(
    '/desktop/gnome/background/picture_filename',
    random.choice(files))

```

---

