---
title: "Turn a 1page Gif into a 4 page (4x bigger) print-out"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by hanzj on 2009-05-27
Hello,
Attached is a gif file that is about 1 page big. It is a special 3-player chessboard. We were thinking of printing it out, but before we do, we would like to make it bigger. Can anyone help us make this 4 times bigger.... to make it 4 pages big (2pages rows; 2 pages columns). If it is converted to PDF, that will be fine and may make printing easier.


Thank you.

---

### Post by wsonar on 2009-05-27
the concept sounds pretty interesting a 3 player chess board

---

### Post by NyteWyyrm on 2009-05-27
Have you tried GIMP?  Using the 'scale' function.  Might have to tweak the resolution, however.

3 player chess does sound interesting.  Do you have rules posted somewhere?

---

### Post by mbsullivan on 2009-05-27
How did you generate the image? It would be best if you could natively create it in a vectorized image format, such as SVG, PS, EPS, or PDF (not with embedded raster image, though).

Failing that, it should be possible to resize it with the GIMP or the ImageMagick tools. Let me know if you need help.

Mike

---

### Post by hanzj on 2009-05-28
Mike,
I did not generate the image. It was from the web. 

I can use an image-editing program such as Gimp to increase the size of the image. But my concern is making it EASILY PRINTABLE.

See [http://www.chessvariants.com/crafts.dir/hexboard/#four](http://www.chessvariants.com/crafts.dir/hexboard/#four) for instance. With that link, you can see how each quarter of a chess board is nicely placed in 4 pages.

Can someone help me do this? If they can be in PDF format, this will help, so that I don't have to mess around with formatting/borders/margins/etc.

(Mike, yes, I need help. 8-) )
Thanks.


