---
title: "Video playback jumpy/skippy"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Timzor on 2009-04-12
I've become rather frustrated with my video playback in Ubuntu.  A lot of times, the video will get "stuck."  The sound will continue playing but there will be no motion for a few seconds, and then the video will jump forward to sync up again with the sound.  Actually, sometimes the sound and video get completely out of sync, but that happens less frequently.

I'm not sure what the problem is. Whether it's with my hardware, software, settings, or just a matter of me using crappy media players.  I'm using VLC mainly, and sometimes Totem movie player.
My OS is  Ubuntu 8.10- the Intrepid Ibex.

Can anyone give me some tips to solve this problem?

---

### Post by the.phantom on 2009-04-12
do you have the latest video driver for your ???? card?

and what is the basic speck of your computer?
cpu
memory?

---

### Post by Timzor on 2009-04-12
> **the.phantom said:**
> do you have the latest video driver for your ???? card?

and what is the basic speck of your computer?
cpu
memory?

I don't know about the driver.  How can I find out?

This is my machine, here.
[http://www.bestbuy.com/site/olspage.jsp?skuId=9027714&st=dv3510&lp=1&type=product&cp=1&id=1218010176167](http://www.bestbuy.com/site/olspage.jsp?skuId=9027714&st=dv3510&lp=1&type=product&cp=1&id=1218010176167)

It should have all the specs...

---

### Post by Yvan300 on 2009-04-12
Ok here's what you can do when playong videos:

Turning off compiz helps. You can do this by going into appearance and turning visual effects to none. You could also try to use little applications simultaneously while watcching videos. Also chck your pc's temperature. If it becomes too hot then your cpu will clock at lower speeds to prevent itself from frying. This lower clock speed may not be enough to play your video.

---

### Post by Timzor on 2009-04-12
> **Yvan300 said:**
> Ok here's what you can do when playong videos:

Turning off compiz helps. You can do this by going into appearance and turning visual effects to none. You could also try to use little applications simultaneously while watcching videos. Also chck your pc's temperature. If it becomes too hot then your cpu will clock at lower speeds to prevent itself from frying. This lower clock speed may not be enough to play your video.

I already tried turning off compiz.  I can't see any difference.  And I usually don't have any other programs running when I'm playing a video, as far as I know.

How do I check the temperature, and what should I do if it is too hot?

---

### Post by Timzor on 2009-04-12
Bump

---

### Post by Timzor on 2009-04-12
Any tips would be appreciated.

Any at all.

---

### Post by Timzor on 2009-04-12
Bump

---

### Post by lykwydchykyn on 2009-04-12
Are these problems with all videos, or just videos played from a disc?

---

### Post by Timzor on 2009-04-12
> **lykwydchykyn said:**
> Are these problems with all videos, or just videos played from a disc?

Actually, I don't think I've ever had problems with movies played from discs.  Just things stored on my hard drive.

---

### Post by RedSingularity on 2009-04-12
This is happening in VLC?

---

### Post by RedSingularity on 2009-04-12
Go to Tools>Preferences>Video and change the output to "x11 video output"

---

### Post by lykwydchykyn on 2009-04-12
What file format are the videos you're playing?  All different or one particular sort?

---

### Post by Timzor on 2009-04-12
> **Shadow121 said:**
> Go to Tools>Preferences>Video and change the output to "x11 video output"

That doesn't seem to help.

---

### Post by Timzor on 2009-04-12
> **lykwydchykyn said:**
> What file format are the videos you're playing?  All different or one particular sort?

Now that you mention it, it might only be MKVs.

---

### Post by lykwydchykyn on 2009-04-12
Are you running the recommended proprietary Nvidia video driver?  You can check this with the driver tool under the system menu (I think that's where it is, anyway; I'm not using GNOME).

---

### Post by RedSingularity on 2009-04-12
System>Administration>Hardware Drivers.

---

### Post by Timzor on 2009-04-12
It looks like I was a few versions out of date.  I updated and rebooted, but it doesn't seem to have fixed it.

---

### Post by Timzor on 2009-04-12
So, I feel this is rather interesting.  I took one of the files I was having trouble with, booted into Windows, and tried playing it there.

In Windows Media Player, it played perfectly.  But when I tried to use the windows version of VLC, it was skipping just like it does when I play it in Ubuntu.


Is it just the program I'm using after all?

---

### Post by Yvan300 on 2009-04-13
Hey the real bottle---- neck could be your pc's specs It's like trying to watch blue ray using a latitude c610 (10 year old pc) if your graphics card can't take high resolution videos then they will play choppy:) What graphics card do you have ?

---

### Post by overdrank on 2009-04-13
> **Yvan300 said:**
> Hey the real bottle---- neck could be your pc's specs It's like trying to watch blue ray using a latitude c610 (10 year old pc) if your graphics card can't take high resolution videos then they will play choppy:) What graphics card do you have ?

Specs in post #3. [Here]("http://www.bestbuy.com/site/olspage.jsp?skuId=9027714&st=dv3510&lp=1&type=product&cp=1&id=1218010176167")
Nvidia 9300 
I am experiencing some similar issue with my nvidia 8200 but with compiz off there is no issues.

---

### Post by gunbladeiv on 2009-05-01
i'm having the same problem here. and i'm using ATI Xpress200M. None of the tips given earlier work on my laptop.  And i guess it's a problem with VLC.

---

### Post by andrewPCT on 2009-05-09
Having the same problem as well -- nvidia card this time.

Tried:
Compiz on
Compiz off
upgrade from 8.10, then tried a clean install (preserving /home)

This is really starting to bug me, as I experience it with any and all videos, flash (nonfree), vlc, totem, etc.

---

### Post by noelsanidad on 2009-05-09
The problem it seems is not always present, sometimes when I watch avi files, it is okay but when I watch another one, the problem shows itself.

---

### Post by zubin71 on 2009-05-09
> **Timzor said:**
> I already tried turning off compiz.  I can't see any difference.  And I usually don't have any other programs running when I'm playing a video, as far as I know.

How do I check the temperature, and what should I do if it is too hot?

um... i really do not think its the "temperature" factor that`s influencing your video capabilities. i had encountered similar problems when a friend of mine installed ubuntu. however, the problem was taken care of by turning compiz and other "visually-taxing" features off.

do you have a graphics card? 
if you do, i suggest you update your driver.
go to system > administration > hardware drivers.
you can upgrade your drivers there.
hope this helps. if it does not, please post your computer configuration in the next post.

---

### Post by Sanjima on 2009-11-20
I'm having the same exact problem and it's quite frustrating. I'm running Ubuntu 9.10 on a fresh installation. Compiz is turned off and no other visually tasking features or anything are enabled, and the only thing I'm running is the movie.

I use Totem, and it happens on both small and large videos (resolution-wise, as well as file size).

My system specs have nothing to do with it, because when I was running Linux Mint I did not have any such problem. I was using Totem, and playing the exact same files. I even had other programs running and Compiz enabled and I had no such problems.

I might add that I was also using the same exact video driver on Mint as I am here on Ubuntu.



> **zubin71 said:**
> if it does not, please post your computer configuration in the next post.

His computer specs are in the third post, in the link he gave.



edit:

Curious.. I seemed to have found a fix for this problem.. On my computer, at least. You all are welcome to try, although it might seem to not pertain to the problem. Just try it, it worked for me so far. =]

All I did was go to System > Preferences > Sound
On the "Output" tab, it had "Simultaneous output to Internal Audio Analog Stereo" selected. So I changed that to "Internal Audio Analog Stereo" instead. It was directly above the Simultaneous one.

So far, this seems to have worked perfect for me. In fact, the sound seems to be flawlessly synced with the video, even moreso than the other option when the video wasn't lagging.

I'm watching a movie at the moment, and before I noticed that one of the things that would cause excessive lag in the video would be if I paused, or seeked around in the video. I tried doing this for about a minute straight, and had absolutely no problem. ^^

I hope this poses some usefulness to everyone.

---

### Post by devil404 on 2010-04-07
> **Sanjima said:**
> 
All I did was go to System > Preferences > Sound
On the "Output" tab, it had "Simultaneous output to Internal Audio Analog Stereo" selected. So I changed that to "Internal Audio Analog Stereo" instead. It was directly above the Simultaneous one.
...
I hope this poses some usefulness to everyone.

Very useful Sanjima! I've been plagued with this problem since my upgrade to 9.10. Choppy video playback, then it speeds up and stops, speeds up then stops. I have two audio outputs: analog and HDMI. My Video card is an ATI Mobility Radeon HD 3400 with the latest drivers.

---

