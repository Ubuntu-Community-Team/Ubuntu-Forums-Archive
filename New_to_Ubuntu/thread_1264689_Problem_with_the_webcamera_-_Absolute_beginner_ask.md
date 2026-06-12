---
title: "Problem with the webcamera - Absolute beginner asking for help :)"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by La-Pixie on 2009-09-12
I installed **Ubuntu 9.04** yesterday. I tried to start my webcam (**Logitech Quickcam Communicate STX**), testing it in ***skype***'s options. However, it just showed a* green screen with statics*. 

Searching on google, I came across the ubuntu help site, and understood that I already had the drivers (otherwise the camera wouldn't even be recognized) but needed to change some kind of commands in order to make it work. I tried to change the commands on skype as it is indicated, but it *did not work*. There were, however, no further details on this particular problem, so I decided to ask for help here.

Does anyone know how to change these commands? I am only a **newbie** on ubuntu and linux in general, so*** I don't know much about commands and such***...
[B]
Thank you in advance for any help![/B] :D

---

### Post by Liolikas on 2009-09-12
Maybe try in other programs? Still same?

---

### Post by La-Pixie on 2009-09-12
I don't have many applications on which I can try it, but um, no, it doesn't work , gives the same result : greenish screen with statics.. :(

---

### Post by nothingspecial on 2009-09-12
Install cheese.

Open a terminal (in your menus applications > accessories > terminal) and type

```
sudo apt-get install cheese
```

After it`s installed it should appear in your sound and video menu.

If you launch it can you see yourself, in which case it`s a matter of configuring skype.

---

### Post by nothingspecial on 2009-09-12
Also can you link the page with the commands you tried.

---

### Post by La-Pixie on 2009-09-12
Thank you, I will try that out now!
 :)

This is the page : [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by La-Pixie on 2009-09-12
I can see myself on Cheese but not on skype...I guess the problem lies there, then. Would you happen to know as well how to configurate skype in order to fix this error?

---

### Post by nothingspecial on 2009-09-12
Close skype

Open your terminal again.

```
gksudo gedit /usr/local/bin/skype
```

Copy and paste this into the file that opens then save and close

```

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```

Then in your terminal
```


sudo chmod a+x /usr/local/bin/skype
```

Try skype again.

---

### Post by La-Pixie on 2009-09-12
Thanks a loooot!!! It worked!
:)

---

### Post by nothingspecial on 2009-09-12
No problem

---