P.S. Rules can be found here: [http://www.three4chess.com/rules.html (@]("http://www.three4chess.com/rules.html")[NyteWyyrm)]("http://ubuntuforums.org/member.php?u=641968")

---

### Post by cariboo on 2009-05-28
Have a look at [rasterbator]("http://homokaasu.org/rasterbator/"), it may do what you are looking for. I've used this a couple of times to print a larger version of a picture.

---

### Post by hanzj on 2009-05-28
> **cariboo907 said:**
> Have a look at [rasterbator]("http://homokaasu.org/rasterbator/"), it may do what you are looking for. I've used this a couple of times to print a larger version of a picture.
I checked it out, but the resulting 2x2 (4 pg) pdf looks awful. All the lines are turn into circles.  It's not meant for this purpose.

---

### Post by mbsullivan on 2009-05-28
> 
I can use an image-editing program such as Gimp to increase the size of the image. But my concern is making it EASILY PRINTABLE.

See [http://www.chessvariants.com/crafts.dir/hexboard/#four](http://www.chessvariants.com/crafts.dir/hexboard/#four) for instance. With that link, you can see how each quarter of a chess board is nicely placed in 4 pages.

Can someone help me do this? If they can be in PDF format, this will help, so that I don't have to mess around with formatting/borders/margins/etc.


Oh, I see. I misunderstood the question.

See the attached PDFs. They are made for a true rail-to-rail printer (no printing margins), and are formatted for 4 landscape-oriented US letter size (8.5x11") papers.

**EDIT: The PDFs are too large to attach here. I'm attaching them as a (BZ2) tarball. To extract it, use the following command.

```
tar -xjf split_image.tar.bz2
```



Hope this helps,
Mike

---

### Post by hanzj on 2009-05-28
Mike,
Thanks so much for your help with the splitting and zooming. I'll give printing a try later.

---

### Post by mbsullivan on 2009-05-29
> Mike,
Thanks so much for your help with the splitting and zooming. I'll give printing a try later. 

Sure, let me know how it goes.

If you have too big of issues with printer margins (most printers can't print to the edge of each page), then I could try and generate PDFs which have a smaller image with a bounding box. In this case, you would presumably cut the bounding box off with a pair of scissors. 

I would need to know a reasonable estimate of how much space to leave on each edge of the page, though.

Mike

---

### Post by hanzj on 2009-05-29
Mike,
Yes, having some printer margin would be great.

What would be great too would be some overlap of the graphic between the pages. (Does this make sense?)

I looked at a previous printout of some other thing. On the longer sides of the pages (the 11.5 inch side of a letter sized paper), we were able to print with a 1-**cm** margin. On the 8 shorter side of the page (8-inch edges), we had about 3 [B]cm.


[/B]Oh, we are also looking at a 6-player chess board!!! 8-) [http://www.chessvariants.com/hexagonal.dir/chexs6.gif](http://www.chessvariants.com/hexagonal.dir/chexs6.gif). Maybe a 3 pages wide by 2 pages tall is what we need. 

Also, if you can teach me how to do this, that would be great. 

I noticed that the zip file you were kind enough to create had a bit of jagged edges for the lines. If we vectorize the image, would that sharpen things up? I'm guessing you used gimp's built-in scale-image function.

---

### Post by mbsullivan on 2009-05-29
> What would be great too would be some overlap of the graphic between the pages. (Does this make sense?)

That should be possible.

> I noticed that the zip file you were kind enough to create had a bit of jagged edges for the lines. If we vectorize the image, would that sharpen things up? 

Not really, unless you could generate the image in a vectorized format. No vectorizer I know of will be able to get rid of the (already jagged) edges going from the raster image.

> I'm guessing you used gimp's built-in scale-image function.

Actually, in this case no scaling was needed... the image was large enough already. The jagged edges present in the PDFs were already there in the original image.

If I had resized the image, though, I'd use either Lanzcos3 (for making the image bigger) or bilinear (for making the image smaller).

Mike

---

### Post by mbsullivan on 2009-05-29
> Also, if you can teach me how to do this, that would be great. 

Okay, the process I used is fairly simple, and general enough to handle many special cases.

(1) Load the image into the GIMP

```
File -> Load
```

(2) Resize the canvas to fit the dimensions appropriate for your page sizes. 

```
Image -> Canvas Size
```

For instance, for the 4 page case, I resized the image to 22 x 17 in. Typically, all measurements should be made in inches. It makes things easier.

(3) Center the image in your new, larger canvas

```
Hit the "Center" Button while still in the Image -> Canvas Size dialog
```

(4) Create the four quadrants one at a time, by cropping the canvas, and saving the resulting image as a PNG

```
Image -> Canvas Size
- Set "Width/Height" to 50%
- Set Offset appropriately to create upper left, upper right, etc.
```

For each quadrant, save it as a unique PNG, then "undo" and repeat the process again.

(5) Convert each PNG to PDF using the ImageMagick tools.

```
sudo aptitude install imagemagick
convert [name].png [name].pdf
```

(6) Profit.

Adding extras, like a bounding box, appropriate margins, and overlap, just requires some more forethought. Adding margins/overlap changes (1) the initial canvas size and (2) the edges of each quadrant. For adding margins, a second canvas size change would be required to add a margin to the bleeding edge.

This process, while manually intensive, was the only thing flexible enough that I could think of.

Hope this helps!
Mike

---

### Post by mbsullivan on 2009-05-29
I'd be willing to take a crack at creating an image with appropriate margins, a bounding box, and some constant overlap.

However, I only have time for one image. Which would you like me to look at?

Mike

PS: Actually, in this case is a bounding box really needed? You're going to cut the thing out along its edges, right?

---

### Post by hanzj on 2009-05-29
No, we printed a different chess board and we did not cut along the edges. We just taped up the 4 pages together.

---

### Post by mbsullivan on 2009-05-30
> No, we printed a different chess board and we did not cut along the edges. We just taped up the 4 pages together. 

So which (if any) of the pictures would you like me to try and divide into four pieces?

If you'd like to try yourself, I'd be happy to answer any questions that might arise.

Mike

---

### Post by hanzj on 2009-06-18
Mike, I made a 6-player hex chess board, which is attached. I would like to make a CRISP/NEAT print of it in, um, maybe 3 x 4 letter-sized pages (12 pages total). Hmmm, maybe that's too big. 
Maybe if they can fit on 9 pages, that would be better.

Around 9-12 pages. I'm not too particular.
Thanks, Miike!
Thanks for your patience.

If you help with this, many people will have the chance to print this out, too.

You're a :KS helper!!!

I created the svg in inkscape

---

### Post by hanzj on 2009-06-18
Here is the Inkscape SVG saved as PDF (saved as PDF wihin Inkscape)

---

### Post by hanzj on 2009-06-18
Here is the Inkscape SVG exported as **PNG** file.

---

### Post by hanzj on 2009-06-18
I found out about [http://www.blockposters.com](http://www.blockposters.com), a free and easy-to-use service.

The resulting PDF is here: [http://www.scribd.com/doc/16558518/Multipage-for-printing-6player-Chess-Hex-Board](http://www.scribd.com/doc/16558518/Multipage-for-printing-6player-Chess-Hex-Board)

---

