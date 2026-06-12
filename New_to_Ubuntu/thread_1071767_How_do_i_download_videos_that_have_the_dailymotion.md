---
title: "How do i download videos that have the dailymotion player???"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by mr.big_gun on 2009-02-16
i want to download alot of pink floyd videos i found and i cant get them. plz help.

---

### Post by Dark006 on 2009-02-16
Start here ([http://www.howtogeek.com/howto/linux/saving-flash-videos-in-linux/](http://www.howtogeek.com/howto/linux/saving-flash-videos-in-linux/)), this will probably help you. 
What I did was made a script for it:
```

#!/bin/bash
cp /tmp/Fla* ~/Desktop/Flash\ Video

```
I made it executable and then I made a launcher for it, so anything that is loaded into memory will be saved to your desktop then you can just rename it.

---

### Post by mr.big_gun on 2009-02-16
yea thats what i do for youtube videos but this player doesn't put the video in my tmp
im kinda a newb so what do i do with a script

---

