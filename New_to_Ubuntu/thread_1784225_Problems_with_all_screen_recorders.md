---
title: "Problems with all screen recorders"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by AlvitrValkyrie on 2011-06-16
Ubuntu 10.10 GNOME

None of the screen recorders I've tried are working. They either dont make it through saving screencasts, or the video they produce is messed up.
For example, gtk record My Desktop. Amazing screen quality. Amazing sound quality. However, when I watch the video it produces, there's a big problem. What ends up happening is that whenever I switched to a new tab in a web browser, or opened up a new program, only bits and pieces of windows would record, resulting in rigid and highly pixilated edges. Also, these bits and pieces of windows would seem to stay on the screen in random places.

Since this is happening with ALL screen recorders I've tried (Including Istanbul and RecordItNow,) I believe it might be a problem with the recorders' settings, or Ubuntu itself. I don't think it's the graphics cards that cause the problem. Everything else works, including the Flash bits of websites (which, on the other 10 or so Installations of Ubuntu 10.10, would randomly go grey.) If it is the graphics cards, I would really like some suggestions that do NOT include installing the nvidia drivers. This is the nteenth time i am giving Ubuntu a chance, and all the NVidia drivers ever did was make sure I could only boot into a tty1 screen and NEVER access my GUI ever again, no matter how many guides' and forums' tactics I used. I've experienced no problems with opensuse, ever, so I'm also sure it's not the settings of the screen recorders.

Alienware m11x
Core 2 Duo
NVidia GForce

Thanks in advance ^^

---

### Post by GWBouge on 2011-06-16
You could try using straight ffmpeg and see if you get the same issues.  Here's an example command:

```
# Record Desktop
#	-s Size:			1920x1080
#	-r	Framerate:		30fps
#	-b	Bitrate:		5000 kbits/s
#	-ab	Audio Bitrate:	128 kbits/s
#	-ac	Audio Channels:	6
#	-i	Input:			$DISPLAY (:0.0)
#	Output File:		out.mpg

ffmpeg -s 1920x1080 -r 30 -b 5000k -ab 128k -ac 6 -i $DISPLAY out.mpg
```

---

### Post by AlvitrValkyrie on 2011-06-16
> **GWBouge said:**
> You could try using straight ffmpeg and see if you get the same issues.  Here's an example command:

```
# Record Desktop
#    -s Size:            1920x1080
#    -r    Framerate:        30fps
#    -b    Bitrate:        5000 kbits/s
#    -ab    Audio Bitrate:    128 kbits/s
#    -ac    Audio Channels:    6
#    -i    Input:            $DISPLAY (:0.0)
#    Output File:        out.mpg

ffmpeg -s 1920x1080 -r 30 -b 5000k -ab 128k -ac 6 -i $DISPLAY out.mpg
```

What turns up in terminal is a whole bunch of "--enable-______" and then the final line is :0.0: No such file or directory

Confused x.x

---

### Post by GWBouge on 2011-06-17
Oops!  it's missing x11grab.  Try this:

```
ffmpeg -s 1920x1080 -r 30 -b 2000k -ab 128k -ac 6 -f x11grab -i $DISPLAY out.mpg
```

Don't forget you might have to change some of that around to suit your machine, what it can handle and what kind of quality you want, like the bitrates, resolution, audio channels, etc.  If you have two monitors, but you only want to capture the right one, you can adjust the $DISPLAY over some by the width of your left monitor.  I've got 1280x1024 on the left, 1920x1080 on the right, so I'd do:

```
ffmpeg -s 1920x1080 -r 30 -b 2000k -ab 128k -ac 6 -f x11grab -i $DISPLAY+1280,0 out.mpg
```

And sorry for the late reply, got called out not long after I posted that.

---

### Post by AlvitrValkyrie on 2011-06-17
> **GWBouge said:**
> Oops!  it's missing x11grab.  Try this:

```
ffmpeg -s 1920x1080 -r 30 -b 2000k -ab 128k -ac 6 -f x11grab -i $DISPLAY out.mpg
```Don't forget you might have to change some of that around to suit your machine, what it can handle and what kind of quality you want, like the bitrates, resolution, audio channels, etc.  If you have two monitors, but you only want to capture the right one, you can adjust the $DISPLAY over some by the width of your left monitor.  I've got 1280x1024 on the left, 1920x1080 on the right, so I'd do:

```
ffmpeg -s 1920x1080 -r 30 -b 2000k -ab 128k -ac 6 -f x11grab -i $DISPLAY+1280,0 out.mpg
```And sorry for the late reply, got called out not long after I posted that.

Why thank you ^^ That works rather well!
Everything works, but it's just a little laggy. I'm guessing I would increase the bitrate...? From 2000 to like 3000? And how would I change the code to increase the quality just a little bit?

