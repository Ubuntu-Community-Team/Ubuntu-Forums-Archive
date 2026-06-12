---
title: "Use convert for jpeg to tiff suitable for tesseract"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-01-07
I often need to use OCR (optical character recognition) to get new text onto the computer.

When I use *tesseract*, I get terrible results, unless I use GIMP to set the image to 1-bit monochrome (and save as TIFF).

(See "Preparing images for Tesseract" at the bottom of the [Community OCR]("https://help.ubuntu.com/community/OCR") page.)

As I often get these files, I'd like to automate the conversion, rather than have to fire up GIMP and manually do it every time.

I tried using *convert*, but the command gives an error when I try to convert it to monochrome:
```
$ convert newtext.jpg -flatten -monochrome newtext.tif
convert: BitsPerSample 1 not allowed for JPEG. `JPEGSetupEncode'.
```If I use *convert* without the *-monochrome* option, then tesseract puts out garbage.

Any ideas?

---

### Post by kaibob on 2009-01-07
I tried the jpg to tif conversion with the monochrome option and got the same result as you did. I was able to convert from jpg to png with the monochrome option and then to convert the png image to tif. I checked the resulting tif image and it was 1-bit and loaded fine in my image viewer. It's a bit of a kludge, but if nothing else works, you may want to give it a try.

---

### Post by Paddy Landau on 2009-01-07
kaibob, that works a treat. As you say, a bit of a kludge, but hey, it works.

Thanks.

---

