---
title: "Making suspend work?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by amsgwp on 2009-05-07
Soo..it goes into suspend when I close the lid on my laptop but won't come out.  I believe I've always had this issue.

What guides are available for fixing this?

I'm using a Asus W7J if that helps.

---

### Post by ssdt on 2009-05-07
There are some problems with suspend in some computer with AMD but I haven;'t faced any with Intel.

---

### Post by durand on 2009-05-07
You could go to the power settings and disable suspend when you close your lid until you find your solution. What happens if you press the power button?

---

### Post by amsgwp on 2009-05-07
Well by default suspend was disabled but I enabled it and it goes into suspend fine (power light starts blinking) but when I click power button to come out of suspend the power light stops blinking but it never comes back to life.

I saw something about wireless drivers being the problem.  How can I check this?

I have a intel proset wireless 3945abg wireless card.  Also this is a intel processor laptop, not AMD.

---

### Post by SaaTeeVaaGreen on 2009-05-07
Which ubuntu release are you using? i had exactly this problem when i was using hardy heron but since i have upgraded to jaunty my laptop resumes from suspend perfectly every time.

---

### Post by amsgwp on 2009-05-07
Jaunty.

I jsut got it to work if I disabled my wireless card.

but once I resumed the wireless wouldn't come back on (I used hardware switch to disable and re-enable).

So can anyone help me figure that out.  Is it possible to automatically disable on suspend and re-enable on wake?

---

### Post by zero7404 on 2009-05-07
i had this problem with mine, the display would not wake up upon resume....had to restart system when that happens.

i am not sure if you're running ATI video hardware in that laptop, maybe you might want to look into download and manual install of the latest linux version....

for mine, i had a choice of the 177 or 180 nvidia restricted drivers and still experienced the problem. so i went to nvidia's site to get their latest package and installed that. so far no issues....

---

### Post by durand on 2009-05-07
> **amsgwp said:**
> Jaunty.

I jsut got it to work if I disabled my wireless card.

but once I resumed the wireless wouldn't come back on (I used hardware switch to disable and re-enable).

So can anyone help me figure that out.  Is it possible to automatically disable on suspend and re-enable on wake?

Yes, it is possible.. There is a config file in /etc but I can't remember what it is. Sorry..

---

### Post by zero7404 on 2009-05-08
scratch my previous statement, i'm experiencing this problem again. 
this thread over @ nv points to the fact that there is no solution yet....
[http://www.nvnews.net/vbulletin/showthread.php?t=109199&highlight=resume+display+blank](http://www.nvnews.net/vbulletin/showthread.php?t=109199&highlight=resume+display+blank)

---

