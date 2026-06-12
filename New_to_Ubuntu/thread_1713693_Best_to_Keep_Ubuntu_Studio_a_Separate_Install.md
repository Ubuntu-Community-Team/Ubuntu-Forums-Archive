---
title: "Best to Keep Ubuntu Studio a Separate Install?"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by skiesbleed on 2011-03-24
Hello all,

I'm currently a user of Ubuntu 10.10, and I use it mostly for web browsing and development.

I also do a lot of music-related work on my Windows PC right now, but I'm interested in trying out Ubuntu Studio 10.10.

Is it best to have a separate install for Ubuntu Studio and dual boot the two, or to install the packages for Ubuntu Studio into my existing installation?

I'm just wondering if there are any significant differences, or if I can expect to see any significant performance decreases if I go with the latter.

Thanks!

---

### Post by Eiji Takanaka on 2011-03-24
yo skies. I can't particularly see the need to dual-boot on this one dude. Ubuntu Studio is just a tweaked version of regular ubuntu, with a couple of extras. One big extra is the RT kernel which is an extremely cool feature allowing for real-time audio recording/processing. I used ubuntu studio a couple ubuntus back and it was pretty cool. 

The only thing that kept me from using it of late is the fact that the people who run it, hadnt come up with a rt kernel for the later versions of ubuntu. I'm not sure if this has yet been remedied for 10.10 studio or not. You'll have to do a bit of digging on that one. 

But yeah other than a tailored set of packages orientated towards the whole sound/video media production/engineering/recording e.t.c thing. And the aformentioned RT kernel, as well as a few minor tweaks you might have to perform manually with the rcprio paramtert and a couple of other paramters i cant remember off my head. Its pretty much the same dealio.

Hope this helps chief.

---

### Post by Joe of loath on 2011-03-24
Depends if you want the realtime kernel or not.

Doing regular desktop work with the RT kernel won't be very fun, multitasking will be... Interesting. Also, the cruft you install through regular use will probably slow down Ubuntu Studio.

---

### Post by nickleboyblue on 2011-03-24
I use the ubuntu studio audio software setup on my computer, which I also use for developing (I'm a programmer in training, so nothing real yet).  The real-time kernel is not available by default in Ubuntu Studio currently, though work is being done in that direction.  If you want the real-time kernel, you will either have to install it manually or use an earlier version of Ubuntu Studio.  I recommend using the current version, because even without the real-time kernel, modern computers perform well enough that, unless you are doing professional work, you won't need the real-time kernel to get excellent results from your audio work.

Also, using a more modern version of Ubuntu Studio is a great idea because the drum machine supports mute groups and because there are several very important changes to the other programs that are included in Ubuntu Studio.

In short, unless you plan on doing professional audio work, you can get by just fine installing the Ubuntu Studio audio software packages directly on top of what you already have running. It won't hurt your development environment at all, because most likely you don't program at the same time as you work with sound.  The packages you will need are all in synaptic:

ubuntustudio-controls
ubuntustudio-audio
ubuntustudio-audio-plugins
ubuntustudio-menu

---

### Post by skiesbleed on 2011-03-24
Thank you for the responses.

I had heard about the real-time kernel, but I hadn't fully read up on it.

I took a look at the Ubuntu Wiki pages regarding it ([https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)), and it sounds like the most desirable option for me would be the -preempt kernel.

Because my current installation has the -general kernel, I am leaning towards trying Ubuntu Studio as a separate installation.

Does Ubuntu Studio 10.10 have the -preempt or -lowlatency kernel by default? Or do I need to manually install that as well?

Thanks again!

---

### Post by Joe of loath on 2011-03-24
It used to be default, I'm not sure if it is or not now, because I've been using Fedora for my audio work.

---

### Post by skiesbleed on 2011-03-24
Mmm, okay.

If I might ask, what are your reasons for going with Fedora for your audio work?

---

### Post by Joe of loath on 2011-03-24
Planet CCRMA. Ubuntu just didn't have all the packages I needed, but CCRMA does. And when I upgraded to a slightly dodgy machine, it didn't run Ubuntu, so I stuck with Fedora.

---

### Post by skiesbleed on 2011-03-24
Interesting. Since I'm going for a new install anyhow, perhaps I'll have to read up on Planet CCRMA.

Thanks again for your help!

---

