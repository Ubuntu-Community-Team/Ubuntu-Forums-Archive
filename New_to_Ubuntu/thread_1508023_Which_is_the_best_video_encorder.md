---
title: "Which is the best video encorder ?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2010-06-12
Hi Guys,

I'm movie freak so I deal with lot of video files, DVD's and Blu-Rays. Primarily I was a windows user in that I'd lot of software choices to select from.

But when I got enlightened I redeemed my self from Bills and Gates and dedicated my full PC to Ubuntu(my first true love).

But now I've this small problem of finding a good video encoder to backup my DVD's and also to convert my video files to other formats like (MKV, 3GP, DivX, MP4 etc ...).

I did little googleing and found these three softwares which will be best for my need please do tell me which to pick.

1.WinFF (The GUI front end for FFmpeg).
2.HandBrake.
3.DVD::RIP (Is Brasero a equlant).

Thank you in advance.

Oh and I just for got which has the best video file format capabilities.

---

### Post by 3rdalbum on 2010-06-12
I think Handbrake and DVD::Rip only deal with DVDs, not with video files already on your hard disk. WinFF is okay but a bit simplistic and not terribly flexible.

I use FFMPEG on the command-line for much of my encoding needs; it's not too hard if you keep the 'man' page open when creating the command. Otherwise you may find that a video editor will do a good (but slower) conversion. Kdenlive works well, but many people swear by Avidemux.

---

### Post by sadaruwan12 on 2010-06-12
bump

---

### Post by Oropher8598 on 2010-06-12
I'd recommend Handbrake as it's fairly easy to use and pretty powerful. It can handle files already on your hard disk as well as the original DVDs, and can transcode from almost any format. It has presets for a variety of devices like iPods etc, as well as manually adjustable settings if you want to dig into the details. The only issue you might have with it is if you want to convert video *into* many different codecs or container formats - Handbrake is focused on h.264 and Theora.

WinFF and FFMPEG are alright, but they have a few 'gotchas' lurking for the uninitiated :) However they may be what you want if you need to convert into a wide range of formats. I've no experience with DVD::Rip I'm afraid.

---

### Post by eyeofreason on 2010-06-12
I'm not sure if I now what you're looking for exactly. I too am a movie buff. I use.

1. K9copy to back up my DVDs :-)
2. Devede to make dvds from my Avi files
3. k3b to burn DVDs with 

All of them are in the repos
Hope that helps!

---

### Post by gandaran on 2010-06-12
[http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/](http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/)
another gui for ffmpeg.

---

### Post by Tholley on 2010-06-12
I also use DeVeDe to create ISO image of the movies, and K3B to burn to disc.
 
DeVeDe takes alittle practice, but once you figure it out, it works good.

---

### Post by Ducatiboy Stu on 2010-06-12
K9copy will make a 700mb .avi file straight from a DVD, just select the main movie file , usually the biggest, and rip to avi format directly

---

### Post by Shampyon on 2010-06-12
I'm gonna put in another vote for Handbrake.

I use ***k9copy*** to back up my DVD to the hard drive as an *ISO*. Then I use ***Handbrake*** to convert to an *x264* codec in an *MKV* container with either *AAC *or *AC*3 audio. Occasionally I also use it to convert *XViD AVI* files to *x264/MKV*.

Since I'm doing this to stream my movies to my lounge room media player on a standard definition TV, I often encode them in a small size. If you want full quality it's usually best to just use the *High Profile* preset, which encodes to *x264/M4V* using the *Constant Quality* setting.

You can also experiment with converting by filesize - you should be able to get full HD quality in an *x264 MKV* with a filesize of about 500MB per 15 minutes of movie runtime - that comes to about 4.4GB for a two hour movie. You can also go by bitrate - 1800 kbps is pretty good, but you can take it up to about 6000kbps while keeping most files under 5GB.

Since I don't have HDTV yet I usually make mine much smaller - around 4MB to 8MB per minute (or a bitrate of 500kbps to 1000kbps), bringing it between 350MB and 700MB per 90min film. Saves space and it's a good filesize/quality tradeoff, especially if you use a portable media player.

My setup has 3GB RAM and a 3GHz Cure2Duo CPU, and my encoding time is usually about 2 to 2.3 times the source video's runtime.

eg: 90min movie = (2.3 x 90) = 207min or 3hr 27min encoding time. It can vary wildly, though - some may take 5 or 6 hours. Best to start them encoding when you're ready for bed.

---

### Post by sadaruwan12 on 2010-06-13
Thank you for all your contributions.

I what I want is a good DVD ripper and a file format converter for a example VOB -> AVI(DviX) AVI -> MKV like that.

Most people tell me FFMpeg is good but it's CLI based so like to know if theres a good GUI front end for that.

---

### Post by Shampyon on 2010-06-13
WinFF is a good GUI for ffmpeg, but I don't know if it does MKV. I know you can convert from ISO or VOB to AVI (DivX, XViD, x264, etc) with k9copy, and you can set it to use either ffmpeg or mencoder.

---

### Post by diablo75 on 2010-06-13
Here's a guide I wrote for using k9copy to backup DVD's (either the individual title to an AVI, or the entire DVD with menus and all to a 4.2 gig ISO file).

[http://davestechsupport.com/blog/2009/02/04/how-to-backup-a-dvd-with-ubuntu-linux/](http://davestechsupport.com/blog/2009/02/04/how-to-backup-a-dvd-with-ubuntu-linux/)

---

### Post by sadaruwan12 on 2010-06-15
than you guy's

---

### Post by MrWES on 2010-06-15
vobcopy -- best way to rip a vob from a DVD

---

### Post by sadaruwan12 on 2010-06-17
What I really want is to convert file formats.

---

