---
title: "Switching from Ubuntu Server to regular Ubuntu 8.10"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by twilliamswithaz on 2008-12-18
So today I probably made my first error in jumping into the linux world by just flat-out installing ubuntu server with no real purpose. I found a guide online that was fairly in-depth and pretty practical. I was bored and messing around with my old desktop, who cares, right?

Well then I decided that I wanted to use the desktop ubuntu OS. I liked the server version, and just want to run my computer using linux.

So my question now is, how do I get Ubuntu installed on my computer? And can I keep the ubuntu server on there?

I have the ISO downloaded onto my CD. I booted from the Ubuntu 8.10 CD. I hit install. It took me to a screen with a beige background, and then froze up with just a cursor. 

So is there anyway I can partition my HD through ubuntu server, and then install ubuntu 8.10 on that partition? how would i go about doing this?

Thank you.

---

### Post by Cl0ud9 on 2008-12-18
I have never tried this, but installing a desktop on the server seems pretty straightforward, if thats what your looking for.

```

sudo apt-get install ubuntu-desktop

```

---

### Post by twilliamswithaz on 2008-12-18
So i don't need to install the 8.10 OS?

---

### Post by Cl0ud9 on 2008-12-18
> **twilliamswithaz said:**
> So i don't need to install the 8.10 OS?

You already have the Ubuntu 8.10 OS installed with the serer version, you just don't have a desktop. Running my previously posted command will keep the server, but it will give you a desktop as well.

---

### Post by jerome1232 on 2008-12-18
In addition to that you might want to switch from the server kernel to the generic kernel (the one that gets installed by a normal installation cd)

```
sudo apt-get install linux-generic
```

But yes that's basically all you have to do, the server version has a server kernel optimized for that job and no desktop enviroment. Installing ubuntu-desktop and linux-generic will get you all of the packages that come with a standard installation.

---

### Post by twilliamswithaz on 2008-12-18
Thank you all very much. I can't wait to get started and learn more on all of this. It's really fascinating to a prior windows user like me, with only some Unix experience from the mac. (I ran the X11 terminal a lot to get familiar with terminal commands)

---

