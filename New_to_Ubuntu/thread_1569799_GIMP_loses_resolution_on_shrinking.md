---
title: "GIMP loses resolution on shrinking"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-09-07
A charity has a large logo. When included into an OpenOffice document, it's too large, so it's easy enough to use OO's ability to shrink the logo.

However, it makes the document's file size large (the logo alone is over 400Kb).

I decided to use GIMP to reduce the logo to the required size, so that it takes less physical space; in OO, we can simply include the image without shrinking.

However, to my surprise, shrinking the logo in GIMP (using Image > Scale Image) loses resolution.

Specifically, the shrunk image has a grainy (pixelated?) appearance.

More information: The original logo is 1634x1653 pixels, at 300dpi (giving a size of nearly 5.4"x5.5"). In GIMP, I changed the resolution to 600dpi and shrunk to 1"x1" (300x303 pixels). I saved it as JPEG at 93% compression (the same as the original logo).

For the Interpolation, I've tried all four methods.

Any idea how I can shrink without getting a grainy appearance?

---

### Post by jtarin on 2010-09-07
can you post the grainy one one? Why not .png?

---

### Post by Paddy Landau on 2010-09-07
> **jtarin said:**
> can you post the grainy one one? Why not .png?
I tried PNG but didn't notice a difference.

I note I made a mistake with the pixels; it's not 300x303, it's 600x607. #-o

I've attached three versions.

[LIST]
[*]A very old one that someone else supplied to me, in greyscale (the quality is fine).
[*]My shrunk version, in colour, PNG.
[*]My shrunk version, in colour, JPG.
[/LIST]

If you insert them side-by-side into an OO text document, you'll see the difference immediately between the old version and my versions.

I'm starting to think that I need to use some sort of smoothing filter.

---

### Post by jtarin on 2010-09-07
Try this. Open your image in its original size in the Gimp. Now open another "new" and it should be the same size.Adjust for your finished resolution and background.Now copy the original into the "new" one. Save as .xcf. Now resize as you want and then save again as an .xcf.gz .Now save as a .jpg and leave all defaults but check progressive in the .jpeg dialogue and save. Now go to the menu and choose Image>Image Properties. Improvment?

---

### Post by mastablasta on 2010-09-07
i think compression could destroy it.
 
also i think OO could be at fault here. I am at work and inserting one fo the two in MS Word 2007 everything looks ok and not grainy at all. :-P
 
What happens if someone else reduces it for you and then you insert it?

---

### Post by jtarin on 2010-09-07
I was able to convert your .png to .jpg with no loss in quality and drastic reduction in file size by progressively saving first as .xcf, .xcf.gz, then finally as .jpeg (progressive)
Try to do all your work in the .xcf format when you have resizing and resolution concerns.Then save in your chosen format. The .xcf.gz format can compress the image without affecting any noticeable quality.

---

