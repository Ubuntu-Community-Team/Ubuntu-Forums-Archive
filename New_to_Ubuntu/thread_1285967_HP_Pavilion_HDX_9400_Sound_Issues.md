---
title: "HP Pavilion HDX 9400 Sound Issues"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by BT1 on 2009-10-08
I thought this might be a good place to post this issue since I have some experience with Ubuntu but not enough to call myself a novice. I've had no problem with ubuntu on my other laptops (Two dell inspirons, a toshiba, acer netbook) but my "big bessie" (huge screen, big weight) entertainment laptop just can't manage to get sound out of Ubuntu 9.04. I'm asking about 9.04 because while I understand that 9.10 is just around the corner, I bought a couple of books that are teaching me to work with Ubuntu 9.04 from the ground up. So I need a little expertise in this realm.


Again,


-Sound does not play while using Ubuntu 9.04 on a HP Pavilion HDX 9400 series laptop.

Thanks for any assistance!

---

### Post by swoody on 2009-10-08
Right-click on the sound icon in the top-right of your screen, and change your sound settings. You may need to add PCM to the visable ones, so you can control that as well. Just make sure they're both unmuted, and turned up a bit - you can turn PCM all the way up to 100%. Try that out, and let us know if it works for you or not :)

---

### Post by BT1 on 2009-10-08
No good. ;(

I had tried this before hand in previous attempts and went back to check and see if anything was updated *shrug*. I opened all the boxes, viewed all the options, played with all of the sliders, and it's still in mute mode. The icon at top right does not show a mute sign, nor do any of the sliders. I think it may be an issue with the sound card being recognised?

Helllp!

---

### Post by BT1 on 2009-10-08
;( Come on you shhhhnazzy gurus! All I need to complete the transition is SOUND lol. That's it. Until then I'm forced to watch movies and listen to audio on windows. :(

Help!

---

### Post by BT1 on 2009-10-09
*shameless bump

Hey I wouldn't unless I was disparate lol. I'm more than likely going to have to go back to windows until I can get this figured out through scanning the forums and checking on my thread. Please help! :(

---

### Post by swoody on 2009-10-12
Just to verify it, in a terminal I would run:
```
alsamixer
```
Then in the alsa mixer window, use your arrow buttons and the 'M' button to make sure the volumes are up, and none of the options are muted.

If this still doesn't work, hopefully someone with more in-depth audio knowledge can pitch in here :)

---

### Post by BT1 on 2009-11-19
This issue is still unsolved.

Headphones work, speakers don't.

Help!

---

