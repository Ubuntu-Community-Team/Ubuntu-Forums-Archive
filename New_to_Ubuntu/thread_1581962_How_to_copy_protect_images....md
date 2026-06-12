---
title: "How to copy protect images..."
date: 2010-09-25
forum: New to Ubuntu
---

### Post by akelsall on 2010-09-25
Is there a utility similar to Adobe's "digital watermark" that I can use to copy protect my images? Something that would allow "batch processing" would be preferable.

Thanks,

Andy

---

### Post by lkjoel on 2010-09-25
Do you mean Ghosting Text?

---

### Post by owise1 on 2010-09-25
There is also a plugin for GIMP that allows you to embed text into the picture - G'MIC Fourier Watermark.  Makes for an invisible watermark that can then be viewed with the Fourier Filter

Dave

---

### Post by stmiller on 2010-09-25
There's also imagemagick (command line only). 

It can do batch processing, though options get a bit extensive. Be careful - actions are destructive with no undo.

Ex:

[http://www.cyberciti.biz/faq/how-do-i-create-watermark-with-imagemagicks-composite-command-in-linux/](http://www.cyberciti.biz/faq/how-do-i-create-watermark-with-imagemagicks-composite-command-in-linux/)

---

### Post by dtschump on 2010-09-26
> **owise1 said:**
> There is also a plugin for GIMP that allows you to embed text into the picture - G'MIC Fourier Watermark.  Makes for an invisible watermark that can then be viewed with the Fourier Filter

Dave

G'MIC is also available as a command line tool which can considered as a replacement to imagemagick :

[http://gmic.sourceforge.net](http://gmic.sourceforge.net)

Current stable version 1.4.2.0 proposes the '-watermark' option :

> gmic -h watermark
>    -watermark   _text,_size>0
        Add an textual watermark in the frequency domain of selected images.
 

(to be renamed 'watermark_fourier' in future releases).
So you can call it from a shell, as :

```
for i in *.jpg; do gmic $i -watermark \"foo fuu\",57 -o w_$i; done

```

---

### Post by HermanAB on 2010-09-26
The Imagemagick command line tool is called 'convert', so run 'man convert'.

---

### Post by akelsall on 2010-09-26
I'm actually looking for something that can be embedded in the image, but not visible to the eye (so that if someone were to use a photo I took, I could prove I was the original owner). Is there anything available like
that for Linux?  

Thanks,

Andy

---

### Post by acreech on 2010-09-26
> **akelsall said:**
> I'm actually looking for something that can be embedded in the image, but not visible to the eye (so that if someone were to use a photo I took, I could prove I was the original owner). Is there anything available like
that for Linux?  

Seems like I have seen a script for Gimp that does that. You might look through these script-fu's which can be added to your gimp. 

[HTML]http://registry.gimp.org/[/HTML]

acreech

---

### Post by kwacka on 2010-09-26
Checkout:

[http://en.kioskea.net/faq/4541-gimp-add-watermarks-on-your-digital-arts](http://en.kioskea.net/faq/4541-gimp-add-watermarks-on-your-digital-arts)

[http://www.ohbuntu.blogspot.com/2010/01/batch-watermark-script-ubuntu-zenity.html](http://www.ohbuntu.blogspot.com/2010/01/batch-watermark-script-ubuntu-zenity.html)

I've tried neither, but proably setting opacity levels to zero would give an invisible watermark.

The problem that I can see is that it you will need to recover an image that has been copied to demonstrate that it has been copied.

A visible watermark can be removed but will reduce the likelihood that it will be copied.

---

### Post by akelsall on 2010-09-26
Thanks to all who replied to my posting. I think I may have to go the watermark route. The GIMP and Zenity look promising.

Thanks again!

Andy

---