### Post by themusicalduck on 2010-09-07
If the original picture is 1634x1653 and you're scaling it down to 303x303, then wouldn't the picture be squashed? You are changing the aspect ratio of the image as well as the size. That attachment you added looks like there is aliasing, rather than pixelation (Although it won't let me look at it full size for some reason, but it looks it from the thumbnail).

What you need to do is change the image canvas size so that it is square (say 1653x1653). You can centre the logo in the dialog that comes up. Then use Layer to Image Size under the Layers menu. Then scale it down to 303x303.

---

### Post by jtarin on 2010-09-07
> XCF is a file format which is special because it is GIMP's native file format: that is, it was designed specifically to store all of the data that goes to make up a GIMP image. Because of this, XCF files may be quite complicated, and there are few programs other than GIMP that can read them.

When an image is stored as an XCF file, the file encodes nearly everything there is to know about the image: the pixel data for each of the layers, the current selection, additional channels if there are any, paths if there are any, and guides. The most important thing that is not saved in an XCF file is the undo history.

The pixel data in an XCF file is represented in a lossless compressed form: the image byte blocks are compressed using the lossless RLE algorithm. This means that no matter how many times you load and save an image using this format, not a single pixel or other image data is lost or modified because of this format. XCF files can become very large, however GIMP allows you to compress the files themselves, using either the gzip or bzip2 compression methods, both of which are fast, efficient, and freely available. Compressing an XCF file will often shrink it by a factor of 10 or more.

The jpeg format uses a compression which tries to get rid of parts of the image most people won't notice anyway. As you compress the image smaller and smaller, the changes gradually get more noticeable.Thats why you work on the file as .xcf then save as .jpeg so you don't lose but the smallest of data which is not noticeable to the eye.

---

### Post by Paddy Landau on 2010-09-07
> **jtarin said:**
> Try this...
Sorry, exactly the same. Even if I set the Subsampling as "best quality" and the Quality as 99%.

Comment: According to the manual (and my tests), .xcf.gz is just .xcf with lossless compression.

> **mastablasta said:**
> What happens if someone else reduces it for you and then you insert it?
Well, I would be willing to see if someone else can do it, but I need to know how to do this. This is not the only organisation I help, so I'd like to get it right.

I'm going to experiment with the filters, but I am puzzled by this grainy effect.

---

### Post by Paddy Landau on 2010-09-07
> **themusicalduck said:**
> If the original picture is 1634x1653 and you're scaling it down to 303x303...
No, it's to 300x303. I retain the aspect.

---

### Post by anaconda on 2010-09-07
Thanks jtarin..

I used your solution for scaling a different image.

Thanks.

---

### Post by jtarin on 2010-09-07
I've taken your .png as you have it and reduced it from 13.2kb down to .jpeg. 5.8kb at 85% and progressive as the only thing changed in the dialog  with no noticeable difference between the two.

---

### Post by jtarin on 2010-09-07
> **anaconda said:**
> Thanks jtarin..

I used your solution for scaling a different image.

Thanks.Your welcome...I'm glad it worked for you.;)

---

### Post by jtarin on 2010-09-07
Your original .png as a .jpg

---

### Post by Paddy Landau on 2010-09-07
> **jtarin said:**
> I've taken your .png as you have it...
I could post the full-size original, which I'm working with and is 400Kb.

I've been experimenting...

Here's an interesting thing. If I scale the image down but *reduce* the resolution to 150dpi, then it comes out a lot smoother!

That gave me the clue.

I used Gaussian Blur, and now it comes out great! It prints well, too.

Thanks for all your help. I'll mark this as solved.

---

### Post by jtarin on 2010-09-07
Gaussian Blur???? If thats what you want.:p

---

### Post by Paddy Landau on 2010-09-07
> **jtarin said:**
> Gaussian Blur???? If thats what you want.:p
Well, it works, that's all I can say! I don't pretend to understand why.

And now I've found something else.

If I save as PDF, then it smooths it out pretty well, even without the blur. Gaussian Blur with 3.0 seems to work best in this case.

---

### Post by themusicalduck on 2010-09-07
> **Paddy Landau said:**
> No, it's to 300x303. I retain the aspect.

Oh, whoops. Must remember to double check the original posting before making long-winded suggestions next time.

---

### Post by JKyleOKC on 2010-09-07
A number of years ago, while still working only in Windows (and these were the days when Win3.1 was state of the art), I picked up a tip from another developer: when reducing a large image by a large amount, blur the image first. The reduction will restore apparent sharpness. I tested it with a 20-time reduction of a photo to create a 16x16 icon, and sure enough it worked. Looks as if you have independently rediscovered this phenomenon.

I think what happens is this: the blurring spreads pixel values out over a larger area and removes all high-contrast edges. The reduction then averages pixel values over that larger area, thus restoring something fairly close to the original pixel's value, and that in turn restores the edges, making the image appear to retain its sharpness but with tiny details lost.

It's a good trick to know!

---

### Post by Paddy Landau on 2010-09-07
> **themusicalduck said:**
> Oh, whoops. Must remember to double check the original posting ...
We've all made that mistake ;)

> **JKyleOKC said:**
> ... when reducing a large image by a large amount, blur the image first.
Brilliant, that explains it, thank you. I was blurring the image *after* reducing the size, but I'll remember this for next time.

---

