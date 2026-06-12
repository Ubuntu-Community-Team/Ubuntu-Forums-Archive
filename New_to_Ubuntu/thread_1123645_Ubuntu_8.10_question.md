---
title: "Ubuntu 8.10 question"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by hiloguy on 2009-04-12
I just did a clean install of 8.10.  Way better than the 6.10 I was using!  All hardware, including wifi was identified and working immediately!  But here's the question:  That slick little box in the lower right corner that lets you flip back and forth between apps is great in concept but it drives me nuts when I can't move my cursor across the desktop without the windows gliding back and forth on their own, usually to the one I am NOT working on.  Is this a common issue?  Is there a fix?

Thank you!

---

### Post by tom56 on 2009-04-12
> **hiloguy said:**
> I just did a clean install of 8.10.  Way better than the 6.10 I was using!  All hardware, including wifi was identified and working immediately!  But here's the question:  That slick little box in the lower right corner that lets you flip back and forth between apps is great in concept but it drives me nuts when I can't move my cursor across the desktop without the windows gliding back and forth on their own, usually to the one I am NOT working on.  Is this a common issue?  Is there a fix?

Thank you!

When you say moving the cursor do you mean the scroll wheel? If so you need to install the following program and then follow the instruction in the linked thread.
```
sudo apt-get install compizconfig-settings-manager
```
[http://ubuntuforums.org/showthread.php?t=921020](http://ubuntuforums.org/showthread.php?t=921020)

---

### Post by hiloguy on 2009-04-12
> **tom56 said:**
> When you say moving the cursor do you mean the scroll wheel? If so you need to install the following program and then follow the instruction in the linked thread.
```
sudo apt-get install compizconfig-settings-manager
```
[http://ubuntuforums.org/showthread.php?t=921020](http://ubuntuforums.org/showthread.php?t=921020)

Nope, that's not it.  When I have an open app that is not full screen, whenever my mouse goes across the desktop portion of the display, the display will glide over to the other end and then the only way I can get it back is to click on the icon (lower right corner) again. Even then, as soon as my cursor leaves the icon and goes back across the brown desktop, it will switch over to the other screen again. Not always, just most of the time. It's frustrating enough  that I'm tempted to disable the otherwise very useful screen-switch thing.

---

### Post by hyper_ch on 2009-04-12
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by lavinog on 2009-04-12
> **hiloguy said:**
> Nope, that's not it.  When I have an open app that is not full screen, whenever my mouse goes across the desktop portion of the display, the display will glide over to the other end and then the only way I can get it back is to click on the icon (lower right corner) again. Even then, as soon as my cursor leaves the icon and goes back across the brown desktop, it will switch over to the other screen again. Not always, just most of the time. It's frustrating enough  that I'm tempted to disable the otherwise very useful screen-switch thing.
What you are describing sounds like the desktop effects. Go to System>Preferences>apperance>Visual effects and select none.
If you would like to keep the desktop effects, but dissable that one feature you have to install the compizconfig-settings-manager as mentioned before

---

