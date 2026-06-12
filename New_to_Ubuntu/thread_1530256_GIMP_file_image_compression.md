---
title: "GIMP file image compression"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by kapi on 2010-07-13
I've spent quite a while now and had numerous discussions on this forum relating to GIMP and its lack of ability to reduce certain images to a decent file size.

Problem solved: For most of the time GIMP rocks but occasionally I've come across images that simply wont reduce far enough, especially in relation to images for the web.eg I have an image from a photo shoot that's 4000 x 2000 in size and 127mb in a tiff format. Fine but when I reduced the image to 500px wide and then saved for the web the file size was nearly 560k. Great but still not good for the web. So I started experimenting with formats.

This is what I've found: first after you've opened your tiff image in GIMP then save as a 16bit bmp. Then resize the image to what ever you need and then use the save for web function. The image is chrystal clear and it's now only 27k, which means it will load quickly on the web.

I should note that most of the time I just reduce my 45mb (approx) images to the desired size and then use save for web and it normally works great, reducing the file size to under 25k.

I hope this helps a few people, it took me several hours. Be nice to hear if it does help.

GIMP just keeps on rockin! 
(even if they haven't included it in the latest release)

---

### Post by avocadorange on 2011-02-24
I installed GIMP last night because I'm struggling with the exact same problem you're describing. However I have .JPG images...and *unfortunately I couldn't figure out how to save an image as 16bit bmp in GIMP. *Do you have any specific suggestions?

---

### Post by Matt__ on 2011-02-24
theres a plugin for gimp called [ "save for web" ](http://registry.gimp.org/node/33) with 

"Options to reduce file size of an image include setting compression quality, number or colors, resizing, cropping, Exif information removal, etc."

you should take a look at [http://registry.gimp.org/](http://registry.gimp.org/) 
there are so many useful and fun plugins :)

---

### Post by avocadorange on 2011-02-25
> **Matt__ said:**
> theres a plugin for gimp called [ "save for web" ](http://registry.gimp.org/node/33) with 

"Options to reduce file size of an image include setting compression quality, number or colors, resizing, cropping, Exif information removal, etc."

you should take a look at [http://registry.gimp.org/](http://registry.gimp.org/) 
there are so many useful and fun plugins :)

Thanks, that does look like a useful plug-in, but I stumbled onto how to do what I needed. File>Save As>{name}.bmp > in the pop-up dialogue choose advanced options>16 bit.

The *_only slight confusion_* is whether to choose "[COLOR="Purple"]RS G6 B5[/COLOR]" or "[COLOR="Teal"]X1 R5 G5 B5[/COLOR]" --any suggestions?

---

### Post by dargaud on 2011-02-25
It's none of Gimp's fault: you should read about the difference between TIF, PNG and JPG, in particular the lossless vs lossy argument. Additionally JPG doesn't support 16 bit images.

---

