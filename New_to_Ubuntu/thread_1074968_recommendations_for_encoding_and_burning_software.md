---
title: "recommendations for encoding and burning software"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Matt26 on 2009-02-19
i'm looking for suggestions on the best software for each of these two tasks in Ubuntu:

1) encoding video files for dvd video- for example AVI files

2) burning dvd video compilations with *if possible* on-the-fly encoding (for example, like Nero for Windows does when you add a video file to a dvd compilation and it encodes it to the proper format prior to burning it)

thanks.

---

### Post by handy on 2009-02-19
I rip with DVDShrink 3.2 which installs very easily & runs perfectly via Wine.  It just takes standard DVD disks removes any protection & has a few other options.  You can set the size it compresses down to single layer disk.  Usually takes about 20 minutes to do this, some shorter some longer, after which you burn.

The other software I rarely use is AVIDemux which is very powerful regarding the range of formats that it can convert to/from.

I expect that there are very likely more streamlined solutions though.

---

### Post by jerome1232 on 2009-02-19
I use handbrake to decrypt and transcode the dvd's to avi containers (I use h.264 video codec and ac3 pass-thru audio codec)

[http://handbrake.fr/](http://handbrake.fr/)

And I use DeVeDe to convert video files into ready to burn iso's that will play in your standard dvd player. I use brasero to actually burn the images to a dvd+/-r

DeVeDe is in the repositories.

And as the previous poster said avidemux is a pretty good video editor if you need to edit the videos, it can also transcode.

---

### Post by handy on 2009-02-19
@***jerome1232***: Can you copy multiple .avi's or whatever to a disk & use DeVeDe to make them all available on a standard DVD player?

There would need to be some kind of menu I suppose for this to work?

---

### Post by halitech on 2009-02-19
I was using ManDVD for my movie work that required menus but the new version of Devede does a great job of converting and preparing an iso. It even has a nice feature of calculating the proper bit rates so you can fit 4 45minute tv shows and put them on 1 dvd for playing in a standard dvd player.

---

### Post by jerome1232 on 2009-02-19
> **handy said:**
> @***jerome1232***: Can you copy multiple .avi's or whatever to a disk & use DeVeDe to make them all available on a standard DVD player?

There would need to be some kind of menu I suppose for this to work?

Yes you can put multiple video files into devede (it supports quite a few formats) and it will create a dvd that includes them all, it has a menu editor but I've never used it since I tell it to skip straight into the movie.

If your wanting to do what I'm thinking your wanting to do you can make several titles, each with it's own video, then create a menu that allows you to select which title you would like to play (Is this what your getting at?)

---

### Post by Dougie187 on 2009-02-19
For future reference, check out [www.osalt.com](www.osalt.com) for alternatives to software. In this case you can search for something like Final Cut Pro or iMovie or even iDvd

---

### Post by handy on 2009-02-21
> **jerome1232 said:**
> Yes you can put multiple video files into devede (it supports quite a few formats) and it will create a dvd that includes them all, it has a menu editor but I've never used it since I tell it to skip straight into the movie.

If your wanting to do what I'm thinking your wanting to do you can make several titles, each with it's own video, then create a menu that allows you to select which title you would like to play (Is this what your getting at?)

I have some .avi & a few vid's in other format, I was thinking I could back them up to DVD & if DeVeDe will convert them to the DVD standard & allow me to have a simple menu, then, providing it doesn't take forever to do the work of creating the standard DVD format disk, it might be worthwhile using DeVeDe to do the job.

---

### Post by Doug11 on 2009-02-21
I use VSO convertx. It runs nice in wine and I have not come across many formats that it would not convert to dvd. Another personal preference thing I guess.

---

### Post by Matt26 on 2009-02-21
> **jerome1232 said:**
> I use handbrake to decrypt and transcode the dvd's to avi containers (I use h.264 video codec and ac3 pass-thru audio codec)

[http://handbrake.fr/](http://handbrake.fr/)

And I use DeVeDe to convert video files into ready to burn iso's that will play in your standard dvd player. I use brasero to actually burn the images to a dvd+/-r

DeVeDe is in the repositories.

And as the previous poster said avidemux is a pretty good video editor if you need to edit the videos, it can also transcode.

i tried DeVeDe today and it seems to have worked great- i couldn't get the other video files i had (converted or original) to burn properly or be recognized by my old DVD player- in Windows or Ubuntu.

good find!

---

