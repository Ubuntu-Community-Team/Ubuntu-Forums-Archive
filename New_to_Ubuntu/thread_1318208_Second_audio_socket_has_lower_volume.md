---
title: "Second audio socket has lower volume"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Dangger on 2009-11-07
Hi! I have a Dell 1420 with two audio sockets at the front. One of them has higher volume than the other. 

I haven't been able to find the way to adjust the volume of the second socket, it was fairly easy on 9.04 but "Sound Preferences" has changed and I don't know where to find it. 

My guess is that I upgraded with it a little lower and it has stayed like this. Now every time I want to use to jacks one of them will be significantly higher than the other. 

Any help will be highly appreciated :D

---

### Post by Dangger on 2009-11-08
bump...

---

### Post by sandyd on 2009-11-08
> **Dangger said:**
> bump...
go into Applications -> Accessories -> Terminal

type in 
```

alsamixer

```there should now be several bars on the screen
right after the "master" bar there is a "headphone 1" bar and a "headphone 2" bar (doesn't matter if the words are cut off)
use the up and down arrow keys to set the correct volume

when your done, press control + c to close

---

### Post by Dangger on 2009-11-08
> **carlee said:**
> go into Applications -> Accessories -> Terminal

type in 
```

alsamixer

```there should now be several bars on the screen
right after the "master" bar there is a "headphone 1" bar and a "headphone 2" bar (doesn't matter if the words are cut off)
use the up and down arrow keys to set the correct volume

when your done, press control + c to close

Thank you!!! :D It's been solved. Instead of being 100 it was about 80.

---

