---
title: "youtube full screen freezes videos"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by sallam on 2010-10-29
Greetings

Whenever I click the full screen button in any Youtube's video, only the audio is played, and the video freezes and do not advance until I go back to normal size.
I'm using ubuntu 10.10 and Firefox 4 b6.
did anyone encounter such problem?
Is there a fix?

Many thanks.

---

### Post by Omnomnom on 2010-10-29
Well first of all, I'd recommend checking for updates to adobe flash. Apart from that, wait a while for the video to buffer as well, because sometimes full screen can up the quality, and try clicking the actual video with your mouse to make sure it isn't paused. It also might be your CPU being slow, personally the only time youtube freezed ever for me is when I'm booted into windows, or when I'm capped.

---

### Post by gandaran on 2010-10-29
> **sallam said:**
> Greetings

Whenever I click the full screen button in any Youtube's video, only the audio is played, and the video freezes and do not advance until I go back to normal size.
I'm using ubuntu 10.10 and Firefox 4 b6.
did anyone encounter such problem?
Is there a fix?

Many thanks.
disable the hardware acceleration in flash settings (right click the flash video window) this fixes the issue of fullscreen flash on computers that do not support hardware acceleration

---

### Post by Omnomnom on 2010-10-29
Ah yes, I forgot to mention that at the start too. Hope we helped :P

---

### Post by rfugger on 2010-11-01
I'm having the same problem.  It is definitely *not* just that the video is slower full-screen.  It used to work fine in lucid, but is broken on maverick.  Actually, it works about 10-20% of the time, but fails the other 80-90%.  When it is frozen, the progress bar is also frozen, and the buttons work, but don't change appearance at all.

Disabling hardware acceleration doesn't fix it.

This seems to be just youtube as other flash video plays fullscreen OK.

---

### Post by rfugger on 2010-11-01
See also this thread for a possible fix:

[http://art.ubuntuforums.org/showthread.php?t=1593274&page=2](http://art.ubuntuforums.org/showthread.php?t=1593274&page=2)

---

### Post by balloooza on 2010-11-01
My fix:
if you get the problem: 
1)Go out of fullscreen mode (esc)
2)Scroll up and down on the page
3)Go to fullscreen again
4)If Problem still exists go to step one, else enjoy video.

I know it is silly, but frankly, it does not bother me. For the record, it happens to me in all browsers, and with almost any flash player, not just youtube. I originally though Apples stand against flash was all politics, about keeping control in the hands of Apple, not adobe. Behind all that corporate whatever you want to call it, I can see a truth to just using Open source standards, despite my feelings towards apple.

---

### Post by jonchamberlain on 2011-03-28
The solution that worked for me was to install a Firefox add-in called 'Flash_aid', which I found on the forum here:
[http://ubuntuforums.org/showthread.php?t=1593274&page=2]("http://ubuntuforums.org/showthread.php?t=1593274&page=2")

YMMV, but I am now a happy camper!

---

