---
title: "imagemagick and the &quot;cp&quot; command"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by al.adab on 2010-10-10
learning to use imagemagick - the aim is to batch-resize pictures, mainly. 

here's what I'm doing to create a *thumb* folder: 

*~$ cd /home/xxxxxx/Pictures/Pentax/Portugal/100_2508* (enter)
*~/Pictures/Pentax/Portugal/100_2508$ mkdir thumbs* (enter)
*~/Pictures/Pentax/Portugal/100_2508$*

I'd like to copy /home/daniele/Pictures/Pentax/Portugal/100_2508/ into *thumbs*, and here's where I get stuck: 

*~/Pictures/Pentax/Portugal/100_2508$ cp /home/daniele/Pictures/Pentax/Portugal/100_2508/ /home/daniele/Pictures/Pentax/Portugal/100_2508/thumbs/* (enter)

[I]cp: omitting directory `/home/daniele/Pictures/Pentax/Portugal/100_2508/'
xxxxxx@xxxxxx:~/Pictures/Pentax/Portugal/100_2508$ [/I]

I tried a number of variations, like adding an * after */home/daniele/Pictures/Pentax/Portugal/100_2508*/ and/or avoiding spaces, but it doesn't work. 

Also it's not clear (to me) the *mogrify* bit. I suppose that once I get the cp command right I should carry on with

*cd thumbs*

At this stage, is it enough to enter 

*mogrify -resize 640 *.jpg*

(if I want to resize it to 640) to resize all the pictures at the above directory?

Any help will be highly appreciated. Thanks.

---

### Post by Vaphell on 2010-10-10
what happens with * at the end of source path in cp?

---

### Post by al.adab on 2010-10-10
~$ cd /home/xxxxxx/Pictures/Pentax/Portugal/100_2508
~/Pictures/Pentax/Portugal/100_2508$ mkdir thumbs
~/Pictures/Pentax/Portugal/100_2508$ cp /home/xxxxxx/Pictures/Pentax/Portugal/100_2508/***** /home/xxxxx/Pictures/Pentax/Portugal/100_2508/thumbs/ 
cp: omitting directory `/home/daniele/Pictures/Pentax/Portugal/100_2508/thumbs'
xxxxxx@xxxxxx:~/Pictures/Pentax/Portugal/100_2508$

---

### Post by SeijiSensei on 2010-10-10
You need the -r switch to cp to have it "recurse" through subdirectories.  If I were you, though, I'd read up on [rsync]("http://samba.anu.edu.au/ftp/rsync/rsync.html") which is a much more elegant solution.  

You can't use mogrify to make a new file; it only transforms the input file and leaves it in the same location.  Here's some suggestions on how to use a script with the "convert" command to do what you want: [http://www.imagemagick.org/Usage/basics/#mogrify_not](http://www.imagemagick.org/Usage/basics/#mogrify_not).  The first example using a "for" loop is probably the easiest solution.  Something like this:

```
cd /home/xxxxxx/Pictures/Pentax/Portugal/100_2508
mkdir -p thumbs
for f in *.JPG
do convert $f -resize 640 thumbs/$f
done
```

takes all the jpegs in your source directory and creates 640 pixel wide jpegs with the identical name in the thumbs subdirectory.  (If the filenames are in lower-case, replace "JPG" with "jpg"; Unix is case-sensitive.)  You can just type each line at the prompt.  If you're going to be doing this often, you might consider writing a simple bash script.

---

### Post by mcduck on 2010-10-10
I'd use convert instead of mogrify, (they are pretty much the same, only difference is that convert makes a copy of the images, keeping the originals intact, while mogrify replaces the original image.

With convert you wouldn't even need to copy the images yourself:
```
mkdir thumbnails
for i in *.jpg; do convert $i -resize 640 -quality 86 -strip thumbnails/tn-$i; done
```
"-quality" sets the compression for jpg, I've found 86 to be a decent compromise between quality and file size. The value is between 0 and 100, but the effect on file size isn't completely linear so try a bit with different settings to see what works best for you. 

"-strip" removes EXIF data from images, you probably don't need to keep it in thumbnail files and removing it reduces the file size.

edit: too slow. :D

---

### Post by al.adab on 2010-10-10
feeling kind of lost - apologies

I tried rsync and didn't get anywhere - am now trying the "convert" option. Maybe you can help me out with a couple of examples? (I keep getting error messages as with *cp*)

after
[I]~$ cd /home/xxxxxx/Pictures/Pentax/Portugal/100_2508
~/Pictures/Pentax/Portugal/100_2508$ mkdir thumbnails[/I]

what exactly do I do if I want to resize all the pictures in the above folder into small files (and leaving it to the program to decide on variables such as width and length) and - at the same time - copy the result into thumbnails?

---

### Post by mcduck on 2010-10-10
You'll have to give at least some value so *convert* knows what size images you want. Width or height, or both.

This command from my above post goes through all .jpg images in your current directory, resizes them to max width of 640 pixels (maintaining the aspect ratio of the original image), removes EXIF data from the image and then saves the new image to the new thumbnails directory you created (adding a "tn-" to the beginning of the thubnail file's names, so "image01.jpg"'s thumbnail would be named "tn-image01.jpg" )
```
for i in *.jpg; do convert $i -resize 640 -quality 86 -strip thumbnails/tn-$i; done
```

You can leave out the "-quality 86" and "-strip" if you want, those are just the options I always use to get small size files with decent image quality for viewing on displays. And of course change how the new images are named. The "$i" variable is the name of the image that *convert* is currently working with.

edit: actually the simplest command to do the same would be this:
```
for i in *.jpg; do convert $i -thumbnail 640 thumbnails/$i; done
```
"-thumbnail" resizes the image and removes some of the extra metadata from the image, but not as much as "-strip" does. "-thumbnail" works reasonably well for creating small thumbnails, if you are creating bigger images you'll want to use the first command instead for better control over image quality and file size.

---

### Post by al.adab on 2010-10-10
thanks mcduck for your help - though I do feel kind of stupid...well, here it goes: 

[I]xxxxx@xxxx:~$ cd /home/daniele/Pictures/Pentax/Portugal/100_2508
xxxxx@xxxx:~/Pictures/Pentax/Portugal/100_2508$ mkdir thumbnails
xxxxx@xxxx:~/Pictures/Pentax/Portugal/100_2508$ _for i in *.jpg; do convert $i -resize 640 -quality 86 -strip thumbnails/tn-$i; done_
[B]convert: unable to open image `*.jpg': No such file or directory @ blob.c/OpenBlob/2480.
convert: missing an image filename `thumbnails/tn-*.jpg' @ convert.c/ConvertImageCommand/2838.[/B]
xxxxx@xxxx:~/Pictures/Pentax/Portugal/100_2508$ [/I]

what do I do wrong? Is it the asterisk that I need to replace 
with

---

### Post by Vaphell on 2010-10-10
do you have any .jpg files (case sensitive) in that dir?

i tested ```
for i in *.jpg; do echo wtf-$i; done
```
and if the jpg files are there, it echoes their name (with appropriate prefix ;-) )
if there is no file matching, you get simple *.jpg in results (*.jpg is not treated as a mask but as a string to use in place of variable)

---

### Post by al.adab on 2010-10-10
case sensitive!!! for some reason the extension is in upper case, i.e., *.JPG*, so the right command is 

*for i in *.JPG; do convert $i -resize 640 -quality 86 -strip thumbnails/tn-$i; done*

thank you so much for you help! you've made my day! :)

---

### Post by al.adab on 2010-10-11
though the *cp* issue is still unresolved...(?)

---

