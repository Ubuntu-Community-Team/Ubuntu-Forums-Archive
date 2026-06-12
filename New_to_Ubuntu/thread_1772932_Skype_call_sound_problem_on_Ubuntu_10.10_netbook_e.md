---
title: "Skype call sound problem on Ubuntu 10.10 netbook edition on HP Mini 110-301dx"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by iamchichi on 2011-06-01
Hello! 

So happy to have converted my friend to use ubuntu on her netbook. ^_^ 

We just got her HP Mini 110-301dx finally running on ubuntu 10.10 netbook edition- went well. 

Then installed and ran skype cuz it's just awesome, 

but then when I called her she sounded like there's a helicopter getting ready for take-off behind her. 


I read a few forum posts which I couldn't get much out of cuz I don't really understand. Is there a workaround to fix this? 

Is this a slow processor problem ? Memory? .... ?

---

### Post by frankbooth on 2011-06-01
This is most likely due to the microphone, try fiddling with the settings by launching a terminal and type:
```

alsamixer

```
Then press F4, use the arrowkeys to navigate and increase/decrease volume. 

Also try with an external microphone and see if there's any difference.

---

### Post by iamchichi on 2011-06-01
> **frankbooth said:**
> This is most likely due to the microphone, try fiddling with the settings by launching a terminal and type:
```

alsamixer

```
Then press F4, use the arrowkeys to navigate and increase/decrease volume. 

Also try with an external microphone and see if there's any difference.

Thanks for the reply.  ooooh! That's a different Alsa Mixer thanks thanks! Checked and tried it. 

Awesome! Thanks thanks!

---

### Post by iamchichi on 2011-06-01
Also... that particular HP Mini does not have a mic jack, just an earphone jack. The only mic that can be used is the built in one next to the camera. 

this HP Mini sucks >..< 


^^;;

---

### Post by iamchichi on 2011-06-21
solved by launching terminal and turning off mic boost and lowering the mic capture :D:D:D

thanks for the reply sir.

---

