---
title: "Resizing multiple images at once"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by adobrakic on 2009-02-07
I need to resize all of the pictures on my pmp to 69x69. They're all in the following:

Music > Artist > Album > Cover.jpg

Yes, they are all named 'cover.jpg,' except they're all in their own album folder. I found out about mogrify, but I have no idea how to make it scan all of the subfolders in a main folder and resize *.jpg to 69x69.

Any help?

---

### Post by Het Irv on 2009-02-07
try this ```
ls -R ~/Music/ | grep cover.jpg | mogrify 'enter the stuff for mogrify here'
```

The first section will ls all your files is in the /Music file, the second section will filter out just the cover.jpg files, the last section will run the mogrify commands.

---

### Post by kaibob on 2009-02-07
This will also do what you want:

```
find /directory/name -iname cover.jpg -type f -exec mogrify -resize 69x69 '{}' ';'
``` 

You show both Cover.jpg and cover.jpg, so I used the -iname option, which is not case sensitive. You need to change the /directory/name to whatever you want. The mogrify command overwrites existing files; you may want to consider the use of the convert command or test this on duplicate files. 

See the following page for information on the resize option:

[http://www.imagemagick.org/script/command-line-processing.php#geometry](http://www.imagemagick.org/script/command-line-processing.php#geometry)

Perhaps a better alternative is phatch:

[http://photobatch.stani.be/](http://photobatch.stani.be/)

BTW, I don't know what a pmp is. I don't know if that will change anything.

---

### Post by The Cog on 2009-02-07
I don't think mogrify takes the filenames from stdin. This might do better:
```
ls -R ~/Music/ | grep cover.jpg | xargs mogrify 'enter the stuff for mogrify here'
```

---

### Post by kaibob on 2009-02-07
Deleted by Kaibob

---

### Post by adobrakic on 2009-02-07
Thanks! 
:)

---

