---
title: "No menus or desktop when I boot, just wallpaper"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by dban420 on 2011-02-23
Hey there guys. 

Installed ubuntu 10.10 last night, dual boot with XP. It was working great, I had most of my drivers installed and was really digging it, surfing the web, watching video etc. Went to bed around 12 after goofing around with it for about 3 hours or so. Got up this morning and went to boot it, but it doesn't boot all the way. What comes up is really just the desktop "wallpaper", with no dropdownmenus or desktop icons. 

Any ideas?

---

### Post by sikander3786 on 2011-02-23
Welcome to the forums :-)

Can you please post the hardware specs of the machine in question.

And do another thing. When you are on the desktop, press Alt + F2 and type,

```
killall gnome-panel
```

Hit <Enter> and see if the panels come up.

---

### Post by dban420 on 2011-02-23
> **sikander3786 said:**
> Welcome to the forums :-)

Can you please post the hardware specs of the machine in question.

And do another thing. When you are on the desktop, press Alt + F2 and type,

```
killall gnome-panel
```Hit <Enter> and see if the panels come up.

Thanks for the welcome!

It's a Gateway with a pentium 4, and 512MB of Ram. Pathetic I know, but it's enough to do most of what I want out of this particular machine. Trying your suggestion now.

---

### Post by dban420 on 2011-02-23
ok panels popped up. thanks man. Any ideas on how to not have to do that each time?

---

### Post by Rex Bouwense on 2011-02-23
Got two ideas.  First, you may have selected auto hide for your panels.  Simply move the curser where the top panel should be and it should appear.  Right click the panel and select properties and remove the check mark by auto hide.  Second, the pixel size may be set to zero.  You can change that in the same area.

---

### Post by dban420 on 2011-02-23
> **Rex Bouwense said:**
> Got two ideas.  First, you may have selected auto hide for your panels.  Simply move the curser where the top panel should be and it should appear.  Right click the panel and select properties and remove the check mark by auto hide.  Second, the pixel size may be set to zero.  You can change that in the same area.

Thanks man, it definitely wasn't that though. I tried moving the mouse all over the screen.

---

### Post by sikander3786 on 2011-02-23
> **dban420 said:**
> ok panels popped up. thanks man. Any ideas on how to not have to do that each time?
So, once on the Desktop, can you please post the output of this command from Applications > Accessories > Terminal;

```
free -m
```

And this might sound strange but one of my friends had the same problem a few days back with his Ubuntu Lucid. The panels didn't pop up at login and the underlying problem was a damaged USB printer cable. I couldn't figure out how that was related to panels but it really was.

---

### Post by dban420 on 2011-02-23
> **sikander3786 said:**
> So, once on the Desktop, can you please post the output of this command from Applications > Accessories > Terminal;

```
free -m
```And this might sound strange but one of my friends had the same problem a few days back with his Ubuntu Lucid. The panels didn't pop up at login and the underlying problem was a damaged USB printer cable. I couldn't figure out how that was related to panels but it really was.


Should be a screenshot attached

---

### Post by dban420 on 2011-02-23
lol let me know if yoiu can read that or not

I'm using a tv as a monitor with S video. can barely read my typing

---

### Post by sikander3786 on 2011-02-23
Yes I can read that output. You are not running out of memory and thats ok.

So, did you try a reboot and see if panels are loading automatically now?

---

### Post by dban420 on 2011-02-23
I'll try that now. Brought my laptop over so I cab see better

---

### Post by dban420 on 2011-02-23
yay!! it booted up fine! I better write that command down just in case though.

I've gotta say, I am very impressed with this OS. I think I'm gonna put it on my laptop too.

I want to run compiz-fuzion but I think that's out of the question on this older desktop.

I want to get a new mother board and CPU for it, but I'm a broke *** student

---

### Post by sikander3786 on 2011-02-23
Yes you might consider adding some RAM as that will really speed up your whole OS. Compiz eats some memory and requires a better graphics card. If you can put in an extra 512 MB of RAM and a decent (not the best) NVIDIA or ATI graphics card, you can get your hand on compiz as well.

Hope you enjoy your stay with Ubuntu!

---

### Post by dban420 on 2011-02-23
> **sikander3786 said:**
> Yes you might consider adding some RAM as that will really speed up your whole OS. Compiz eats some memory and requires a better graphics card. If you can put in an extra 512 MB of RAM and a decent (not the best) NVIDIA or ATI graphics card, you can get your hand on compiz as well.

Hope you enjoy your stay with Ubuntu!

I thought about adding RAM, but I'll still be stuck with the pentium 4. I'm gonna wait till I have enough to upgrade the whole thing

---

