---
title: "Best Program to create .ISO files from a CD or DVDs"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by TAspr on 2011-06-13
I have yet to find one that will create an ISO file from a CD or DVD that is simple.  Can you help me out?

---

### Post by Paqman on 2011-06-13
Brasero?

---

### Post by coffeecat on 2011-06-13
Brasero. Disc copy > in the Copy CD/DVD mini-window choose "image file" under "Select a Disc to Write to". Click on Properties to change the path and/or file name. Now click on the "Create Image" button.

---

### Post by TAspr on 2011-06-13
Why won't the system populate the audio files in the audio CD section?  I think it wants to burn an existing ISO file??


I am attaching a pic to find out.

---

### Post by coffeecat on 2011-06-13
I don't know. I am not having that problem. If I insert an audio disc, open Brasero and choose Disc Copy, I get "Audio Disc: 53 min" in the Select disc to copy, and a choice of .toc or .cue images if I click on properties.

Try another audio CD and see if you still get the problem. Also, k3b is perfectly good for making images of optical discs. In k3b, Tools > Copy Medium. Then you get a more complex options window than in Brasero. You might find k3b works for you if you can't get Brasero to work.

---

### Post by TAspr on 2011-06-13
> **coffeecat said:**
> I don't know. I am not having that problem. If I insert an audio disc, open Brasero and choose Disc Copy, I get "Audio Disc: 53 min" in the Select disc to copy, and a choice of .toc or .cue images if I click on properties.

Try another audio CD and see if you still get the problem. Also, k3b is perfectly good for making images of optical discs. In k3b, Tools > Copy Medium. Then you get a more complex options window than in Brasero. You might find k3b works for you if you can't get Brasero to work.

Thanks Partner, I will try and create the image file.  I am not familiar with the .toc or .cue image files; that is why I got confused, but if it performs the same function, then so be it.  What are these file types anyway?

---

### Post by psusi on 2011-06-13
They describe the track layout of the disc so that programs trying to read or burn the corresponding .bin or .raw image file know where each track begins and ends.

---

### Post by YesWeCan on 2011-06-13
K3b

---

### Post by coffeecat on 2011-06-13
What psusi said. ^  ^  ^

TOC: [http://en.wikipedia.org/wiki/Optical_disc_authoring#TOC](http://en.wikipedia.org/wiki/Optical_disc_authoring#TOC)

BIN/CUE: [http://www.afterdawn.com/glossary/term.cfm/bin_cue](http://www.afterdawn.com/glossary/term.cfm/bin_cue)

Brasero defaults to "Cdrdao image" which gives you a .toc.bin file and a .toc file which is a text file. Selecting Cue image gives you a .bin and a .cue file.

---

### Post by crispy_420 on 2011-06-13
> **TAspr said:**
> Why won't the system populate the audio files in the audio CD section?  I think it wants to burn an existing ISO file??


I am attaching a pic to find out.

You'll also notice nothing shows because you are looking for an image file inside your source CD.

---

### Post by parkerskouson on 2011-06-13
> **YesWeCan said:**
> K3b
Yes only use K3b. That will make it bootable. most other programs will not. the programs have to specialize in .ISO burning.

---

### Post by wep940 on 2011-06-13
I've learned something here with this thread, so thank you all for your input to TAspr, but I have to ask, if the OP is just burning an ISO of an audio disk, why would it need to be bootable?  I'm a little stupid here so I'm hoping I'll learn something else I need to know on that.

Sorry to jump in - just wanted to get that answer.

---

### Post by coffeecat on 2011-06-14
> **wep940 said:**
> I've learned something here with this thread, so thank you all for your input to TAspr, but I have to ask, if the OP is just burning an ISO of an audio disk, why would it need to be bootable?

I would have thought it wouldn't. A bootable audio disc? I've not heard of such a thing.

Also, concerning making ISOs of data discs which happen to be bootable, Brasero can do this  just fine, just as well as k3b. If you use Brasero to create an ISO of a bootable disc and then burn that ISO to another disc, you get a bootable disc.

Going back to audio discs, I do have one interesting hybrid. It looks like a standard audio CD and plays like an audio CD in ordinary media players, but when I put it in the optical drive of my Ubuntu system, two things happen. A popup appears asking whether I want to play it with Banshee and a nautilus window opens with some data files in it. Double-clicking on the index.htm file that's among them opens up firefox with a web-page all about the artist. There are also two disc icons on the desktop, one for the audio bit and one for the data portion.

Perhaps this is common but I'd not seen this before and there's no mention of it in the CD booklet. Perhaps if I make an ISO of the CD with k3b, k3b will make it bootable! :wink:

---

### Post by wep940 on 2011-06-14
Yeah, I didn't see a reason for it being bootable, but maybe I misread the intent of  a prior post.

An audio CD with HTML on the artist, etc.?  I've never heard of that before either but it sounds great!  If you put it in an stand-alone entertainment center such as a surround sound for a TV, does it act like a DVD and show the HTML option as well, or does it still just show the audio?

Sounds like something interesting!

If you also get it bootable, let me know, as I would really like to see my PC booting up and running the Inagodavida OS, and then compare it to the Beethoven OS to see what the difference in styles might be! ;)

---

### Post by coffeecat on 2011-06-14
> **wep940 said:**
> An audio CD with HTML on the artist, etc.?  I've never heard of that before either but it sounds great!  If you put it in an stand-alone entertainment center such as a surround sound for a TV, does it act like a DVD and show the HTML option as well, or does it still just show the audio?

I never thought of doing that. I'll try it it my Sony PS3. Thanks!

> **wep940 said:**
> If you also get it bootable, let me know, as I would really like to see my PC booting up and running the Inagodavida OS, and then compare it to the Beethoven OS to see what the difference in styles might be! ;)

