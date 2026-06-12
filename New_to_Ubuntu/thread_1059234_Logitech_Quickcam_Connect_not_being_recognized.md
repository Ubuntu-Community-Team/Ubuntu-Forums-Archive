---
title: "Logitech Quickcam Connect not being recognized"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Djalmahal on 2009-02-03
Hi,

i did some research before buying a quickam connect from logitech, some sites claim it works out of the box, some say you have to route it through a virtual device, but after plucking it in it simply is not being recognized (skype, cheese, camstream). I did install gpcsa, restarted. The out of "lsusb"is 

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 046d:089d Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So it seems to shop up as bus 002, I have no other logitech device used in my computer

I use Ibex and the light on the camera doesn't light up.

I tried to follow
[http://ztatlock.blogspot.com/2008/11/logitech-quickcam-in-ubuntu-810.html](http://ztatlock.blogspot.com/2008/11/logitech-quickcam-in-ubuntu-810.html)
but the code didn't go through, i don't know the terminal well enough to know why.

What to do next?

Thanks
Andreas

Update:

I ran the install program in a virtual windows machine and the webcam is recognized and working with the logitech software, skype crashes though.
What am I missing in linux?

---

### Post by petervk on 2009-02-04
Looks like this is a Ubuntu kernel bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267522](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267522)

You can follow the progress at the link above and possibly try any workarounds suggested (if there are any).

Webcam support in linux is hit or miss. Can you return it for another?

---

