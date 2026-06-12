---
title: "Simple Gimp Question"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by DGINSD on 2011-05-16
I'm putting together my own icon theme and I need to resize some 128 png images to various sizes I got the actual image resized with scale in Gimp, but how do I get the canvas to resize as well? Maybe if someone could point me to a good Gimp and Inkscape tutorial?

---

### Post by Lateralis on 2011-05-16
Assuming you have one layer, which you have resized, click Image -> Fit canvas to layers.

Tutorials: Google is your friend! 

[http://www.gimp.org/tutorials/](http://www.gimp.org/tutorials/)
[http://gimp-tutorials.net/](http://gimp-tutorials.net/)
[http://www.ghuj.com/](http://www.ghuj.com/)
[http://www.noupe.com/gimp/30-exceptional-gimp-tutorials-and-resources.html](http://www.noupe.com/gimp/30-exceptional-gimp-tutorials-and-resources.html)
[http://www.gimp-tutorials.com/](http://www.gimp-tutorials.com/)
[http://www.tankedup-imaging.com/gimp/layers.html](http://www.tankedup-imaging.com/gimp/layers.html)

---

### Post by mcduck on 2011-05-16
Just use Image->Scale Image. (or if you only want to change canvas size instead of scaling the whole image, then Image->Canvas Size.)

---

### Post by DGINSD on 2011-05-17
Thanks guys

Next question is there any way to automate rescaling a whole directory's worth of icons?

---

### Post by compmodder26 on 2011-05-17
This is fairly old and I have not tried it out, but it may give you what you want:

[http://ulyssesonline.com/2008/09/22/batch-resize-images-with-gimp/](http://ulyssesonline.com/2008/09/22/batch-resize-images-with-gimp/)

---

### Post by Ghost|BTFH on 2011-05-17
```
convert -resize 50% input.png output.png
```

I would use *.png *.PNG to make sure they're not overwritten.  This is a very ugly way to perform this, I know there's a more elegant way but the code is escaping me at this time.  However, for the time being until someone else comes along and tells you the elegant way to do this, the above will work properly.

If you take the 128x128 and reduct to 50% you get 64x64, do it to the new files and you get 32x32 and once more you'd get 16x16...kinda handy for such projects.

Cheers,
Ghost|BTFH

---

### Post by mcduck on 2011-05-17
I suppose the "elegant way" would be looping through all the images in the directory:

```
mkdir 64 
for i in *.png; do convert "$i" -resize 64x64 "64/$i"; done 
```
(this will save the resized images into a subdirectry named "64", just to avoid overwriting the original ones. )

edit: Note that the convert command is part of Imagemagick package, which is *not* installed by default.

edit2: In case you'd prefer a graphical tool for batch image processing instead of using command line, you might want to try [Phatch]("http://photobatch.stani.be/").

---

### Post by SeijiSensei on 2011-05-17
You can write simple bash scripts to resize all the images in a directory using ImageMagick convert.  There's also apparently a nautilus plugin called nautilus-image-converter that will resize all the images in a directory.  Do a search of the forums for "batch resize images" to get some suggestions.

---

### Post by bigsmitty64 on 2011-05-17
[THIS]("http://www.codeunit.co.za/2010/01/04/ubuntu-batch-resize-your-images-using-gimp/") may help you, never used it, but I'll probably give it a go. :P

[HERE]("http://bdhacker.wordpress.com/2011/01/04/resize-multiple-images-in-a-folder-batch-image-resize-in-ubuntu/") is another option I found :D

---

### Post by DGINSD on 2011-05-17
Thanks again knew there had to be a better way than one at a time. I'll give em a whirl when I get home.

---

### Post by audiomick on 2011-05-17
You might be interested in this, perhaps. ;) Another way of going at it.

[http://openubuntu.com/index.php/topic,885.msg29020.html#msg29020](http://openubuntu.com/index.php/topic,885.msg29020.html#msg29020)

---

### Post by DGINSD on 2011-05-17
> **mcduck said:**
> I suppose the "elegant way" would be looping through all the images in the directory:

```
mkdir 64 
for i in *.png; do convert "$i" -resize 64x64 "64/$i"; done 
```
(this will save the resized images into a subdirectry named "64", just to avoid overwriting the original ones. )

edit: Note that the convert command is part of Imagemagick package, which is *not* installed by default.

edit2: In case you'd prefer a graphical tool for batch image processing instead of using command line, you might want to try [Phatch]("http://photobatch.stani.be/").

I've tried to install the imagemagick twice but when I follow the testing instructions I get errors. I had to compile it from source. Anything special I need to do? Heres the error I get

> display: error while loading shared libraries: libMagickCore.so.4: cannot open shared object file: No such file or directory


---

### Post by DGINSD on 2011-05-18
K, I got the Phatch graphics editor to work but could never figure out ImageMagick, unfortunately Phatch doesn't seem to have a converter to .svg  next question is how would one convert a whole directorys worth of .png images to .svg images.

---

### Post by Perfect Storm on 2011-05-18
Simple remove the .svg files and replace them with .png files.

You can't convert them .png to .svg...well you can but the outcome may not turn what you expected.

.svg = Scalable Vector Graphics
[http://en.wikipedia.org/wiki/Scalable_Vector_Graphics](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

---

### Post by josephmills on 2011-05-18
> **DGINSD said:**
> K, I got the Phatch graphics editor to work but could never figure out ImageMagick, unfortunately Phatch doesn't seem to have a converter to .svg  next question is how would one convert a whole directorys worth of .png images to .svg images.

I ran acrros this hope it helps [http://www.porpoisehead.net/mysw/index.php?pgid=gimp_svg](http://www.porpoisehead.net/mysw/index.php?pgid=gimp_svg)

---

### Post by jtarin on 2011-05-18
As you probably know by now in your search for icon enlightenment, start with a 256px .svg then you can downsize and convert all you want.
[Here's imagemagick for 10.10]("https://launchpad.net/ubuntu/maverick/+package/imagemagick").

---

### Post by DGINSD on 2011-05-19
can you set up .png files to be scalable? If so no problem. What I mean by this is if I set the icons index.theme file to set a directory of .png as scalable will it work ok?

I changed a few .png's to .svg by opening them with inkscape and then saving as, probably not the right way to do it but...

---

### Post by jtarin on 2011-05-19
Yes,but they would suck.....resolution.

---

### Post by mcduck on 2011-05-19
> **DGINSD said:**
> can you set up .png files to be scalable? If so no problem. What I mean by this is if I set the icons index.theme file to set a directory of .png as scalable will it work ok?

I changed a few .png's to .svg by opening them with inkscape and then saving as, probably not the right way to do it but...

No, they are still bitmap images, not vector images so it makes no difference.

...and same goes for just importing a bitmap image into Inkscape and saving it. That just gives you a bitmap image saved (or in worst case just linked) as texture inside SVG file. It won't scale any better than the original PNG image did.

Inkscape *can* trace bitmap graphics into vector graphics (choose Path->Trace Bitmap) but the results of tracing bitmaps into vectors are rarely very good, the process only works well for very simple images with few colors and not much details.

If you want scalable graphics, the  you have to start by making your graphics in scalable format (like SVG), and then creating the bitmap images from that.

---

### Post by Perfect Storm on 2011-05-19
> **mcduck said:**
> 
If you want scalable graphics, the  you have to start by making your graphics in scalable format (like SVG), and then creating the bitmap images from that.

+1

It may be a bit difficult to learn how to use a vector program, but the reward is immense when learned.

This is 96x96 pix .svg file. See How I can scale it (~300%):
[img]http://eosvision.files.wordpress.com/2011/05/faenza-postler1.png[/img]

---

### Post by jtarin on 2011-05-19
> **Artificial Intelligence said:**
> +1

It may be a bit difficult to learn how to use a vector program, but the reward is immense when learned.

This is 96x96 pix .svg file. See How I can scale it (~300%):
Yea ,but what about the cost of a stamp for that thing.

---

### Post by DGINSD on 2011-05-19
> **jtarin said:**
> Yes,but they would suck.....resolution.

What if you started with a larger png's say 250 or so? I mean my computer is rather old and I could never see a need for an icon even up to that size.

Let me briefly explain what I've done theres parts of a few icon packages I like so I've "bits and pieces'" them into one package but the different packages have the icons set up in different way some with large .svg's some not so much.

So really the icon package I'm putting together is for personal use just to fit my own personal taste and it will likely never go on anyones computer but mine

How could one find the source of specific icons ones larger than the ones in the downloaded packages?

---

### Post by DGINSD on 2011-05-19
> **Artificial Intelligence said:**
> +1

It may be a bit difficult to learn how to use a vector program, but the reward is immense when learned.

This is 96x96 pix .svg file. See How I can scale it (~300%):
[img]http://eosvision.files.wordpress.com/2011/05/faenza-postler1.png[/img]

So it would appear I need to learn to use inkscape any good links to get started with it? Cause that program looks totally foreign to me.

---

### Post by mcduck on 2011-05-19
> **DGINSD said:**
> What if you started with a larger png's say 250 or so? I mean my computer is rather old and I could never see a need for an icon even up to that size.

Let me briefly explain what I've done theres parts of a few icon packages I like so I've "bits and pieces'" them into one package but the different packages have the icons set up in different way some with large .svg's some not so much.

So really the icon package I'm putting together is for personal use just to fit my own personal taste and it will likely never go on anyones computer but mine

How could one find the source of specific icons ones larger than the ones in the downloaded packages?

Making a large icons is not the same as making a scalable icon. If you want 256x256 sized icons, you can already do that, exactly the same way as with other icons sizes. Programs will then pick the appropriate sized image and use that.

Taking a fixed-size image and saying it's scalable will not make it scalable. :)

---

### Post by mcduck on 2011-05-19
> **DGINSD said:**
> So it would appear I need to learn to use inkscape any good links to get started with it? Cause that program looks totally foreign to me.

You could start with their own tutorials blog: [http://inkscapetutorials.wordpress.com/suggest-a-tutorial/tutorial-list/]("http://inkscapetutorials.wordpress.com/suggest-a-tutorial/tutorial-list/")

---

### Post by DGINSD on 2011-05-19
So just out of curiosity and likely my next project where are the window boardersand controls stored?

---

### Post by jtarin on 2011-05-19
> **DGINSD said:**
> So just out of curiosity and likely my next project where are the window boardersand controls stored?
That's another topic for another forum.....mark this one solved.

---

