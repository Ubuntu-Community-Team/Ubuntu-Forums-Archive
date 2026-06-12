---
title: "[SOLVED] reducing photos for email transmission"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by gracefaith on 2008-12-15
I have Gimp downloaded but don't know what to do to make it work when emailing a photo. What do I need to do to make it work - or do I need another program? 

A minor matter - I wanted to indicate following a previous question which was well answered that the solution worked and the the thread was finished and to say thank you - which I understand is the normal courtesy - but I did not know how to! As you can see I am not at all computer literate so please assume nothing in offering your solutions!

Thanks

Guy

---

### Post by Shhnap on 2008-12-15
Do you want to make the file smaller in screen dimensions or in file size? Then i'll tell you how to do either.

---

### Post by nhasian on 2008-12-16
> **gracefaith said:**
> I have Gimp downloaded but don't know what to do to make it work when emailing a photo.

after you've opened a photo, in the toolbar go to *Image*, then *scale image*.  change the dropdown from pixels to percent.  now if you put 25% it will reduce the image to 25% its original size.  makes it easier to email. 


[QUOTE=gracefaith]A minor matter - I wanted to indicate following a previous question which was well answered that the solution worked and the the thread was finished and to say thank you - which I understand is the normal courtesy[/QUOTE]

you can mark your thread solved by using the *Thread Tools* at the top of your post and to thank someone click the "Thanks" icon [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG] on the bottom right corner of the post.

---

### Post by mike555 on 2008-12-16
I think there is a right click option , called "nautilus -resize" or something like that for Ubuntu..

---

### Post by davidsrsb on 2008-12-16
I find that with modern digital cameras reducing pixel count gives better image quality than aggressive jpeg compression for a given file size.

Using Gimp, this is done with "image"-"scale image"
Don't forget to save to a new file name

---

### Post by alienexplorers on 2008-12-16
I use gthumb.  I open the photo and then goto the image menu and choose resize.  Then I just insert or attach it to the email.

---

### Post by gracefaith on 2008-12-17
> **Shhnap said:**
> Do you want to make the file smaller in screen dimensions or in file size? Then i'll tell you how to do either.

It's the file size I want to reduce more than the actual photo size. I see that someone suggests just adjusting the pixels on the camera - a reasonable option  except that if you take a photo on higher resolution for  conventional printing, or have a photo already taken, that's not so good.


Thanks

---

### Post by starcannon on 2008-12-17
> **alienexplorers said:**
> I use gthumb.  I open the photo and then goto the image menu and choose resize.  Then I just insert or attach it to the email.
I just installed nautilus-image-converter, wow, thats as easy as it gets. Quick and simple, just r-click the image, click resize images, do what comes natural; it even allows you to do entire selections of images; thanks for the heads up on that mike555.

+1 for gthumb, for simple chores like resizing for email.

Gimp is great but a bit like using a car crusher on a soda can.

---

### Post by Tatty on 2008-12-17
> **mike555 said:**
> I think there is a right click option , called "nautilus -resize" or something like that for Ubuntu..
```
sudo apt-get install nautilus-image-converter
```

---

### Post by gracefaith on 2008-12-17
Can you advise step by step how to apply the nautilus or gthumb to the photos, from selection of photo to actually attaching it to the email?

Thanks

---

### Post by Tatty on 2008-12-17
> **gracefaith said:**
> Can you advise step by step how to apply the nautilus or gthumb to the photos, from selection of photo to actually attaching it to the email?

Thanks
I have never used gthumb.

To do it in nautilus run the code in my last post to install the nautilus image convertor extension, then i believe you just have to right-click on an image file, and it should give you some options.

---

### Post by vedavrata on 2010-04-08
I use gThumb under Ubuntu Linux.

When i save a JPEG file, i just can specify a Quality (%) but i can not see the old and the new file size, as well can not see the image difference (what i would lose), can't i ?.. 

How to see the both old (original) / new (will be saved) file size of JPEG file?
How to see the both old (original) image / new (will be saved) image simulaneously [in two modes "Fit to half a widnow / fit to half a widnow" and "No fit / no fit (i.e. 1:1 / 1:1)"] to evaluate visual quality ?

---

