---
title: "How to play FULLSCREEN videos in console?"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Miter_J on 2010-12-18
It took me so much time that I finally made it to play videos in the console.
The command is "sudo mplayer -vo fbdev test.avi"
But I could not make it full-screened, even I put the parameter "-fs" after it.
The only difference that "-fs" took is only that it put the display screen from the the left-up corner to the center, but it's still not full-screened.
Someone please help me out.:cry:

---

### Post by andrew.46 on 2010-12-18
Perhaps something like the following:

```
mplayer -vo fbdev -screenw 800 -screenh 600 -geometry 50%:50% test.avi
```

adjusting width and height to your preferences, this should play the video in the centre of the screen perhaps use *-fs* for fullscreen as well, I have not tested this. This works with the svn MPlayer, not sure about older versions...

Andrew

---

### Post by Miter_J on 2010-12-18
Sorry guy, I've tryed what you said but nothing changed.
The video is still in the center and the size is still small.
Why is this so hard in console but seems very easy in the GUI since we can simply double click the window and accomplish it?

---

### Post by andrew.46 on 2010-12-18
Perhaps something like the following:

```

mplayer -vo fbdev -screenw 800 -screenh 600 -geometry 50%:50% -zoom -fs test.avi

```

Andrew

---

### Post by Miter_J on 2010-12-18
> **andrew.46 said:**
> Perhaps something like the following:

```

mplayer -vo fbdev -screenw 800 -screenh 600 -geometry 50%:50% -zoom -fs test.avi

```

Andrew
- -Still not work...
Does this work on your computer?
Nothing changed here.

---

### Post by andrew.46 on 2010-12-19
Hi Miter,

> **Miter_J said:**
> Does this work on your computer?

A very pertinent question :). I am between Ubuntu installations at the moment but on my Slackware setup I have a 640 x 480 framebuffer set in Lilo, and I can achieve full screen display with the following slight variation of the syntax I have suggested to you:

```

mplayer -vo fbdev -screenw 640 -screenh 480 -zoom -fs -xy 640 test.avi

```

Easier results can be achieved with *-vo svga* which might be worth trying as well... I shall experiment with higher resolutions on the framebuffer settings on my system just for curiosity 

Andrew

**Edit:** Well I set the framebuffer to 800x600x32k (in Lilo this is done simply with *vga=788* ) and the following syntax then produced full screen with correct aspect ratio:

```

mplayer -vo fbdev -screenw 800 -screenh 600 -zoom -fs -xy 800 test.avi

```

It is a little cumbersome but works well enough, I note that fbdev2 gives a better result though...

---

### Post by Miter_J on 2010-12-19
Wow!~ That's so nice of you!
-xy 1280(the width of your resolution, mine is 1280. More than 1280 will bring out an error.) will make it full screen.
Thank you so much~

---

### Post by Miter_J on 2010-12-19
PS, the -screenh and the -screenw are not necessary though.
```
mplayer -vo fbdev -xy 1280 -fs -zoom test.avi 
```
will perfectly achieve my goal

---

### Post by MooPi on 2010-12-19
Have you tried ```
mplayer -aspect 16:9 -fs test.avi
```
I change the aspect to get full/full screen
Possible ratios to use for smaller screens, 1:1, 4:3, 3:2, and finally 16:9,

---

### Post by Miter_J on 2010-12-19
I just tried. It doesn't work.
Now the only way to get full screen for me is what I said above.
Are you in console?
In terminal, your command is ok.

---

### Post by MooPi on 2010-12-19
> **Miter_J said:**
> I just tried. It doesn't work.
Now the only way to get full screen for me is what I said above.
Are you in console?
In terminal, your command is ok.

Terminal, I don't use the console, and find the terminal easier to configure. Sorry for the confusion.

---

### Post by andrew.46 on 2010-12-19
Hi Miter_J,

> **Miter_J said:**
> PS, the -screenh and the -screenw are not necessary though.
```
mplayer -vo fbdev -xy 1280 -fs -zoom test.avi 
```
will perfectly achieve my goal

Glad that you have achieved your goal :). Indeed you are perfectly correct, it seems that *-screenh* and *-screenw* are not necessary which I will admit has caught me by surprise. In theory it is necessary to use these as fbdev is not aware of the screen dimensions but following your suggestion I tested without these and there was no difference. You learn something new every day :).

Andrew

---

### Post by Miter_J on 2010-12-19
That's really great to have such a nice mate like you.
Thank you, Andrew.

---

### Post by Miter_J on 2010-12-19
Nothing to be sorry about.
I just find text-only environment very charming, so I tried to be only in the console.
Thank you though, for your kindness~

---

### Post by Miter_J on 2010-12-19
Oh, my English seems to be very poor.
Should I say "sorry for" instead of "sorry about"?
What a naive mistake...

---

