---
title: "Baffled about tiffs and why some software (gimp) won't view while other sw does!"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by cogvos on 2010-09-20
Dear all,

I have been playing around with UFraw which exports the results as tiff files. I guess it can do others but I have been using tiffs. 

Problem I have is that the gimp can't import these - it comes up with a load of errors saying that 

invalid TIFF directory; tags are not sorted in ascending order
TIFF directory is missing required "ImageLength" field
invalid TIFF directory; tags are not sorted in ascending order

before giving up. Now I thought this was a problem with the file (ok it sounds like one!) but both F-Spot and gThumb can open the file as can inkscape! (OK the last is a vector programme) so why cant the gimp.

I'm running gimp 2.6.7 but cannot figure out how to get the latest (2.6.10) via synaptec. I'm using ubuntu 9.10 

Any ideas?

---

### Post by mastablasta on 2010-09-20
have you tried just opening a tiff picture not importing it?

---

### Post by cogvos on 2010-09-20
> **mastablasta said:**
> have you tried just opening a tiff picture not importing it?

errmmm.. not sure. I have a tiff I right click on it - I select open with and then gimp image editor. So I presume I am opening the file rather than importing? Aren't they the same in anycase? Sorry Confused...

---

### Post by mastablasta on 2010-09-22
i am asking because i tried to open it from within Gimp and it opens tiff files just fine.

---

### Post by coffeecat on 2010-09-22
> **cogvos said:**
> Dear all,

I have been playing around with UFraw which exports the results as tiff files. I guess it can do others but I have been using tiffs. 

Are you using ufraw, or gimp-ufraw, both of which are in the repositories? If ufraw, try gimp-ufraw which is designed as a gimp plugin and *ought* to be able to produce tiffs that the gimp understands. Or at least it did when I tried it some time ago.

> **cogvos said:**
> I'm running gimp 2.6.7 but cannot figure out how to get the latest (2.6.10) via synaptec. I'm using ubuntu 9.10 

You won't. In one version of Ubuntu you will get bugfixes and security patches in updates but not newer versions. You could try enabling the backports directory and seeing which gimp version it offers you. Read what this link has to say about backports before you enable it:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

---

### Post by coffeecat on 2010-09-22
> **mastablasta said:**
> i am asking because i tried to open it from within Gimp and it opens tiff files just fine.

I know very little about tiff files but I do know that the GIMP sometimes just opens a TIFF, and sometimes it says it needs to import it and does some sort of conversion when it does so. This happens when I want to open TIFFs from my 35mm scanner, but once I've saved a TIFF from GIMP or something like gThumb, the GIMP opens it without a murmur.

---

### Post by mcduck on 2010-09-22
.tiff is actually rather complicated image/container format (and non-standardized to make things even worse) , as there are several variants of it, all using the same .tiff file name extension while not necessarily being supported everywhere. For example you image could be BigTiff (a 64-bit version of TIFF image).

Make sure you save your images as Baseline Tiff if you want to be sure they work in every program.

Apart from that, it's pretty hard to say what might be the problem without having the actual file itself at hand.

(I just have to point out that it's a common joke to say that TIFF comes from "Thousands of Incompatible File Formats" ;))

---

### Post by mastablasta on 2010-09-22
> **mcduck said:**
> .tiff is actually rather complicated image/container format (and non-standardized to make things even worse))
 
 
oh, i didn't know that. i just always thought it's raw uncompressed picture data. never occured to me that kind of data is not standardised since most scanners (especially the first ones) output default to tiff.

---

### Post by garvinrick4 on 2010-09-22
It is a common format tiff in the printing and desktop publishing. It can be seperated into 4 colors on scan (cymk) and then rastrorized and printed to film in a document in what is called a image setter. These color seperations can then burn a plate to be placed in a sheet fed or web printer. Then off to bindery. To get a good scan for a tiff must be done on a drum scanner. A full page tiff 8 1/2 by 11 is about 80 meg. Drum scanner can take a 35 millimeter chrome and scan at 600 or 900 and even 1200% for dual page and look fantastic. Flat bed scanner is fine for half tones some like to fool around with color with a photoshop plug-in. Flatbed scanner cheap as hell, Good drum scanner $80,000. If you want to put out magizine quality work only one way to scan. Mac has kind of been the machine best for desktop publishing they just work in that industry. Quark express, Photoshop, illustrater and so on were the standards and most likely still are for software. Nothing free and open source there. Any which way if you ask me TIFF's are the only true format for a good scan, be it reflective, chrome or negative scan. If you like to scan on your flatbed fool around with tiffs and changing the percentages of the color seperations cyan, yellow, magenta and black and print and see how nice you can make a bad photograph look using photoshop. Make your girl friend look like a jewel.

---

### Post by garvinrick4 on 2010-09-22
> **mastablasta said:**
> oh, i didn't know that. i just always thought it's raw uncompressed picture data. never occured to me that kind of data is not standardised since most scanners (especially the first ones) output default to tiff. That is correct no such thing as a 45k jpeg then. Tiffs are real thing, rest were made to be compressed to be easier to store and move around. Even black and whites (half tones)
were done in tiff in 256 grey scale.

---

### Post by mcduck on 2010-09-22
> **mastablasta said:**
> oh, i didn't know that. i just always thought it's raw uncompressed picture data. never occured to me that kind of data is not standardised since most scanners (especially the first ones) output default to tiff.

That would be the Baseline Tiff.

TIFF format allows anybody to add new stuff to it. So basically anybody can make their own "version" of TIFF file adding pretty much any data into it, vectors, layers, multiple pages, different compression types etc..

While in theory even such files, at least the basic image data, should be possible to open in any program that supports the Baseline Tiff this isn't usually the case. More likely the programs will simply get overwhelmed by all the stuff they can't recognize and fail to open the file correctly.

So in theory it is a great format, in reality it only works reliably if you stick to the most basic version of TIFF. For anything else you always need to check compatibility. Which in my opinion is good enough reason to use other image formats instead. 

(I mostly use PNG these days, at least for anything that doesn't need to include a color profile, or .exr if I need more dynamic range than what PNG can handle. Of course there are situations where the extended features of TIFF format are needed, but in that case you really have no option anyway. :D)

---

