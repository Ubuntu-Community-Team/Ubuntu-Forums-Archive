---
title: "how to play movie with .3gp extension?"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by RajaAjmal on 2009-06-20
hi there,
i've some movies with .3gp extension. on playing them, i can only view the movie, but no sound. i've installed VLC player, but to no avail. any help pls?

---

### Post by Hendronicus on 2009-06-20
I've had good luck with Xine.

---

### Post by Rabindranath on 2009-06-20
Have you enabled compiz? I think compiz should be enabled for proper video playback. You can enable it under System > Preferences > Appearence

---

### Post by Marlonsm on 2009-06-20
Maybe there is some codec missing.

Go to: System > Admin > Synaptic and install ubuntu-restricted-extras.

---

### Post by andrew.46 on 2009-06-21
Hi RajaAjmal,

> **RajaAjmal said:**
> i've some movies with .3gp extension. on playing them, i can only view the movie, but no sound. i've installed VLC player, but to no avail. any help pls?

Many 3gp movies have amr sound and as this is a proprietary codec it is not included by default in Ubuntu. One way to play these files is to enable the Medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and then install MPlayer and optionally SMPlayer:

```
sudo apt-get install mplayer smplayer
```

and I suspect that SMPlayer will then play your 3gp file with no problems.

Andrew

---

### Post by RajaAjmal on 2009-06-21
thanx for ur reply.

but i've tried everything mentioned and nothing work. any more idea pls?

---

### Post by andrew.46 on 2009-06-21
Hi RajaAjmal,

> **RajaAjmal said:**
> but i've tried everything mentioned and nothing work. any more idea pls?

Hmmmm..... sounds a little odd. Can you post this file anywhere?

Andrew

---

### Post by andrew.46 on 2009-06-22
Well, just to make things a little easier I have produced a typical 3gp file that is made up of h263 video and amr sound:

```
wget http://www.andrews-corner.org/samples/Ramstein_Du_Hast.3gp
```

It is a great example of why such sound is pretty bad and h263 video is pretty ordinary :-). But more importantly this *will* play with the MPlayer from Medibuntu, so if you can download this one and give it a go?

Andrew

---

### Post by yochaigal on 2009-07-05
You need AMR codecs to hear sound for .3gp files in ubuntu.  
See:

[http://ubuntuforums.org/showthread.php?t=762399](http://ubuntuforums.org/showthread.php?t=762399)

[http://ubuntuforums.org/showthread.php?t=178455](http://ubuntuforums.org/showthread.php?t=178455)

---

### Post by ukrapi on 2009-07-11
Hi RajaAjmal
Did you try Realplayer11? I had the same problem which you described and managed to get both video & sound with Realplayer-11 on jaunty.

Goto:
[http://www.real.com/linux/]("http://www.real.com/linux/")
Download the deb file.

---

### Post by steveneddy on 2009-07-11
I believe you need

libamrnb3

and

libamrwb3

which is part of Medibuntu.

I had to do this to watch Blackberry video.

I use Mplayer.

Try this:

[http://blog.sartek.net/2008/05/mplayer-from-source-with-3gp-support-on.html](http://blog.sartek.net/2008/05/mplayer-from-source-with-3gp-support-on.html)

---

### Post by andrew.46 on 2009-07-11
Hi steveneddy,

> **steveneddy said:**
> I believe you need

libamrnb3

and

libamrwb3

Certainly the svn MPlayer *used* to play amr/3gp files utilising these libraries but this support has been dropped in the last couple of days. Older versions than the most cutting edge svn will still play these files though.

All the best,

Andrew

---

### Post by lisati on 2009-07-11
One option might be to check out video conversion tools. In my collection of CDs I have one for a mobile edition [Ulead ]("http://www.ulead.com/products/runme.htm")Video Toolbox which has an option to convert files from 3gp format to other formats. I have no idea if there's a Linux-friendly version of if the copy I have (a Windows version which came with a DVD burner) will work with Wine - I haven't had the need to do anything more with my 3g phone with Ubuntu beyond using it as a modem.

---

### Post by steveneddy on 2009-07-11
> **andrew.46 said:**
> Hi steveneddy,



Certainly the svn MPlayer *used* to play amr/3gp files utilising these libraries but this support has been dropped in the last couple of days. Older versions than the most cutting edge svn will still play these files though.

All the best,

Andrew

Well then, just use ffmpeg to convert the video and be done with it.

---

