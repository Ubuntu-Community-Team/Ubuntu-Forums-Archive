---
title: "n00b with video issues"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by MoeThirteen on 2009-09-03
Hi! I have been using Ubuntu for about a month now and I have been 99% happy with the change One problem I have is that when I watch video online (mostly you tube) my CPU maxes out and anything I do (i.e. pause, back, or close tab) comes with a significant delay.

I was wondering if this could be a driver issue? I looked but never found any solid answer.

This is my four year old bone stock "rig": [http://www4.dealtime.com/xPF-AMD-eMachines-W3105-Desktop-w-AMD-Sempron-3100-processor-15-LCD-Display](http://www4.dealtime.com/xPF-AMD-eMachines-W3105-Desktop-w-AMD-Sempron-3100-processor-15-LCD-Display)

Thanks in advance for any help.

---

### Post by T.J. on 2009-09-03
[QUOTE
I was wondering if this could be a driver issue? I looked but never found any solid answer.
[/QUOTE]

If you are using the stock onboard video, you may have driver issues depending on what you do.  That would be my guess.

---

### Post by MoeThirteen on 2009-09-03
Would I need a specific driver for my setup or is there a general driver I need?

---

### Post by mapes12 on 2009-09-03
Hi

The link you posted says that your video device is a VIA UniChrome Pro. This may help: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by MoeThirteen on 2009-09-03
Thanks it did help. Although it helped rule out a driver issue because it said that my driver comes with ubuntu 8.04 and up.

So I guess I have the same problem except its not a driver issue unless someone has information to contrary. ](*,)

---

### Post by pedro3005 on 2009-09-03
Did you install ubuntu-restricted-extras?

---

### Post by Sealbhach on 2009-09-03
It might be the version of flash you're using. Open up a new tab and type in

```
about:plugins

```You should find an entry for Flash that looks a little like this:

> **Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 10.0 r32Have a look at what version you're using. Also, maybe change/update your Firefox. Look in Synaptic for Firefox 3.5.

You could also test how Youtube works in Opera: [http://www.opera.com/](http://www.opera.com/)

To see if it's a problem with Firefox only.

.

---

### Post by MoeThirteen on 2009-09-04
> **Sealbhach said:**
> It might be the version of flash you're using. Open up a new tab and type in

```
about:plugins

```You should find an entry for Flash that looks a little like this:

Have a look at what version you're using. Also, maybe change/update your Firefox. Look in Synaptic for Firefox 3.5.

You could also test how Youtube works in Opera: [http://www.opera.com/](http://www.opera.com/)

To see if it's a problem with Firefox only.

.

I looked at my flash and it said "Shockwave Flash 10.0 r32" which is up to date.

also i'm using firefox 3.5 even though it says "Shiretoko"

and I will check out Opera

EDIT: i tried opera and it works better but not by much the CPU still hovers at around 93% and i had issues with streaming video freezing or not starting.

---

### Post by Sealbhach on 2009-09-04
> **MoeThirteen said:**
> I looked at my flash and it said "Shockwave Flash 10.0 r32" which is up to date.

also i'm using firefox 3.5 even though it says "Shiretoko"

and I will check out Opera

EDIT: i tried opera and it works better but not by much the CPU still hovers at around 93% and i had issues with streaming video freezing or not starting.

Look in Synaptic and see if you have the plugin 

swfdec-mozilla - mozilla plugin for SWF (macromedia flash)

If you have, remove it and see how that works.

.

---

### Post by MoeThirteen on 2009-09-04
> **Sealbhach said:**
> Look in Synaptic and see if you have the plugin 

swfdec-mozilla - mozilla plugin for SWF (macromedia flash)

If you have, remove it and see how that works.

.

It was unchecked so I don't have it.

---

