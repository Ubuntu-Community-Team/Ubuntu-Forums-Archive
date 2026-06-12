---
title: "Need a hand with compiling build-essential and madwifi"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by holy_hawk_saw on 2009-02-13
So my girl has a toshiba satellite laptop (atheros AR242x wireless card), and the wireless card does not work with intrepid ibex. I searched high and low for the fix, which I think I found. The only problem is, is that the ethernet is not working and neither is the wifi card, so I have to download from my comp and then install to her comp. Thats where the problem comes in, I'm a newbie, so I need to know if installing build-essential and then the newest madwifi drivers is the right direction, and how to do that without internet. I have the .tar files extracted but thats about as far as I got without trying to fumblef*ck my way through the code. Can anyone give me a hand? much appreciated, and a beer awaits you if you make it my way.:)

p.s. I would also be happy to figure out how to get the ethernet back on, but if the wifi card works, then I'm not as worried. But having internet on the comp is the deal breaker, otherwise she goes back to vista :(

---

### Post by bodhi.zazen on 2009-02-13
Well, you can download the .deb (from the Ubuntu repositories) instead, that makes it easier.

For example : [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndiswrapper](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndiswrapper)

You can use aptoncd to automate the process ...

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I would build from source only if the .deb fail or you are following a specific guide that instructs you to build from source. Such a guide usually has detailed instructions.

---

### Post by holy_hawk_saw on 2009-02-16
thanks so much, I'll give it a shot!

---

