---
title: "Couldn't not find package. Webcam server"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by nitroxdm on 2009-12-29
I have a new install of 9.10

I would like to use the box as a web cam server. I found few a guides. The first step is to run:

sudo apt-get install webcam-server

I get:

E: Couldn't find package webcam-server

I remember having to add package sources once upon a time. Is that what I need to do? If so what sources?

Or do I need to do something completely different?

The goal here is to have a internal web page that shows the web cam image, just to monitor one room in my house for the next few days.

---

### Post by oldos2er on 2009-12-29
Make sure you have the universe repository enabled, then try ```
sudo apt-get update && sudo apt-get install webcam-server
```

---

### Post by nitroxdm on 2009-12-29
Thanks I now have webcam-server installed. It's not working like I thought it would. But it's installed.

Thanks!

---

### Post by no2498 on 2009-12-31
does your web cam work with cheese or wxcam
you need ( motion )
it only takes pics if something moves
it runs in the termanl you will need to kill it to stop it

---

### Post by nitroxdm on 2010-04-19
Sorry for leaving this hanging for so long. I ended up installing windows. It worked. Maybe someday I will give it another shot.

---

### Post by ky5u on 2010-04-26
> **oldos2er said:**
> Make sure you have the universe repository enabled, then try ```
sudo apt-get update && sudo apt-get install webcam-server
```
Bless you fair maiden.  I thought I was going batty.  I tried to install nvidia drivers and got everything hosed, so since it was a new unbuntu install, I just reinstalled.  All of a sudden apt-get could not find anything.  Thanks!
:lolflag:

---

### Post by Dmitry13 on 2010-12-08
> **ky5u said:**
> Bless you fair maiden.  I thought I was going batty.  I tried to install nvidia drivers and got everything hosed, so since it was a new unbuntu install, I just reinstalled.  All of a sudden apt-get could not find anything.  Thanks!
:lolflag:
even after such an update there is no such a package, why ?

---

### Post by texpat on 2011-05-31
Yep, same problem here.

EDIT: I did apt-get update, btw. Problem persists.

Ideas anyone?

---

### Post by TwoD on 2011-09-25
[https://launchpad.net/ubuntu/+source/webcam-server](https://launchpad.net/ubuntu/+source/webcam-server)
It seems this package was orphaned a while ago, the release history says there were no releases after Lucid. :(

A bit sad, considering I've not found another webcam HTTP server as simple as this one.

---

### Post by HermanAB on 2011-09-25
ffMpeg has a server called ffserve.

---

