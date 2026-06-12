---
title: "Screen doesn't look good, fuzzy etc."
date: 2009-02-23
forum: New to Ubuntu
---

### Post by iball8888 on 2009-02-23
[http://i66.photobucket.com/albums/h274/Iball2/snapshot1.png](http://i66.photobucket.com/albums/h274/Iball2/snapshot1.png)

That is what my desktop looks like, i don't know if its the same for me as it is for you, but the text is a little blurry almost like it has its own shadow.  Also when i look at pics its not good quality.  MY resolution is 1440x900 that is recommended on the stickers of my 17' Gateway LCD Monitor.

Also i activated my Nvidia 177 drivers but not my 173, does it make a difference?

Any suggestions?

---

### Post by Temposs on 2009-02-23
1) You can only have one nVidia driver activated at a time.

2) Go to System->Preferences->Screen Resolution and see what it says your resolution is. If it's lower than 1440x900, try to increase it.

---

### Post by iball8888 on 2009-02-23
I just said my res is 1440x900 >.>

idk what else is wrong:(

It also says my color depth is 24.  I also have 16, and 8.  Is 24 good or shouldn't there be a 32?

---

### Post by HavocXphere on 2009-02-23
You can try setting/disabling anti-aliasing fonts option under sys settings, appearance, fonts.

The screenshot looks fine to me...

Be sure to use a DVI cable for the screen.

---

### Post by overdrank on 2009-02-23
> **iball8888 said:**
> I just said my res is 1440x900 >.>

idk what else is wrong:(

It also says my color depth is 24.  I also have 16, and 8.  Is 24 good or shouldn't there be a 32?

You may also try adjusting in the nvidia-settings ```
kdesu nvidia-settings
```
Almost did not catch you are using kde. ;)

---

### Post by Berzzan on 2009-02-23
iball8888: I think I have the exact same problem as you. Although I am running on my laptop display (15.4") 1440x900@60, and the fuzzieness just eats my eyeballs out of their sockets! Have to give up Ubuntu if I can't fix this... If I find I way to fix this I tell you and I hope you tell me if you do =)

Cheers!

AAH! At least I fixed my problem by turning 'Bicubic filter' OFF in the CompizConfig!

---

