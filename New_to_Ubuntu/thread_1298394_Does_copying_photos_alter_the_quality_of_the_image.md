---
title: "Does copying photos alter the quality of the image?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by emz414 on 2009-10-22
Hi all, my son disagrees with me on this (another Ubuntu fan) so he told me to ask all the smart people over here. So does it?

---

### Post by amauk on 2009-10-22
copies of digital data are absolutely identical, with no degradation

---

### Post by earthpigg on 2009-10-22
> **amauk said:**
> copies of digital data are absolutely identical, with no degradation

correct.

now, if you copy them using some "photo management" program, or by uploading them to photobucket and re-downloading them, then this may not be the case....

but a drag and drop or copy and paste in a simple file manager such as what you get from the "places" menu in ubuntu? identical, with no degradation.

---

### Post by Psyphre on 2009-10-22
No degradation at all.

---

### Post by Bucky Ball on 2009-10-22
A matter of compression. If you shrink a photo you basically 'squeeze the air out' and those zeros and ones cannot be replaced if you then blow the photo up to full size again. Shrinking and then resizing to a bigger file will DEFINITELY degrade quality.

---

### Post by jrrader on 2009-10-22
A file, no matter what type of file, is a list of 1s and 0s.  Copying, sending over a network, or burning onto a disk will leave you with the same 1s and 0s unless you have an error of some sort.   Jpegs are lossy when compressed, not copied or viewed.

---

### Post by undecim on 2009-10-22
In most cases, the image will be an exact copy.

The only times you have to worry about quality degradation are when you change file formats (for example, convert a png to jpeg) deal with non-digital manipulation of the image (for example, if you print an image, then scan it back, it won't look as good), or when you use another application to manage the image (specifically, programs that upload images to the webwill somethimes throw out information from the file to make it smaller, and easier on the server you are uploading it to)

But, if you just have a .jpeg file (or any other type of file for that matter) and drag-drop that file onto a thumb drive, put it in an email as an attachement, or move it to another folder on your hard drive, every single 1 and 0 in the file will be exactly the same as the 1 or 0 it was copied from, no matter how many times you move it around.

---

### Post by OrangeVixen on 2009-10-23
One thing to watch out for is that, for example, since most JPEG (.jpg) image codecs use "lossy" compression, if you open a .jpg image in an image viewer or editor program and then use "Save As" to save it as a .jpg to a new location or new file name, then you are compressing again and you will loose some data. If you Copy an image file using a File Browser or using "cp" from a terminal/command line you won't loose any data.

Just beware of the "Save As".

There is jpegtran that is a special program that can rotate and crop JPEG images without any loss of data.

Non-lossy formats such as PNG (.png) will not loose any data if you "Save As" in an image viewer or editor program, unless you resize, crop, or edit them.

---

### Post by stinger30au on 2009-10-23
> **emz414 said:**
> Hi all, my son disagrees with me on this (another Ubuntu fan) so he told me to ask all the smart people over here. So does it?

just doing a stright copy from memory card to hdd there is no degredation
same as a copy from hdd to memeory card or what ever

end of story

---

### Post by timespliter on 2012-12-04
hey guys, I'm totally new to the forums here but have a very similar question 
some  .jpeg photos have some strange  pixelation in them and some don't. 
i have attached them to my post. Any idea why or any solution?

---

### Post by wildmanne39 on 2012-12-04
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

