---
title: "turn these ready-to-print boxes in PDF to 4x6 jpgs"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by hanzj on 2009-11-11
Hello,
Please see attached files. What is the quickest way to turn the PDFs with printable flash cards (that need post-printing cutting) into individual 4x6 JPEGs(, which I shall upload to an online photo center)? Each flash card should be one 4x6 JPG.

UPDATE: It looks like 2 Flashcards would fit nicely (by nicely, I mean that the words and photograph are easy to read and see) into 1 4x6 JPEG. So I may just end up with a 4x6 JPEG having 2 flashcards (side by side).


Thank you.

---

### Post by ajgreeny on 2009-11-11
If I understand you right, you want to convert the PDFs that contain 6 rectangle pictures into 6 jpgs, and the single table into another.  If so I think you can use the command convert eg ```
convert 1-50.pdf 1-50.jpg
```which in that case will produce 9 different files 1-50.jpg to 1-50.jpg.8, ie each file number is increased by 1.  You can then use gimp or another graphics editing app to get each rectangular pic from each of those into a separate file if you wish.

There may even be better ways to do this which are less clunky and allow for direct manipulation of the pdf file, but if so, I have never used them so can not help you on that.  Search in the repos using synaptic for pdf editing and see what comes up.

---

### Post by hanzj on 2009-11-11
ajgreeny,
thanks for your post. I removed the "single table" file you were referring to because I accidentally attached it.

---

### Post by hanzj on 2009-11-11
I used Gimp and manually (that is, one by one)  produced these JPEGs from the 1-50.pdf

---

### Post by kaibob on 2009-11-11
You can use the Imagemagick convert utility both to convert the PDF files to JPG format and to create the individual flash cards with the crop option. The following (which doesn't crop correctly) is an example:

```
convert input.pdf -crop '100x200+10+20' output.jpg
```

The trouble with this is the time it takes to figure out the crop coordinates and size. Unless this is something you are going to be doing on an ongoing basis, I think doing it manually with gimp is preferable.

Another alternative is to convert the PDF files to JPG format using Imagemagick and then to use the Gthumb utility to do the actual cropping. I suggest Gthumb because it is very easy to use when cropping an image.

---

### Post by ajgreeny on 2009-11-12
Good point kaibob, I didn't think about gthumb, which I have used often to crop images as it is so much faster than gimp if all you need is a crop tool.

Mind you, I did say "or another graphics editing app" so I was at least correct in that overall comment and don't feel too bad about suggesting gimp, which I also use a great deal.

---

