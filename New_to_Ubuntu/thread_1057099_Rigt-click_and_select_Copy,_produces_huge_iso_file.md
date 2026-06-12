---
title: "Rigt-click and select Copy, produces huge iso file"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by MockY on 2009-02-01
To copy a DVD, it really can't get any easier. Simply right-click on the DVD on your desktop and select copy.
The problem however is that the resulting file ends up being 7-8 GB in size. This is the case for older DVDs as well, making it impossible to burn the images onto a regular 4GB dvd. I am not going to burn them though, but only have a copy on my server so that I can watch it on my mediacenter (XBMC). The collection is not huge (around 90 DVDs) but it will take up almost a while TB drive, which seems like a waste.

Is there a setting in Nautilus I can use to shrink that size down a little, without causing the quality to noticeably decrease?

---

### Post by jerome1232 on 2009-02-01
That's because generally those dvd's are Dual Layer Dvd discs which can hold up to 8.5 GB's of data. There's a couple things you can do to reduce the size, k9copy can extract out only the main movie and generate an iso that's ready to burn to a single layer dvd, all without transcoding so there's no loss in quality.

Another method, this is the way I do it, is to use handbrake (or dvdrip) to transcode the movies to an avi file, perfect for keeping on the computer and playing on the computer, then use DeVeDe to generate a dvd burnable image from your avi file and burn it to dvd, this way you have two copies one on the comptuer one on disc.

DeVeDe and dvdrip are both in the repositories, handbrake does a considerably better job for me than dvdrip did.
```
sudo apt-get install dvdrip devede k9copy
```
[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by krzysz00 on 2009-02-01
Open a Terminal and run:
```
dd if=**/dev/cdrom** of=**mydvd.iso**
```

replace /dev/cdrom with the device for your cd (first drive is usually /dev/cdrom)
replace mydvd.iso with the name of the file you eant to copy the dvd to
Explenation:
dd = low-level binary copy command
if=/dev/cdrom  = input file is the cdrom drive
of=mydvd.iso File to copy the input file to. of is short for output file

As for the Nautilus problem, I don't know but it might be a bug, file a bug report

---

### Post by MockY on 2009-02-01
> **jerome1232 said:**
> That's because generally those dvd's are Dual Layer Dvd discs which can hold up to 8.5 GB's of data. There's a couple things you can do to reduce the size, k9copy can extract out only the main movie and generate an iso that's ready to burn to a single layer dvd, all without transcoding so there's no loss in quality.

Another method, this is the way I do it, is to use handbrake (or dvdrip) to transcode the movies to an avi file, perfect for keeping on the computer and playing on the computer, then use DeVeDe to generate a dvd burnable image from your avi file and burn it to dvd, this way you have two copies one on the comptuer one on disc.

DeVeDe and dvdrip are both in the repositories, handbrake does a considerably better job for me than dvdrip did.
```
sudo apt-get install dvdrip devede k9copy
```
[http://handbrake.fr/](http://handbrake.fr/)

Thanks for your response.

I used Handbreak but by extracting the movie to an .avi, making it around 1GB creates a lesser quality picture (obviously). I have yet to try to rip them in 4GB to see if that makes a difference. I tried out DVDShrink and set the output to 4GB, but some elements of the movie were a bit distorted, as in lines were visible when something moved fast on the screen (example being the flying animated THX guy before the movie Finding Nemo).

I will try out k9copy next, though I really don't like installing KDE software and all the KDE dependencies on a fully functional Gnome install.

---

### Post by jerome1232 on 2009-02-01
Yeah with handbrake I've found using the h.264 video codec video looks great, for audio I don't transcode it, I just copy it over as AAC.

That line thing your talking about is due to interlacing make sure you have whatever program (if transcoding is involved) set to deinterlace movies that do that, and yes with transcoding you will always lose some picture quality but I transcoded Bangkok Dangerous to a 1.5 GB avi file and it appears to be dvd quality to me on our 55" inch tv. (You might just be more picky than me too :) )  It does take some playing around with to get it the way you like it.

I was like that too about k9copy but it's a really great piece of software. It might be what your looking for since it doesn't actually transcode the video.

---

### Post by MockY on 2009-02-01
Thank you so much for the information. I will try many different options with the 3 software that you mentioned in order to perfect it. I mean, I don't want to copy all 90 DVDs and then find out that the quality is not the level I want it to be. I might be too picky, and I am watching all movies on a 61" TV, but I (actually my wife) would rather bring out the DVD and use the dvd player to watch the movie if the quality is not as good. And that is what I want to prevent since it is way more convenient to have the collection in the mediacenter instead of taking space on the shelves.
The DVD player uses HDMI and the XBMC box uses regular RGP output, but I seriously can't see a difference.

---

### Post by MockY on 2009-02-01
> **jerome1232 said:**
> Yeah with handbrake I've found using the h.264 video codec video looks great, for audio I don't transcode it, I just copy it over as AAC.

That line thing your talking about is due to interlacing make sure you have whatever program (if transcoding is involved) set to deinterlace movies that do that
The following is for HandBreak
AAC is grayed out when I select h.264. I assume there is something that I need to install before using that.

Furthermore, deinterlace, what should I select? Fast, Slow, or Slower?

---

### Post by jerome1232 on 2009-02-01
I did say AAC didn't I, I meant AC3 - Pass through.

I assume the Slower deinterlace would be the best quality

---

### Post by MockY on 2009-02-01
Thanks

---

