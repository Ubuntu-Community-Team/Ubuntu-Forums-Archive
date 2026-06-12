---
title: "'wget' command only downloads thumbnails."
date: 2010-10-24
forum: New to Ubuntu
---

### Post by imotox on 2010-10-24
I want to download a bunch of images from a site so I tried using wget. However it only downloads the thumbnails of those images and I can't get it to work better. Could one of you help me please and explain what I did wrong/needed to change so I can learn? This is what I have.

```
wget -P pics -p -nd -l2 -H -A.jpg -erobots=off http://boards.4chan.org/p/res/1044003
```


*FYI: If you know about 4chan and are scared of the link, this link is safe as it is to the photography board. These are artistically oriented pictures of a storm that was going on.*

I finally figured it out and if anyone is curious on how to do it, this is how I did it:

```
wget -P pics -H -nd -r -Dimages.4chan.org -A.jpg -erobots=off http://boards.4chan.org/p/res/1044003
```

Where:
'-P [name]' gives it the directory name of the folder in your home folder
'-H' Goes to outside links
'-nd' is no-directory which won't put the images in separate folders.
'-r' is recursive
'-A[.extension]' tells it what extensions to download
'-D[location]' is the server location you're restricting it to
'-erobots=off' makes it so you don't get bot files

---

### Post by genjix on 2011-03-15
Thank you! I found you from google.

Here's a better command,
```
wget -P pics -H -nd -r -Dimages.4chan.org -A '.jpg,.jpeg,.png,.gif,' -erobots=off http://boards.4chan.org/b/res/315938092
```

(downloads other image files too)

For extra goodness, add this to your .bashrc:
```
function spider4chan() { wget -P pics -H -nd -r -Dimages.4chan.org -A '.jpg,.jpeg,.png,.gif,' -erobots=off "$1"; }
```

Now when I run spider4chan [linkname], it will download all the images from that page.

$ cd /tmp/
$ spider4chan [http://boards.4chan.org/b/res/315938092](http://boards.4chan.org/b/res/315938092)

/tmp/ is cleared everytime you reboot, so you can view the images and then forget about them.

---

