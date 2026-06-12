---
title: "Internet disconnects after a couple of minutes"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by steveishere on 2009-10-13
I have had a wireless Internet setup with my desktop PC loaded with Ubuntu 9.04.  It's worked fine until recently.  Lately, when I've gotten onto Firefox, the Internet disconnects within one to five minutes.  The problem is not with the Internet connection, as my laptop works just fine with the wireless Internet.  I have a USB wireless port from Asus.

---

### Post by pythonscript on 2009-10-13
In my experience, usb wireless cards can be fickle most of the time. I would try connecting the USB wireless card to your laptop, turn off your laptop's internal card, and try connecting that way (to see if it's the card or your desktop computer). Also, you could try connecting to the router that I'm assuming exists wired, if possible, and see if the same problem still occurs. Once we troubleshoot that, we'll try other options.

---

### Post by steveishere on 2009-10-16
Thanks for the suggestion of connecting my wireless adapter to my laptop, and connecting my desktop computer via ethernet cable to the router.  I'm not sure if I've had any success doing either, though.  

I have an Asus Eee PC laptop operating on Xandros Linux, and I don't know how to get into the settings to get it to switch from its internal wireless port to the USB port.  Likewise, I'm not sure if I can get my desktop to switch from its wireless port to the ethernet cable.  I know that I originally had to get help just to get the system to read my Asus wireless port, going through a number of commands in terminal mode.  

So I don't know if you can help me with doing either one?  Thanks!

---

### Post by pythonscript on 2009-10-16
I don't know about xandros linux... I've never even used that distro before. However, in terms of your desktop, you should be able to disconnect the usb wireless device and connect the ethernet cable and it (the gnome network manager) should be able to pick up the wired network automatically, assuming you have a relatively standard network card. Sorry I can't be of more help than that! Maybe someone else in the community will know how to work with xandros linux; it might be almost identical for all I know, but I don't know anywhere close to enough to comment.

---

### Post by steveishere on 2009-10-17
Thanks.  Well, here's the results of my tests--when the USB port is in, the Internet connects but disconnects after a couple of minutes.  When the USB port is out and I connect via ethernet cable to the router, the Internet doesn't connect at all.  But my laptop continues to connect via its wireless port with no problem.  

Thanks for your help!

---

### Post by pythonscript on 2009-10-17
I'm not sure what to tell you about your desktop computer... what kind of ethernet card do you have in your desktop? That's one piece of hardware that should work pretty well unless you have a really old and/or non-standard piece of network hardware. 

Let me see what
```
lspci | grep Ethernet
```

returns, and if nothing, just post all of lspci here.

---

### Post by steveishere on 2009-10-18
This is what I get:

02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet controller (rev 03)

---

### Post by pythonscript on 2009-10-18
You could search these lists to see if you card is on the list of supported hardware; I would think it would be, though, because normally Intel has good support for Linux and vice versa. I'm almost out of ideas, but hopefully more people in the community will get on this thread!

---

