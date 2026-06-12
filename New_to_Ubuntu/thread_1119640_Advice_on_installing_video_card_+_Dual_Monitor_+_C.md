---
title: "Advice on installing video card + Dual Monitor + Compiz"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by suomalainen on 2009-04-08
Ubunteros:

I would like to run dual monitors with Compiz on a 8.04LTS system. However, I am uncertain of what the exact first steps are/should be, in order to perform a flawless install????

At the moment, I have NOT installed Compiz nor have I installed the graphics card. Before I do that, I wanted to find out here the order in which I should install the hardware and install the programs so that the entire process goes without issue!

The hardware I have includes:

Two (2) HP w1907 displays

EVGA 256-P2-N761-TR GeForce 8600 GTS 256MB 128-bit GDDR3 PCI Express x16 HDCP Ready SLI Supported Video Card - Retail

Two (2) DVI-D Single link cables

The instructions I'm looking at following include:

[http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/](http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/)

[http://www.youtube.com/watch?v=zFX5UssUgcs](http://www.youtube.com/watch?v=zFX5UssUgcs)

Additionally, it is my understanding that a DVI-D Single Link cable is fine to use for resolutions below 2000. But how does this work in relationship to dual monitors? Is my actual screen resolution increased to over 2000+ where a DVI-D Dual Link cable may be required???

Any advice, insight or other lead information is appreciated.

Thank You!

---

### Post by Sam Lars on 2009-04-09
Compiz is installed by default in Ubuntu, you may just not be using it since you don't have the video drivers installed for your card.
I would think that the cables would be on a per-monitor basis... each cable would only have to be responsible for the resolution of the monitor it is connected to.
So I think you only have to worry about installing your video drivers for Compiz.  You should be able to set up dual screens before then.
Does Hardy have a program display properties in Administration or Preferences in the menus?  I think Intrepid does and I know Jaunty does, and it makes configuring dual monitors very easy.

---

### Post by suomalainen on 2009-04-09
Sam Lars,

Thanks for the reply!

Do you believe that first I should:

1. Install graphics card
2. Install video drivers using Envy NG 
3. Enable dual monitors
4. Install Compiz?

What are your thoughts?

Regards,

Suomalainen

---

### Post by Sam Lars on 2009-04-09
That looks like a good order.

---

