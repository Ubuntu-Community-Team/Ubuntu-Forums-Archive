---
title: "Phatch, So easy a caveman can..."
date: 2009-09-16
forum: New to Ubuntu
---

### Post by sillyboy on 2009-09-16
Please help. Using 8.04. I need to batch resize 20 GB of photos.  I was reading where Phatch was easy to use, and can batch resize.  I can not figure the thing out.  Could someone please spell this out for me??  Or is there another program I could use?

Thanks

---

### Post by oldfred on 2009-09-16
I downloaded several bash scripts and put them into the scripts file
~/.gnome2/nautilus-scripts
One I found again on the internet that has some flexibility:
[http://ubuntuforums.org/archive/index.php/t-509102.html](http://ubuntuforums.org/archive/index.php/t-509102.html)

I was primarily looking for thumbnails but you can obviously modify to suit:
```
#!/bin/sh batch640x480
# author: Bas Wenneker
# email: sabmann [ta] gmail [tod] com
# Use this script to batch resize all images in a folder.
# First open the folder and then use the script.

for file in `ls -l`
do
name=`echo $file | cut -f1 -d.`
  convert -strip -geometry 640x480 -quality 50 $file thumbnails/"${name}_640x480.jpg
done
```

---

### Post by sillyboy on 2009-09-16
Thank You

---

### Post by stani on 2009-09-23
> **sillyboy said:**
> Please help. Using 8.04. I need to batch resize 20 GB of photos.  I was reading where Phatch was easy to use, and can batch resize.  I can not figure the thing out.  Could someone please spell this out for me??  Or is there another program I could use?

Thanks

Hi, I'm the author of Phatch. Did you read the tutorials?
[http://photobatch.wikidot.com/tutorials](http://photobatch.wikidot.com/tutorials)

Can you describe what you try to do and why it is not working for you?

---

