---
title: "Firefox crashes before saving pictures"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-26
Hello! I am having problems with saving pictures from Firefox.

When I go to google and search for any image, and try to save it by doing 'right-click' and selecting 'Save Image as...', Firefox freezes. 

Also, when I try to save the webpage containing just the image (I think it's equivalent to right-click->save image as), Firefox also crashes/freezes.

I do not know whether Firefox crashed X.org or the whole OS. After everything freezes, I do not know how to return to the Desktop or how to escape from this crash (or freeze). I just restart my PC... :(

Does anyone know how this might have happened? I tried installing Opera but I couldn't get it running.

I am using Ubuntu 9.04 64-bit version.

EDIT:

I'm recently installed Ubuntu 9.04 on my AMD64 laptop. I found out that atheros drivers included from the installation was not working on mine, I had to do follow a madwifi guide from the net. It is this one:

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

I used that guide because it works for me perfectly. Note, it had me do a sudo apt-get install build-essential and sudo apt-get update. I'm just thinking that that might have changed something in my firefox.

I never saved a picture from the net before I used the guide. So I never knew whether had the problem before I used madwifi.

PC Setup:

AMD AthlonX2 64-bit
NVidia 8200M G
1.9GHz
3Gb RAM
Ubuntu 9.04 Jaunty Jackalope x86_64

Please advise. Thank you guys! (and girls)

---

### Post by LesterPalooza on 2009-04-26
*bump*

---

### Post by lukjad on 2009-04-26
Can you try this:

Right click the image, and select "Copy Image Location". Then open a terminal (Applications->Accessories->Terminal) and type:

```
wget [Right Click->Paste]
```

This should DL the image to your home directory.

---

### Post by SuperSonic4 on 2009-04-26
I would use wget too and copy/paste the image location. If you want to save it to a different directory you can use cd first

```
cd /dir
wget <image url>
```

Note you do not need the '< >' tags

---

### Post by LesterPalooza on 2009-04-26
It works great for me. :) Thanks!

On the side: I still do not know what's happened to Firefox. :( This is, of course, just a short term solution... I am looking for a long-term solution. :)

---

