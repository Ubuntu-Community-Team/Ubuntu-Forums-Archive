---
title: "Panel Heart Attack"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Don'tKnowWhatI'mDoing on 2010-01-10
Help Please!
I am fairly new to Ubuntu, my brother gave me his old computer which had it installed. I bought a new hard drive and did a fresh install. I'm running Karmic 9.10, set p AWN and compiz, I even got nvidia to do dual monitors, separate x screens just like I had before the fresh install. But my problem is this: after setting the separate x screens up I reset the computer, as it had asked, and now my gnome panels are freaking out. The are flashing on and off, I only have access for a little less than two seconds. Also same with alt+F2. So... I'd love to be able to use my computer without getting a headache again,
Thanks all that help!
pharaoh(Don'tKnowWhatI'mDoing)

---

### Post by goiggles on 2010-01-10
lets try and kill replace compfiz with metacity as the window manager
```
metacity --replace &
```

if that doesn't work you can use compfiz again by
```
compiz --replace &
```

I take it that you may be having trouble starting any apps since alt+F2 disappears as well. try and see if alt+f1 will keep the application window up long enough to get to a terminal.

---

### Post by Don'tKnowWhatI'mDoing on 2010-01-10
Ah, well I'd rather not replace compiz with metacity. Then I couldn't use AWN or Tilda, which is what I usually use for a terminal, it just looks nicer. Also, I just restarted with only one monitor plugged in, and no problems.

---

### Post by Don'tKnowWhatI'mDoing on 2010-01-10
Any new ideas on what the problem is? I'm hoping it isn't with compiz, it's half of the reasons I like using Ubuntu.

---

### Post by goiggles on 2010-01-10
well do you have compfiz on the normal setting and not the advanced? that will still let you run awn and i assume tilda as well.

---

### Post by Don'tKnowWhatI'mDoing on 2010-01-10
It's set to normal in animations and default just about anywhere else. It needs the transparency for those two. As soon as I put in either
 	Code:
 	metacity --replace & 
or
Code: 	compiz --replace & 
both AWN and Tilda decide they don't want to work anymore. Haha.
Good times, right? 
And thanks, as always.

---

### Post by goiggles on 2010-01-10
well its apparently very difficult to get compfiz and dual monitors setup.

[http://ubuntuforums.org/showthread.php?t=884161&highlight=compiz+dual+monitors](http://ubuntuforums.org/showthread.php?t=884161&highlight=compiz+dual+monitors)

now i don't have time to run through it all but towards the end of the thread theres people who make adjustments for 9.10. It looks quite complicated so good luck. try and see if those guys can help you through it.

---

### Post by Don'tKnowWhatI'mDoing on 2010-01-10
Oh, thanks, this looks promising. It didn't seem so hard last time, I got it running just fine, I might hook up that old hard drive and look into some of the settings on that thing.

Thanks again,
pharaoh (Don'tKnowWhatI'mDoing)

---

