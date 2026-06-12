---
title: "little app for resizing photos"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by ub9876 on 2009-10-26
is there a small app for resizing photos by percent, auto,
with just a clik or 2....????

---

### Post by vinutux on 2009-10-26
explain.... more plz...... there are a lot of tools.......

---

### Post by Warren Watts on 2009-10-26
[ImageMagick]("http://www.imagemagick.org/script/index.php") is a command line tool with TONS of features for manipulating image files.  

I'm positive you could use it to quickly scale images, etc....

---

### Post by oldfred on 2009-10-26
Some where I found these two scripts. Change to directory and right click, scripts and choose script to run. You can easily modify them if you want.
 
Copy them into 
~/.gnome2/nautilus-scripts

batch640x480
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
```Create_thumbs
```
#! /bin/sh

# Dialog box to choose thumb's size
SIZE=`zenity --list --title="Choose the thumbnail's size" --radiolist --column="Check" --column="Size" "" "320x240" "" "640x480" "" "800x600" "" "1024x768"`

if [ "${SIZE}" == "" ]; then    
zenity --error --text="Size not defined by user.
Please choose a size to use. "
exit 1
fi

# How many files to make the progress bar
PROGRESS=0
NUMBER_OF_FILES=`find -iname "*.jpg" -maxdepth 1 | wc -l`
let "INCREMENT=100/$NUMBER_OF_FILES"

mkdir -p thumbnails

# Creating thumbnails. Specific work on picture should be add there as convert's option
(for i in *.jpg *.JPG; do
echo "$PROGRESS";
echo "# Resizing $i";
convert -strip -resize "${SIZE}" -quality 80 "${i}" thumbnails/"${i}"
let "PROGRESS+=$INCREMENT"
done
) | zenity  --progress --title "$Creating thumbnails..." --percentage=0
```

---

### Post by shadow120 on 2009-10-26
the fastest way ive found to do it is online.  i use [http://www.picresize.com/](http://www.picresize.com/)

---

### Post by kaibob on 2009-10-26
Another option is the Nautilus Image Converter. It's in the repo's--some screen shots can be seen at:

[http://www.bitron.ch/software/nautil...-converter.php](http://www.bitron.ch/software/nautil...-converter.php)

You may also want to look at phatch:

[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by the.phantom on 2009-10-27
showFoto ( in applications add/remove)
a quick photo edit program and think 2 or 3 clicks it can resize by percent or pixels  and do other corrections and crop

---

### Post by kwokyinc on 2009-10-27
> **Warren Watts said:**
> [ImageMagick]("http://www.imagemagick.org/script/index.php") is a command line tool with TONS of features for manipulating image files.  

I'm positive you could use it to quickly scale images, etc....

Yup. I love this one too. very handy.

For example, the command "convert -resize 50% *" will help you reduce the size of all files in the directory by 50%

---

### Post by epswing on 2009-11-08
> **kaibob said:**
> Another option is the Nautilus Image Converter. It's in the repo's--some screen shots can be seen at:

[http://www.bitron.ch/software/nautil...-converter.php](http://www.bitron.ch/software/nautil...-converter.php)

You may also want to look at phatch:

[http://photobatch.stani.be/](http://photobatch.stani.be/)

I've install this via Synaptic, but how do I get it to show in right-click context menus?

---

### Post by bacardiandwatermelon on 2009-11-08
All the above apps are good, but simply just use gimp to resize my photos.

---

### Post by laidback on 2009-11-08
Think you need to reboot then you'll see them. (Probably only need to restartx but I reboot to be sure)

---

### Post by Viva on 2009-11-08
Try [nautilus image converter]("apt:nautilus-image-converter") You can resize or convert them using the context menu in nautilus.

---

### Post by stani on 2009-11-08
> **epswing said:**
> I've install this via Synaptic, but how do I get it to show in right-click context menus?

For nautilus you can install:
```
sudo apt-get install phatch-nautilus
```

Phatch should be available in the "Open with..." context menu.

---

