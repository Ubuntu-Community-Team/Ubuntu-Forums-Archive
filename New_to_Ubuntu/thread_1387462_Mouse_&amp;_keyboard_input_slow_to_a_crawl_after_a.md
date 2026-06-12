---
title: "Mouse &amp; keyboard input slow to a crawl after any hi-speed download"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by abben on 2010-01-21
I have just re-install ubuntu 9.04.

At first I mistakenly thought this problem was the fault of the torrent program transmission. I would download a large file (anything over 100 mb). If the download was "fast" (by my standards at least, which is over 500kb/sec) and fast for some sustained amount of time (around 5 to 10 minutes), things would slow to a crawl.

If a download went fast for a sustained amount of time, the frame rate for the mouse would move at about 4 fps, and without fully responding to mouse movement. The keyboard input would be slow as well. Input wasn't merely delayed, it would miss typed keys altogether. If I tried to type 'hello' it might type 'hlo'. 

What really threw me for a loop was that any download, from any browser program or any torrent program, or from wget it would slow.

And, earlier today when I was installing debian on this same computer- the same thing happened when I was downloading kdm and kde *through the console*. Keyboard input slowed to a crawl before I even had any graphical stuff running.

All this together in handy bullet form:

correlations:
[LIST]
[*]'fast' download (over roughly 500k a second)
[*]download remains fast for some sustained amount of time (perhaps 5-10 minutes continuous)
[*]regardless of the program
[*]I am 99.999% sure it is not a hardware issue. This didn't happen to me with old versions of ubuntu (such as edgy).
[*]I am 99.999% sure that the behavior is prompted by a large, fast download and not something else
[/LIST]

effects:
[LIST]
[*]greatly slowed keyboard/mouse input
[*]remains slow for the rest of the session even after download is finished.
[*]does not seem to be CPU usage or memory shortage problem (video & audio are not slowed)
[*]Things are back to normal after a restart.
[/LIST]

Any thoughts are greatly appreciated.

---

### Post by ikt on 2010-01-22
> **abben said:**
> Any thoughts are greatly appreciated.

Heya, great post, about as good as one can get on a very strange issue.

All I can suggest is have you tried another mouse and keyboard? Possibly seeing the difference between a usb mouse and a ps/2 mouse etc.

---

### Post by abben on 2010-01-24
I just wanted to update and see if anyone has heard about this.

Someone else had the same problem [here]("http://ubuntuforums.org/showthread.php?t=1306501&highlight=transmission+slow+mouse+keyboard"), thinking it was the fault of transmission.

In that thread they mistakenly thought it was a wireless connection problem (its not, I have the same issue and I'm wired to a LAN).

Any thoughts. Also, I've never filed a bug report before. Is my problem even specific enough that I *could* file one?

---

### Post by abben on 2010-01-24
> **ikt said:**
> Heya, great post, about as good as one can get on a very strange issue.

All I can suggest is have you tried another mouse and keyboard? Possibly seeing the difference between a usb mouse and a ps/2 mouse etc.

I know I've used a different mouse before, and I think a long time ago in the past I used a different keyboard can my memory isn't clear enough. I'll switch out the keyboard and see what happens. Though I'm not sure how the keyboard would know when I'm downloading large files at a fast speed.

---

### Post by ikt on 2010-01-26
> **abben said:**
> I know I've used a different mouse before, and I think a long time ago in the past I used a different keyboard can my memory isn't clear enough. I'll switch out the keyboard and see what happens. Though I'm not sure how the keyboard would know when I'm downloading large files at a fast speed.

Any results?

I'm actually quite interested in what it could be.

On the more extreme end if you've got time to, are you able to setup ubuntu 10.04, maybe on a separate hard drive or partition and see if it still is effected.

---

