---
title: "Are there any image viewers that can also convert file formats?"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by phubert28 on 2010-05-31
I have 64 bit Ubuntu 10.4

I know I had at least one image viewer under Windows XP that could also convert file formats easily as well as change the pixel density of an image (for avatars/icons).

Is there any such utility that runs under Liniux???

---

### Post by rhd on 2010-05-31
Gimp (Applications -> Graphics -> Gimp) can do the conversion job just via 'File -> Save As...' and then choose to 'Choose File Type (By Extension)'
To resize an image in Gimp, use 'Tools -> Transform Tools -> Scale' and choose your desired pixel size. Some formats, like png or jpeg, allow for a compression scale to be set in the save as dialog.

---

### Post by phubert28 on 2010-05-31
Never tried Gimp tho I downloaded and installed it on Windows.
But it's a tad heavy for image thumbnails and format conversion, isn't it?
Does Gimp even DO thumbnail views???

I had Screenthemes on Windows and about 1,700 images thru them. Of course they can't be extracted to jpg's - or extracted PERIOD, so I'm building a new portfolio.

Even that, of course, won't match the 'pack' partitioning functionality of Screenthemes ([www.Screenthemes.com](www.Screenthemes.com)).

OTOH, this way I AM getting only the individual images I SELECT.

Ran into an image that CAME with the system that has a .png extension, and I BELIEVE it is the boot theme backgound, but Image viewer can's bring it up, saying it's not a png file... that made me think of the various image viewers under Windows.

It keeps looking as though I will continue to need Windows for a number of things...

---

### Post by sica07 on 2010-05-31
Try gthumb. You can resize your images with it, browse them as thumbnails, convert them as jpg, png, tiff, etc. What I like most about gthumb is that it can do lossless transformation of JPEG.

---

### Post by alphacrucis2 on 2010-05-31
> **sica07 said:**
> Try gthumb. You can resize your images with it, browse them as thumbnails, convert them as jpg, png, tiff, etc. What I like most about gthumb is that it can do lossless transformation of JPEG.

+1 for gthunb but the lucid version seems to be fairly old. I'm running the one from the webupd8 ppa.

---

### Post by mike555 on 2010-05-31
You could install "nautilus-image-converter" ... but if you open an image and want to save it as something you can just tell it to by setting the extension (on the save as name)...... at least that works for me..

---

### Post by mkvnmtr on 2010-05-31
I resize images with the nautilus add on.Do not even need to open the image. Not as elegant as some of the others but fast.

---

### Post by phubert28 on 2010-05-31
Thanks to all for the responses. I'll look into each of them!

---

### Post by phubert28 on 2010-05-31
Problem:
I installed gthumb but found something odd.

I had images copied to /usr/share/backgrounds

However, I didn't care for some images that CAME WITH the system and created two directories under backgrounds: archive and cosmos.

Using sudo to run gthumb (after I observed this without doing so), the program shows those two directories as EMPTY, but in a terminal session I see the contents I MOVED there (ls -Al)

Nautilus also has no problem seeing the files... all jpg's.

??? any thoughts ???

---

### Post by The Cog on 2010-05-31
For doing large numbers of images, try imagemagick - it's in the repositories. It's command line only but that means you can script mass conversions easily.

Example:
mogrify -format png  -resize 96x96 *.jpg

---

### Post by alphacrucis2 on 2010-05-31
> **phubert28 said:**
> Problem:
I installed gthumb but found something odd.

I had images copied to /usr/share/backgrounds

However, I didn't care for some images that CAME WITH the system and created two directories under backgrounds: archive and cosmos.

Using sudo to run gthumb (after I observed this without doing so), the program shows those two directories as EMPTY, but in a terminal session I see the contents I MOVED there (ls -Al)

Nautilus also has no problem seeing the files... all jpg's.

??? any thoughts ???

Possibly something to do with file permissions. BTW you are supposed to run gui apps via gksu rather than sudo.

---

### Post by Kevin McCready on 2012-04-02
update as of 2 April 2012
ImageMagick is a software suite to create, edit, and compose bitmap images.
It can read, convert and write images in a variety of formats (over 100)
including DPX, EXR, GIF, JPEG, JPEG-2000, PDF, PhotoCD, PNG, Postscript,
SVG, and TIFF. Use ImageMagick to translate, flip, mirror, rotate, scale,
shear and transform images, adjust image colors, apply various special
effects, or draw text, lines, polygons, ellipses and Bézier curves.
All manipulations can be achieved through shell commands as well as through
an X11 graphical interface (display).

---