Beethovenbuntu! :p Or even better, Beethoven's9thbuntu. &#9834; &#9835; *Freude, schöner Götterfunken. Tochter aus Elysium....* &#9835; &#9834;  :-\"

:wink:

---

### Post by L Campbell on 2011-06-14
> **TAspr said:**
> I have yet to find one that will create an ISO file from a CD or DVD that is simple.  Can you help me out?

I vote for K3b, it has always worked well for me.

---

### Post by TAspr on 2011-06-14
> **wep940 said:**
> I've learned something here with this thread, so thank you all for your input to TAspr, but I have to ask, if the OP is just burning an ISO of an audio disk, why would it need to be bootable?  I'm a little stupid here so I'm hoping I'll learn something else I need to know on that.

Sorry to jump in - just wanted to get that answer.

Exactly, that is all I wanted to do.  So I am with you.

---

### Post by halibaitor on 2011-06-14
If you are using WINE, then the program you want is ImgBurn.  It is the only one that has worked properly for me.  YMMV

---

### Post by local user on 2011-06-15
> **YesWeCan said:**
> K3b

I agree with him K3B is the best ISO tool ;)

---

### Post by TAspr on 2011-06-15
> **halibaitor said:**
> If you are using WINE, then the program you want is ImgBurn.  It is the only one that has worked properly for me.  YMMV

Ok, can you pkease layout the steps on how to use WINE?  I am still having trouble using it.  How do you even approach the windows program file, where do the files reside, and how do you launch them?  Can I make a specific directory with all the files in them?

---

### Post by kimda on 2011-06-15
Or you can also make iso's with the dd command. 

```
dd if=/dev/sr0 of=disk.iso
```

---

### Post by TAspr on 2011-06-15
> **kimda said:**
> Or you can also make iso's with the dd command. 

```
dd if=/dev/sr0 of=disk.iso
```

What program does it use to do this using the command line??

---

### Post by psusi on 2011-06-15
> **TAspr said:**
> What program does it use to do this using the command line??

What?  That IS the command line program.

---

### Post by TAspr on 2011-06-15
> **psusi said:**
> What?  That IS the command line program.

I understand that, but what does Ubuntu use as a native program to do this?  There is no name for it?

---

### Post by nothingspecial on 2011-06-15
The name of the program is dd

It is a very quick and effective way of making an iso image.

I use it to backup dvds

However, I should mention that it is also a very quick and effective way of wiping a hard drive or completely destroying your system if used incorrectly. If you are going to use dd make sure you understand what you've just typed before you hit enter.....

... and then check again, just to be sure.

---

### Post by HermanAB on 2011-06-15
Howdy,

There are two simple ways to read a CD/DVD and write it to an ISO file.

Data Definition:
$ dd if=/dev/cdrom of=filename.iso

The good old kitty cat:
$ cat /dev/cdrom > filename.iso

Pick your poison...

---

### Post by gtippitt on 2011-07-01
K3B is pretty simple and works great.

---

### Post by beew on 2011-07-01
acetoneiso

---

### Post by L Campbell on 2011-07-24
> **TAspr said:**
> I have yet to find one that will create an ISO file from a CD or DVD that is simple.  Can you help me out?

K3b is my favorite.

---

### Post by pierreyy on 2011-07-24
> **TAspr said:**
> I have yet to find one that will create an ISO file from a CD or DVD that is simple.  Can you help me out?

Brasero and then burn image(bottom tab) very simple. Id stay away from the command line, you dont wanna something while ur in root and screw something up...

"However, I should mention that it is also a very quick and effective way of wiping a hard drive or completely destroying your system if used incorrectly. If you are going to use dd make sure you understand what you've just typed before you hit enter....." - NOTHINGSPECIAL

---

### Post by Jagoly on 2011-07-24
> **halibaitor said:**
> If you are using WINE, then the program you want is ImgBurn.  It is the only one that has worked properly for me.  YMMV

ImgBurn in wine is most definitely not simple. I can't imagine how a burner in wine could possibly work when plenty of excellent native software doesn't.

---

