---
title: "wireless stopped working after update"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by mookie_jones on 2009-05-06
I came into work this morning, and allthough i was previously allready using jaunty, i ran the update manager and now my laptop doesnt see the wireless card. 

I found that when i turn the wireless card on though, the bluetooth icon shows up in the systray and then disappears when i power the wireless card off. going back to the previous release allows my card to work again..

how do i fix this?

---

### Post by lkraemer on 2009-05-06
Maybe this will help.... if it applies to your hardware!

To check for your Wifi hardware, Open a Terminal Window and DO:
```

lshw -C network
 

```
You should see Atheros AR242x.

[http://ubuntuforums.org/showthread.php?t=1142199](http://ubuntuforums.org/showthread.php?t=1142199)

lkraemer

---

