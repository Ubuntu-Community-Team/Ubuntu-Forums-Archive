---
title: "Need help running Blurb BookSmart on Linux"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Cosmogirl on 2010-06-18
Hi,

I wonder if anyone can help me finally get rid of Windows forever?

The only app I still use on Windows is Blurb BookSmart.  It annoys me that I still have to use Windows for this one thing so I was delighted to discover recently that you can convert BookSmart to run on Linux - found several posts including the ones [here]("http://www.flickr.com/photos/mydailycommute/391528303/#comment72157605398264838") and [here]("https://help.ubuntu.com/community/BookSmart").  I decided to follow the instructions in the second link (seemed simpler for a beginner) but I'm having problems with the installation.

I installed dmg2img and downloaded the Mac version of BookSmart 2.6.1.   However when I tried use dmg2img to convert the file (which is actually a newer version of BookSmart than the one mentioned in the Community Documentation), I got an error message:

> ERROR: Can't open input file BookSmart_2.6.1.dmg

Am I doing something wrong, or is there a problem with the file?

Thanks for your help.

---

### Post by mister_p_1998 on 2010-06-18
Easiest way that works if you dont mind using around 10gb of space is Virtualbox. All I use it for is Sonicstage to transfer mp3's to my Minidisc.
Steve

---

### Post by Cosmogirl on 2010-06-18
Thanks for replying.  In fact I already have Virtualbox but that still means I need to use Windows!  I know some people have managed to install BookSmart successfully onto Linux.  Also I'm sure it would run much faster and I wouldn't need to transfer all my photos onto the virtual system in order to make a photo book.

---

### Post by ieee488 on 2010-06-18
> **Cosmogirl said:**
> Hi,

I installed dmg2img and downloaded the Mac version of BookSmart 2.6.1.   However when I tried use dmg2img to convert the file (which is actually a newer version of BookSmart than the one mentioned in the Community Documentation), I got an error message:


Is the downloaded file in the same directory as dmg2img program? That command assumes that it is.

---

### Post by Cosmogirl on 2010-06-19
Good point.  In fact they don't have to be in the same directory (dmg2img is a utility) but you're quite right, stupidly I hadn't accessed the directory with my BookSmart file in it before running the command.  So thanks!  I have now converted the file to img.

I'll keep this thread open as will probably need more help again soon!  I'll let you know if I manage to get BookSmart up & running.

---

### Post by simonrobidas on 2010-06-25
I also had trouble trying to install BookSmart 2.6.

Last night, I tried installing a newer version, BookSmart 2.8, and it worked, although I had to install sunjava 1.6 instead of using the default openjdk. I used the instructions found here: [http://help.ubuntu.com/community/BookSmart]("http://help.ubuntu.com/community/BookSmart")

One glitch: BookSmart crashes when trying to load pictures into a book if the source is my computer's local hard drive. It imports pictures form SmugMug just fine though. Go figure... I have to admit I didn't spend much time trying to figure out this glitch as I had all the pictures I wanted in SmugMug.

---

### Post by purple52 on 2010-10-19
FYI, seems like BookSmart 2.9.1 works with local files again.

---

