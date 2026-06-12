---
title: "Bizarre wifi and power issue on my Dell Mini 10v"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by kjzz12 on 2011-08-06
So I've been using Ubuntu and a couple other variants for some time now. I just reinstalled a fresh vanilla 11.04 on my Dell 10v, and I've been noticing a bizarre behavior. Upon unplugging my computer from the wall, my wireless speeds drops by a large amount. It feels to me as though it's an intentional behavior, only I can't figure out how to disable it. I have a Broadcom wireless adapter, and I have DSL through Qwest.

Here's a screencast of the issue:
[http://www.youtube.com/watch?v=Oxcn21sRh38](http://www.youtube.com/watch?v=Oxcn21sRh38)

I'm downloading a podcast in this video, just as an example. About 20 seconds in, you'll see my battery indicator turn to unplugged, and simultaneously, my speed will drop from ~500 kb/s to around 60 - a huge difference.

Any ideas? Need any more details?

---

### Post by JC Cheloven on 2011-08-06
> **kjzz12 said:**
> About 20 seconds in, you'll see my battery indicator turn to unplugged, and simultaneously, my speed will drop from ~500 kb/s to around 60 - a huge difference.

Then did you plug it afterwards? I ask because I noticed how your download speed raises again to normal (about 500kb/s) after some seconds.

To answer your question: first run ```
iwconfig
``` and see which interface your wifi is. Likely, it will be eth1. Assuming that (if not please change accordingly), run 
```
sudo iwconfig eth1 power off
``` 

As usual, please use "man iwconfig" to see other options.

---

### Post by kjzz12 on 2011-08-07
You just made my night! Dead on. I'll change this to solved.

And yes, I did plug in halfway through the video. Oh, and Kazam screencaster? Amazing.

---

### Post by JC Cheloven on 2011-08-07
Glad it worked. And BTW, welcome to the forums! :)

---

