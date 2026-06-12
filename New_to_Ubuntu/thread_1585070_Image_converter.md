---
title: "Image converter"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by BobJam on 2010-09-30
I'm looking for an image format converter, but  before you point to the standard converters, like .png to .jpg or .gif  to .ico, let me point out that the format I want to convert from is  machine language.

 I have an old email archived, and it has an image shown in the form  "iVBORw0KGgoAAAANSUhEUgAAAZQAAAEqCAIAAAC9ZzHyAAAACXBIWXMAAA7EAAAOxAGVKw4bAAAA  . . ." (that's what I'm calling "machine language", though that may not  be correct . . . but you get the point).

 I know that particular image is a color photo.  What I would like to  do is take that "code" and convert it back to an image format, like .jpg  or .png, so that I can view it.

 I have a vague memory that I ran across something like that one time,  but if I do a Google search on "image converter" all I get is the  standard stuff that converts those .jpg to .png and .gif to .ico and  such.  That's not what I'm looking for.

 And if I do a Google search on "binary images" all I get is stuff  about black and white and pixels for two colors and such.  So that's not  it either.

 Does the animal I'm looking for exist?

---

### Post by 3rdalbum on 2010-09-30
It may be uuencoded, or binhexed. Try some software that decodes those formats to reveal the original image file.

---

### Post by jtarin on 2010-09-30
What email program? Maybe Yenc? [Multi-decoder in perl.]("http://www.filetransit.com/download.php?id=98651")

---

### Post by MartyBuntu on 2010-09-30
Are you talking about something like this:

[http://en.wikipedia.org/wiki/ASCII_art](http://en.wikipedia.org/wiki/ASCII_art)

---

### Post by BobJam on 2010-09-30
@ MartyBuntu,

No, it's not ASCII Art.

@ Everyone,

It was base64 code (had nothing to do with machine language . . . so I may have mislead there) . . . I found that encoding explanation in the header directly above the lines.

So instead of "Image converter" I should have titled this "Decoder". 

I found some on line base64 decoders (just Google for "base64 on line decoders"), and a few I can download to my local machine.  'Sperimenting right now.

 Actually, a base64 decoder is built right into Ubuntu, so it was  under my nose the whole time.  That one is not a GUI however, so I have  to play with the command line a little.  To see the manual, just type this into the terminal:
```
man base64
``` Just looking at them all and seeing what is the easiest to use.


 Interesting . . . I went from famine to feast.

---

### Post by jtarin on 2010-10-01
[An online one]("http://www.opinionatedgeek.com/dotnet/tools/base64decode/")

---

