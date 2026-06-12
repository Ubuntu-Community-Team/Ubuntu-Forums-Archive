---
title: "Karmic - music players and iPod support"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-11-03
Hey everyone,

Since upgrading to 9.10 from Jaunty, I've noticed that my iPod won't show up in many media players. 

I tried Banshee, Songbird, and Amarok, with no success. The only player it would show up in was Rhythmbox.

Does this have something to do with not using HAL anymore?

---

### Post by swiftsam on 2009-11-03
I am experiencing the same thing.  I am trying to switch over to Banshee because Rhythmbox was getting on my nerves, but I can't get it to show up.  I even added the Banshee ppa, but there are no updates (last build was 3 weeks ago).

Anyone have an idea of what we can test to see where the problem is?

---

### Post by unamanic on 2009-11-03
I don't have an ipod, but the OP is probably right about the switch from HAL to device kit.  try adding a .is_audio_player file to the device's root.  You may need to set parameters in the file to get it to work properly.

---

### Post by swiftsam on 2009-11-03
Thanks for that idea.  I'm not having luck with it right off the bat.  

I don't see any particularly recent discussion about this with reference to ipods and banshee, but I tried out these instructions

[http://act1v8.wordpress.com/2007/10/07/make-banshee-recognize-your-mass-storage-device-as-a-dap/](http://act1v8.wordpress.com/2007/10/07/make-banshee-recognize-your-mass-storage-device-as-a-dap/)

but using the ipod folder structure ...

```
audio_folders=iPod_Control/Music/
folder_depth=2
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg
```

Banshee still doesn't see it.

---

### Post by synicalx on 2009-11-03
I've been having iPod trouble on 9.04 myself, music players seem to not like my 2G touch?

I tried my mates Jailbroken touch (same model and all) and that showed up just fine, maybe it's Apples fault? :P

---

### Post by jimmy the saint on 2009-11-03
> **unamanic said:**
> I don't have an ipod, but the OP is probably right about the switch from HAL to device kit.  try adding a .is_audio_player file to the device's root.  You may need to set parameters in the file to get it to work properly.

That file may make some software recognize the device, but most ipods are encrypted (unless they are very old) so it is unlikely that that file would help in this case.  

Have you checked out this site?
[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)

---

### Post by atleastzero on 2009-11-15
> **jimmy the saint said:**
> Have you checked out this site?
[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)
 
Has anyone tried this? I will give it a shot after work and post back with results.

---

### Post by RJ12 on 2009-11-15
> **synicalx said:**
> I've been having iPod trouble on 9.04 myself, music players seem to not like my 2G touch?

I tried my mates Jailbroken touch (same model and all) and that showed up just fine, maybe it's Apples fault? :P

Thats because apple changed something in The 2G for iPod/iPhone so they have to be jailbroken to work on Ubuntu "AKA Non apple software" (Good job apple now you will have a lot of users jailbreaking not a good marketing strategie!);)

---

