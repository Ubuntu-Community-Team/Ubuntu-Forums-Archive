---
title: "Help with webcam-server"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by weirdbeardmt on 2009-05-16
Hi

On Ubuntu Desktop 9.04, I installed webcam-server (sudo apt-get install webcam-server). 

You need to issue 

```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```

before running it, which gets round the No Supported Colour Palette found error, and then it works fine.

However, I want to run it on 9.04 server, and I'm stuck.

I assume server doesn't have v4l so have installed it

```
sudo apt-get install libv4l-0
```

However, whenever I run it, even with the LD_PRELOAD, I get the No Supported Colour Palette error.

I don't know enough about linux to troubleshoot... any ideas or help?! :)

---

### Post by weirdbeardmt on 2009-05-17
In fact I think this is more likely something to do with gnome. I installed Ubuntu 9.04 desktop but from the alternate CD and did a commandline install only - and once again, no dice, getting the "no support colour palette" error.

Any idea how I can get the appropriate colour palettes or whatever I need, without installing gnome?

---

### Post by weirdbeardmt on 2009-05-17
Well I give up. I got it working with Motion instead.

---

