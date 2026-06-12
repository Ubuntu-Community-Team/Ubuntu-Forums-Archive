---
title: "fonts"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by impatientboi on 2009-08-19
I have noticed that regardless of the font selected, they seem to be very similar. I have read in some magazines that fonts are kind of a weakness in linux. Does it offer support for the traditional windows fonts, times new roman, arial etc, or are these proprietary formats and thus not available on linux? I have noticed that although there is a wide selection of fonts there seems to be negligable differences between those with the same name, which i had expected, but even those which have different names seem to appear very, very similar to other fonts.

cheers
mark

---

### Post by zarthon on 2009-08-19
```
$sudo apt-get install msttcorefonts
```
This contains the Microsoft fonts that they provided to the public for free.
There are a huge number of open source fonts.
You can down load them and arrange the files similarly to other fonts in:
/usr/share/fonts/truetype/
There are also other optional font packages that are not automatically installed. Search for fonts in synaptic.
Finally you can install fontforge and make your own font !

---

### Post by raymondh on 2009-08-19
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Want to try mac fonts?

[http://ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html](http://ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html)

---

### Post by impatientboi on 2009-08-19
> **zarthon said:**
> ```
$sudo apt-get install msttcorefonts
```This contains the Microsoft fonts that they provided to the public for free.
There are a huge number of open source fonts.
You can down load them and arrange the files similarly to other fonts in:
/usr/share/fonts/truetype/
There are also other optional font packages that are not automatically installed. Search for fonts in synaptic.
Finally you can install fontforge and make your own font !

thanks very much. Am I correct in assuming i punch in that command into the terminal and they are automatically installed into the directory :
usr/share/fonts/truetype/?

---

### Post by 3rdalbum on 2009-08-19
Yes.

Fonts are not a weakness of Linux, FYI. Font rendering looks very different to Windows and it looks a little different different to the Mac OS, but there's nothing inferior about fonts or font rendering on Linux.

---

### Post by Compintuit on 2009-08-19
Well, if you select the right settings, font rendering is the same, I believe. Using the msttcorefonts and the font settings no smoothing, medium hinting, and an RGB subpixel order my fonts are rendered the same as in XP, atleast before SP2 turned on smothing.

---

### Post by warreno on 2009-08-19
> **impatientboi said:**
> I have read in some magazines that fonts are kind of a weakness in linux.

I think more in the sense that compared to other OSen (Mac, ahem), Linux's native font support isn't as geared to designers' needs. IOW, it isn't entirely as refined ("easy") as some might prefer.

Installing a new font in OSX basically means a download from someplace like [Dafont]("http://www.dafont.com/") and double-click to suck it into FontBook. I don't believe it's quite so simple under Lin, but by no means is it excruciating.

That said, Linux *does* have a font creator/editor package that includes support for OpenType, so this could easily be changing very soon.

---

### Post by zarthon on 2009-08-20
I was wrong about where to put your downloaded fonts. 
```
mkdir /usr/**local**/share/fonts/truetype
```
and put your downloads in there. 
I did and they were immediately avaliabe when i opened openoffice.org Writer for example.

The advantage of /usr/local is that you know extra files that could not be restored from Ubuntu packages are there so you can easily back them up and remember them when you upgrade or migrate your system without remembering each and every file.

Thank you because in the process I got two fonts that I really like:
[http://www.webpagepublicity.com/free-fonts/a/Acoustic%20Light.ttf](http://www.webpagepublicity.com/free-fonts/a/Acoustic%20Light.ttf)
[http://www.webpagepublicity.com/free-fonts/a/AdineKirnberg-S.ttf](http://www.webpagepublicity.com/free-fonts/a/AdineKirnberg-S.ttf)
The site claims they are free but I did not do any checking on that claim.

---

### Post by 3rdalbum on 2009-08-20
> **Compintuit said:**
> Well, if you select the right settings, font rendering is the same, I believe. Using the msttcorefonts and the font settings no smoothing, medium hinting, and an RGB subpixel order my fonts are rendered the same as in XP, atleast before SP2 turned on smothing.

I've never managed to get my fonts on Ubuntu looking as horrible as IE 7 on Windows XP :-)

---

### Post by CatKiller on 2009-08-20
> **impatientboi said:**
> Does it offer support for the traditional windows fonts, times new roman, arial etc, or are these proprietary formats and thus not available on linux?

As an aside, I really hate Times New Roman and Arial. Horrible.

In answer to your question, they are proprietary fonts. But, since getting text displayed in the same way over the Internet is a problem, Microsoft made some of the fonts that come with Windows available for re-distribution so that every web designer could be reasonably sure that any visitor to their web page would have a handful of fonts available regardless of browser or platform. Despite the fact that I find the fonts themselves really ugly, it was quite a good idea. Microsoft no longer distribute the fonts themselves, but since they were allowed to be redistributed you can get them from a bunch of other places. These are the fonts that are included in the *msttcorefonts* package.

---