Code for me:
ffmpeg -s 1366x768 -r 30 -b 2000k -ab 128k -ac 6 -f x11grab -i $DISPLAY out.mpg

Thanks a lot.

And I figured out the problems with the screen recorders. It's the encoding. When I set gtk screen recorder to record on the fly, the problems are gone, BUT the recording goes like 4 ties faster than the audio.

---

### Post by GWBouge on 2011-06-17
> **AlvitrValkyrie said:**
> And I figured out the problems with the screen recorders. It's the encoding. When I set gtk screen recorder to record on the fly, the problems are gone, BUT the recording goes like 4 ties faster than the audio.

Ow, yeah, I never would have guessed that, lol.  No clue what to do about the audio/video sync issue, either.

> **AlvitrValkyrie said:**
> Why thank you ^^ That works rather well!
Everything works, but it's just a little laggy. I'm guessing I would increase the bitrate...? From 2000 to like 3000? And how would I change the code to increase the quality just a little bit?

Your welcome  =o)

Simply put, bitrate is quality.  How much data is being pushed per second.  So increase that, you increase quality, but it takes more machine to handle, so it'll likely lag more.  You'll have to play around a bit to get what you want, but you can get some pretty good quality HD video at 2-3000kbps, 1500kbps or so could still manage something worthwhile if you know what you're doing (from what I've seen ... I don't know what I'm doing  XoD ).  At 1366x768, I imagine the 1000 - 2000kbps range should suffice.

You could surely mess around with that command a bit to really better the end result, 'cause in all honesty, I didn't really do many tests, lol.  You could go down to 24fps.  You probably don't need 6 channel audio, if any at all.  You can also play around with different encoding options and codecs to get better quality without raising the bitrate, and see what works best.  Lots more info here:

[http://www.ffmpeg.org/ffmpeg.html#SEC6]("http://www.ffmpeg.org/ffmpeg.html#SEC6")

---

### Post by AlvitrValkyrie on 2011-06-17
> **GWBouge said:**
> Ow, yeah, I never would have guessed that, lol.  No clue what to do about the audio/video sync issue, either.



Your welcome  =o)

Simply put, bitrate is quality.  How much data is being pushed per second.  So increase that, you increase quality, but it takes more machine to handle, so it'll likely lag more.  You'll have to play around a bit to get what you want, but you can get some pretty good quality HD video at 2-3000kbps, 1500kbps or so could still manage something worthwhile if you know what you're doing (from what I've seen ... I don't know what I'm doing  XoD ).  At 1366x768, I imagine the 1000 - 2000kbps range should suffice.

You could surely mess around with that command a bit to really better the end result, 'cause in all honesty, I didn't really do many tests, lol.  You could go down to 24fps.  You probably don't need 6 channel audio, if any at all.  You can also play around with different encoding options and codecs to get better quality without raising the bitrate, and see what works best.  Lots more info here:

[http://www.ffmpeg.org/ffmpeg.html#SEC6](http://www.ffmpeg.org/ffmpeg.html#SEC6)


Aye, thanks a lot. Much appreciated.
Have a good day, good night, or whatever you're about to have.

---

### Post by AlvitrValkyrie on 2011-06-17
> **GWBouge said:**
> Ow, yeah, I never would have guessed that, lol.  No clue what to do about the audio/video sync issue, either.



Your welcome  =o)

Simply put, bitrate is quality.  How much data is being pushed per second.  So increase that, you increase quality, but it takes more machine to handle, so it'll likely lag more.  You'll have to play around a bit to get what you want, but you can get some pretty good quality HD video at 2-3000kbps, 1500kbps or so could still manage something worthwhile if you know what you're doing (from what I've seen ... I don't know what I'm doing  XoD ).  At 1366x768, I imagine the 1000 - 2000kbps range should suffice.

You could surely mess around with that command a bit to really better the end result, 'cause in all honesty, I didn't really do many tests, lol.  You could go down to 24fps.  You probably don't need 6 channel audio, if any at all.  You can also play around with different encoding options and codecs to get better quality without raising the bitrate, and see what works best.  Lots more info here:

[http://www.ffmpeg.org/ffmpeg.html#SEC6](http://www.ffmpeg.org/ffmpeg.html#SEC6)

One more issue.
Sound not recording o;

---

### Post by mike555 on 2011-06-17
Kazam Screencaster works for me .........

---

### Post by GWBouge on 2011-06-17
Hmm ... you might have to add something like '-i pulse -f alsa' in there before the output file.  I'm fairly positive the first command I posted worked before (probably 10.04 last I used it), but I guess whatever's going on now needs you to specify what and how.  I can pretty much guarantee you my sound setup is quite different than yours, so I dunno how much help I'mma be there, but there seems to be others with the same problem:

[http://www.google.com/search?q=ffmpeg+no+sound+with+x11grab]("http://www.google.com/search?q=ffmpeg+no+sound+with+x11grab")

---

