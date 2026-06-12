---
title: "video converter?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by gackt on 2009-02-24
Ok can someone tell me what video converter software is available in the repo i try cache search but it's not helping. I want software that can convert video to other format ( not just a dvd ripper). I need software that can convert avi to vcd format or dvd. 
Thanks

---

### Post by llamabr on 2009-02-24
You want ffmpeg and mencoder, but be careful not to read the man pages.

---

### Post by gackt on 2009-02-24
why?

---

### Post by gackt on 2009-02-24
i just found out that those two software are already installed in my buntu. but when i hit alt+F2 and type mencoder it shows up nothing. Is it text based? is there any software that can do the same thing and have GUI?

---

### Post by llamabr on 2009-02-25
Try using google.

I'm sorry, I'm forbidden by the forum code of conduct from suggesting that you read the technical manuals associated with this software.

In fact, I don't suggest that you read up on google to learn how to use these programs, even if the information is there.

---

### Post by gackt on 2009-02-25
you tell me to google and not to read it at the same time? Arghhh i think i'll just use wine for windows software.

---

### Post by Arylon on 2009-02-25
> **llamabr said:**
> be careful not to read the man pages.

This is either a failed attempt at reverse psychology, or the man pages are a poorly written confusing mess. Of course I think most of Linux's man pages are confusing, but maybe that's just me. ;)

---

### Post by Rolcol on 2009-02-25
You can try HandBrake but it's not in the repositories.  They have the .deb package for Ubuntu.  

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by gackt on 2009-02-25
> **Rolcol said:**
> You can try HandBrake but it's not in the repositories.  They have the .deb package for Ubuntu.  

[http://handbrake.fr/](http://handbrake.fr/)

thanks i'll try it

---

### Post by Ripose on 2009-02-25
Use VLC

---

### Post by anewguy on 2009-02-25
I had problems, and admittedly in version 7.04 (?), with memcoder, ffmpeg and some related and "based-on" tools.  This was due to bugs at that time in a build process to make a conversion tool I downloaded from the repositories.  I will be watching this thread as I would like to find such a product for myself as well (converting avi to a format useable on a Cd or DVD that can be read by something other than Linux).

I will throw something in here that I hope doesn't distract from this:  there is a free download in Windows called Kates' Video Converter that has worked wonders for me.  Has anyone tried this in Wine or found a comparable product in Linux?


Thanks, and hope I'm not distracting from this thread!

Dave ;)

---

### Post by Bradtek on 2009-02-25
WinFF works well for me, just as easy as any Windoze app

[http://winff.org/html/](http://winff.org/html/)
There is an Ubuntu 8.10 version

I assume you need to have ffmpeg installed
I don't actually remember as I installed it 
shortly after Ubuntu insta;;

---

### Post by bailbath on 2009-02-25
> **gackt said:**
> i just found out that those two software are already installed in my buntu. but when i hit alt+F2 and type mencoder it shows up nothing. Is it text based? is there any software that can do the same thing and have GUI?

Programs use those two to process video. Try Avidemux it is a menu based gui that I find easy to use. I would try to use the programs from Ubuntu package manager,as it will auto update, rather than a non native program in wine.
Ian

---

### Post by TenPlus1 on 2009-02-25
Avidemux can convert video formats from one to the other

DeVeDe can convert video formats to Video DVD or SVCD formats...

Both can be found on [www.getdeb.net](www.getdeb.net)

---

### Post by anewguy on 2009-02-25
Have they "fixed" avidemux?  The reason I ask it is one of the applications I had trouble with in 7.04.  The audio would get further and further ahead of the video when converting avi to another format.  This is why I went through all the build processes for 3 or 4 pieces of software so I could rebuild avidemux with a supposed fix.  One of those make processes eventually caused avidemux not to make.  That is the main reason I didn't recommend it, but I also didn't want to start a debate in this thread - I'm just watching for answers myself.  If avi conversion to another format has been fixed so the video and sound are now in sync, I would surely appreciate knowing that, so thanks for any input you provide in that regard while answering the original poster's question.

Thanks!  ;)


dave;)

---

### Post by Cresho on 2009-02-25
winff and cinelerra.  Use Winnff to convert your videos to mpeg2 and import ton cinelerra.  then after you can export ad reconvert in winff.

---

### Post by Ms_Angel_D on 2009-02-25
WinFF is a great converter I use it's a mandatory install for me on my systems, I suggest you have a look at it ;). Good Luck!

---

### Post by gackt on 2009-02-25
Thanks!!!!! avidemux is somewhat slow and the gui is well....could have been better..hehe or it is just my feelings.

Use vlc? how am i gonna use vlc to convert video..

winff = could not find package ( im using offline repo heheh).

I wonder if there is one super software that could convert video, audio (mp3 to ogg), picture (bmp) whoa that would be nice.

---

### Post by kamolt on 2009-02-25
To convert video's to another format I use AVIDEMUX. It has some nice filters and you can also do some editing. Maybe it's not fast but the result is excellent. Some expensive commercial programs I tried before did a worse job. I usually convert to x264 and dont see any difference with the original. My core I7 needs about 2 hours to convert a 90min movie from mpeq to x264 in dual pass mode. Since I can easily run other programs at the same time I dont care about the speed. After all it's the machine that does the work, I could eat, watch tv etc in the meantime.

---

### Post by llamabr on 2009-02-25
If you want to convert images, then you want imagemagick, which is the backend for gimp.

---

### Post by anewguy on 2009-02-25
Hey gackt!!  I was trying hard not to hijack your post, but it seemed like the questions fit into your quest for the type of product I've been searching for as well.  Please let me know how things work for you so that maybe I can try that product as well and see if it works out for me - feel free to p.m. me.

Also, a trick I learned for marking things solved even though it's been removed from the forum for now:

Go to your opening thread, click edit, then advanced.  This lets you modify the title, so you can include something like SOLVED or [SOLVED] at the front or the back of the title.  A little more work than the single button click we were used to, but it does get the job done.

Good luck, and let me know how your testing goes!!
Dave ;)

---

### Post by gackt on 2009-02-26
Thank for the tip ( kind a primitive but ehhhh it works)

---

### Post by Ripose on 2009-02-26
> Use vlc? how am i gonna use vlc to convert video..

Click on MEDIA --> Convert/Save

---

### Post by hiproductions on 2009-03-03
I use Mpeg streamclip. Its free and we use it for downconverting and file conversion from one format to the other. I love me som Mpeg Streamclip.

---

