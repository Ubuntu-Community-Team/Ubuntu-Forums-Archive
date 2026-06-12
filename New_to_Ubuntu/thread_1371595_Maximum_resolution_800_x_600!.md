---
title: "Maximum resolution 800 x 600!"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Stovey on 2010-01-03
System => Preferences => Display only gives me three options, the maximum is 800x600.

I'd like to change the display resolution, because the bottom of the screen seems cut-off sometimes.

Would someone please help solve this?  Thanks!

I'm on an Acer Aspire One AOA150, and I installed Ubuntu 9.10 last week.

---

### Post by mikewhatever on 2010-01-03
So, what happened since last week, or has it been like that from the start?

---

### Post by Stovey on 2010-01-03
Yeah, it's been like this since the very start.  I was just happy that mostly everything was working.  But I can't live with the bottom of the screen missing any longer!

I tried making a video clip with "Cheese" - but it didn't work, the video was choppy and not synced to audio.  So when I installed "Kino" the short screen prompted me to post here.  It looks like this:

[img]http://i128.photobucket.com/albums/p195/BassBucket/Screenshot_Kino.png?t=1262555017[/img]

---

### Post by RedSingularity on 2010-01-03
What does your xorg file look like?

---

### Post by corncob on 2010-01-03
It happens to me sometimes too, only its been the top of the screen that's cut off.  What I found that I need to do to fix it is reboot (turn off and back on) the monitor (actually an HDTV).
Possibly 800x600 is all the resolution your monitor will support?

---

### Post by Stovey on 2010-01-03
> **RedSingularity said:**
> What does your xorg file look like?

I don't have an xorg file.

My monitor supports 1024 x ???.

---

### Post by Stovey on 2010-01-03
OK, I got this figured out, with the help of other threads.  I created a xorg file with this:

$ sudo dpkg-reconfigure -phigh xserver-xorg

And then I typed this which I don't know if it was necessary or not:

sudo xorg -configure

And after restarting, the display preferences allowed me to adjust the screens properly for both the laptop and the monitor.  You guys are the BEST!!

Now my screen looks waaaaay better, like this:

[IMG]http://i128.photobucket.com/albums/p195/BassBucket/Newsettings.png?t=1262561596[/IMG]

---

