---
title: "Help with streaming needed! BCCi and 4oD mostly"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by Jenferd on 2010-08-29
I am a complete noob with Ubuntu! last week the HD on this laptop died, I yelled at a friend to bring me another which he did, my Win 7 disk would not install, I trod on my XP disk so thought ho hum now is the time to try... well it all went quite well aside from the fact I've found the graphics card on this laptop doesn't work so well in this version of Ubuntu 9.10... card is ATI mobility Radeon 9200! streaming hardly worked at all until I rooted through a lot of posts and figured to go to Appearance>Visual effects and check none and it was loads better...

Now BBCi and 4oD kind of work but sometimes get a really bad lag, the visual will stall on a frame and I get two lots of audio, on BBCi I've figured if I hit pause then delete history, then hit play it behaves again but the more I do it the sooner it lags again... on 4oD it does the same but have noticed it does it less if you do the pop out player and close the main window but that's a pain in the doodah when it does get stuck...

Trying to figure how much of it is down to my card not working well with Ubuntu and how much is down to BBC and Channel 4 not implementing stuff &&& anything else that might effect it???

Streaming worked great with Win 7 on wireless, the Toshi running XP works great on wireless too... have hard wired this laptop and still have the same problem!

I would love to stay with Ubuntu and possibly put it on the Toshi as really like it but the laptops are used for streaming from these two sites a LOT so...

any help would be appreciated... I'm comfortable with using the terminal as long as someone explains what I'm typing is doing :0)

EDIT-ADD: Browser is FF, flash etc is all newest version, flash works fine for everything but streaming....

---

### Post by blazemore on 2010-08-29
Yes it's easier to fix this in the terminal.

The problem is that the flash player is trying to use your laptop's integrated Intel graphics to accelerate the video. Unfortunately, the state of Intel's graphics drivers on Linux is a bit of a sore spot in the community at the moment.

You can tell Flash not to do this by firing up a terminal and issuing the following commands:


```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" | sudo tee -a /etc/adobe/mms.cfg
```

Restart any web browsers and try again.
This certainly won't hurt performance, but if it does, do this to undo the changes:
```
sudo mv /etc/adobe/mms.cfg /etc/adobe/mms.cfg.old
```

---

### Post by Jenferd on 2010-08-30
Thank you so much Blazemore, I am right at the end of an episode of Heir Hunters on BBCi and have had no problems with streaming at all :o 
 
One of the girls will try something on 4oD but it looks promising... my girls are happy bunnies, thanks again :)

---

