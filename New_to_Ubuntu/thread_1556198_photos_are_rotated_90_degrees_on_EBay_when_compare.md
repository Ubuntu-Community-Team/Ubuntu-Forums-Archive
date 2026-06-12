---
title: "photos are rotated 90 degrees on EBay when compared with GIMP"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by naomibrown on 2010-08-19
Hi,

I'm trying to upload some .jpg photos from GIMP to EBay. When I look at the photos in GIMP and in the File Browser they are rotated correctly, but when I upload them to EBay they are rotate 90 degrees clockwise. 

Any ideas why and what I could do to fix them?

Thanks,
Naomi

---

### Post by prshah on 2010-08-19
> **naomibrown said:**
> When I look at the photos in GIMP and in the File Browser they are rotated correctly, but when I upload them to EBay they are rotate 90 degrees clockwise.

Most cameras embed EXIF information to the jpg file. Usually this contains an entry for orientation; while EoG and GIMP parse this entry, it may be that Ebay is not checking this.

To confirm, use exiftool (it's in the repositories) to check the orientation, eg```
Thu Aug 19 @15:23:36:~/Pictures$ exiftool 2010-08-12\ 15.00.31.jpg |grep -i orient
Orientation                     : Horizontal (normal)

```

---

### Post by naomibrown on 2010-08-20
Thanks for your reply. I've had a look at [http://www.leancrew.com/all-this/2009/04/derotating-jpegs-with-exiftool/]("http://www.leancrew.com/all-this/2009/04/derotating-jpegs-with-exiftool/") and [http://www.abc-view.com/articles/article5.html](http://www.abc-view.com/articles/article5.html) and now I have more of an idea of what you're talking about.

I tried playing with one of my images, and this is what I got originally.

```
$ exiftool -Orientation IMG_8346.JPG_original 
Orientation                     : Rotate 270 CW
```

This is when I have set the orientation to 1. 

```
$ exiftool -Orientation IMG_8346.JPG 
Orientation                     : Horizontal (normal)
```

Unfortunately, when I upload them both (in turn) to ebay they both come out rotated 90 CW, so I still have the same problem.

Thanks,
Naomi

---

### Post by prshah on 2010-08-21
> **naomibrown said:**
> to ebay they both come out rotated 90 CW, so I still have the same problem.

Rotation using EXIF information is "soft" rotation, ie, the image is unchanged (Except for the EXIF information), and it is upto the viewer program to correct the orientation when the picture is displayed.

Try this:

Delete the orientation tag altogether```
exiftool -Orientation= IMG_8346.JPG
``` (Note the space after "=")

That should set it back to Horizontal.

Then, view it in your favorite viewer (Eg, Eye Of Gnome, built-in) and correct the rotation to your satisfaction. In EoG, Ctrl+R rotates left, and Ctrl+Shift+R rotates Right. This is a "hard" rotation, ie, the image is actually changed. Save (by Ctrl+S) the image.

Upload the image to Ebay and check if it is OK.

---

### Post by naomibrown on 2010-08-21
Great! That's working now. 

So basically ebay is ignoring the EXIF data. 

Is it possible to do the delete orientation code for every file in a directory without having to repeat this for each file by name?

Is there also a way to rotate the images in GIMP rather than having to do this manually for each file? 

Thanks for all your help!
Naomi

---

### Post by prshah on 2010-08-21
> **naomibrown said:**
> Is it possible to do the delete orientation code for every file in a directory without having to repeat this for each file by name?

```
exiftool -Orientation= *.jpg
``` (Note that case sensitivity applies, so you may have to use *.JPG)

Dunno about mass rotate though.

---

### Post by mörgæs on 2010-08-21
Xnview is a good program for batch conversion of pictures. The user interface is not as good as in other programs, but it works!

---

### Post by alphacrucis2 on 2010-08-21
> **prshah said:**
> ```
exiftool -Orientation= *.jpg
``` (Note that case sensitivity applies, so you may have to use *.JPG)

Dunno about mass rotate though.

I think imagemagic can do bulk editing rotations etc. I haven't used it myself though.

---

### Post by naomibrown on 2010-08-22
Thanks for the replies! I'm going to have an experiment later with batch rotations.

Quick question, how can I move all of the files with, for example, "_original" in the file name to a new folder, using the command line?

I now have two copies of each photo and it would be neat to do it like that. 

Thanks,
Naomi

---

### Post by coffeecat on 2010-08-22
> **naomibrown said:**
> Thanks for the replies! I'm going to have an experiment later with batch rotations.

Another one you might want to look at is a Nautilus extension. The package is nautilus-image-converter and is in the Ubuntu repositories. Once installed, all you have to do is select (in Nautilus) the image(s) you want to convert, right-click and you'll find both "Rotate.." and "Resize..." in the right-click menu.

Simple, neat and effective. It deserves to be more widely known about.

---

### Post by prshah on 2010-08-22
> **naomibrown said:**
> Quick question, how can I move all of the files with, for example, "_original" in the file name to a new folder, using the command line?

For your already created files, use ```
mv -v *_original* newdir/
``` For exif-edited files you create in the future, to do this in a single operation, use```
exiftool -Orientation= -o newdir/ *.jpg
``` which will strip the Orientation value and move the newly created file in to the directory newdir (which must exist).

---

### Post by naomibrown on 2010-08-22
> **coffeecat said:**
> Another one you might want to look at is a Nautilus extension. The package is nautilus-image-converter and is in the Ubuntu repositories. Once installed, all you have to do is select (in Nautilus) the image(s) you want to convert, right-click and you'll find both "Rotate.." and "Resize..." in the right-click menu.

Simple, neat and effective. It deserves to be more widely known about.

I've tried installing this package through the software centre but I don't see any rotate or resize options when I right-click :(

Thanks for the tip prshah, that is great!

Thanks,
Naomi

---

### Post by coffeecat on 2010-08-22
> **naomibrown said:**
> I've tried installing this package through the software centre but I don't see any rotate or resize options when I right-click :(

You probably have to restart Nautilus by logging out and in again or by rebooting.

---

### Post by naomibrown on 2010-08-22
> **coffeecat said:**
> You probably have to restart Nautilus by logging out and in again or by rebooting.

Sorry, I can be an idiot.

It works really well now, after a reboot!

---

### Post by KirbySmith on 2010-08-23
Me too, ...

... but with a bit of panic in between; the process removes a lot of seemingly unrelated files and when completed, Firefox page rendering was a mess.  However, rebooting has restored, as far as I can tell so far, a functioning Firefox.  I can only hope that improvements of this sort do not install older versions of files that Ubuntu has corrected for functional or security defects.

kirby

---

### Post by coffeecat on 2010-08-23
> **KirbySmith said:**
> Me too, ...

... but with a bit of panic in between; the process removes a lot of seemingly unrelated files and when completed, Firefox page rendering was a mess.  However, rebooting has restored, as far as I can tell so far, a functioning Firefox.  I can only hope that improvements of this sort do not install older versions of files that Ubuntu has corrected for functional or security defects.

kirby

Um... Which process? Batch resizing image files or batch editing EXIF data isn't going to remove files or affect Firefox. At least, I hope not. :?

---

### Post by KirbySmith on 2010-08-25
I was *not* referring to the use of the tool.  I was watching the install process for nautilus-image-converter and it performed a lot of package removals.  It was at the end of the install process that Firefox was a (temporary) mess.  I suppose this could be due to the repository version of the image converter being older than my Firefox version (3.6.8 )

kirby

---

### Post by col48 on 2010-08-25
I have had the same issue with a Digital Photoframe.  Viewing all the photos with GIMP they looked fine, but when copied to the photoframe (slowly :( as it can't do it quickly) many were 90degree rotated.  Inference: the photoframe was not automatically rotating them.

This thread tells you why, and gives a more efficient way to correct the problem than I found.

---

### Post by coffeecat on 2010-08-25
> **KirbySmith said:**
> I suppose this could be due to the repository version of the image converter being older than my Firefox version (3.6.8 )

I'd be surprised. I prepared a fresh install of 10.04.1 for a relative the other day - it's running Firefox 3.6.8 - and updated it fully before installing nautilus-image-converter with a load of other useful things. I'm sure that no packages were removed and Firefox is still running fine.

I've installed nautilus-image-converter in each of the last three or so releases of Ubuntu on my several machines and never seen anything like this. I don't know why you  had this problem.

---

### Post by KirbySmith on 2010-08-27
Good to know that it is rare or unique.  Maybe there was an interaction with NoScript.  In any case, the "problem" was temporary and I have had no issues with Firefox since then.

kirby

---

