---
title: "I have a folder of 925 .fits.gz"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by The Switch Blade on 2009-06-07
How can I extract them all simultaneously?

I assume there's some easy shell script

---

### Post by yoda2031 on 2009-06-07
> **The Switch Blade said:**
> How can I extract them all simultaneously?

I assume there's some easy shell script

The bash command-line wildcard "*" when used in an argument has somewhat strange behaviour (in my opinion) but is nevertheless what you want in this case.  Use the same command you'd use to extract a .fits.gz file normally (I'm not familiar with the .fits type) and use *.fits.gz to replace the name.  Make sure your CWD is where the files you want to extract are, then something like "gunzip *.fits.gz" will do it.

If the 925 you want to extract are not the only .fits.gz files in the directory, you will need to find some other way of selecting just the 925 you want.  More detail would be needed if you require assistance for this (ie, how are the files named?).

---

### Post by ellgor on 2009-06-07
Hi,

Install unrar and unrar-nonfree using synaptic(or your preffered app) when thats done simply click on the file and the option extract(here) will be available, hope this helps.

Regards, Ellgor.

---

### Post by The Switch Blade on 2009-06-07
**FITS** or **Flexible Image Transport System** is a digital [file format]("http://en.wikipedia.org/wiki/File_format") used to store, transmit, and manipulate scientific and other images. FITS is the most commonly used digital [file format]("http://en.wikipedia.org/wiki/File_format") in [astronomy]("http://en.wikipedia.org/wiki/Astronomy"). Unlike many image formats, FITS is designed specifically for scientific data and hence includes many provisions for describing [photometric]("http://en.wikipedia.org/wiki/Photometry") and spatial calibration information, together with image origin metadata.

It's 061102_*.fits.gz

so I assume I can do gunzip 061102_*.fits.gz

---

### Post by yoda2031 on 2009-06-07
> **The Switch Blade said:**
> 
It's 061102_*.fits.gz

so I assume I can do gunzip 061102_*.fits.gz

Thanks for the info on .fits.  Yes, gunzip 061102_*.fits.gz.

As I say, make sure you're in the right directory because the * wildcard takes its completion options from the current working directory (from what I've observed).  Probably goes without saying, but it's caused me a couple of minutes of confusion in the past.

---

