---
title: "Terminal server client disabled some protocols"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by HishamN on 2008-06-04
Hi,

I used ubuntu 6.10 3 weeks ago and when I start Terminal server client I see 3 protocols enabled and 2 are disabled:

- RDP
- RDPv5
- VNC

are enabled,

- XDMCP
- ICA

are disabled.

Now I'm using Ubuntu Hardy (8.04)(GNOME) and I have 2 protocols enabled and 3 disabled!

- RDP
- RDPv5

Are enabled

- VNC
- XDMCP
- ICA

Are disabled!!

My question is, how to enable at least VNC and XDMCP?

Thanks

Regards

---

### Post by HishamN on 2008-06-05
Any comments?

Regards :confused:

---

### Post by chidge on 2008-06-07
VNC disappeared from my list of protocols as well
I got it back by
```
sudo apt-get install vncviewer
```
:KS

edit - maybe it was removed as vinagre is the default VNC client now?

---

### Post by HishamN on 2008-06-08
> **chidge said:**
> VNC disappeared from my list of protocols as well
I got it back by
```
sudo apt-get install vncviewer
```
:KS

edit - maybe it was removed as vinagre is the default VNC client now?

VNC enabled now, what about XDMCP? :confused:

Thanks

Regards

---

### Post by HishamN on 2008-06-10
Any help? :(

Thanks

Regards

---

### Post by HishamN on 2008-06-16
Any help :o

---

### Post by mooncaptain on 2008-07-05
Try installing Xnest on both ends.

1st try running Xnest from terminal. If it isn't installed it will give you a command to install it.

After that go to terminal services and select XDMCP

Again. Do this on both ends. It may not solve all your problems but it worked for me in the LAN environment.

---

### Post by hantms on 2009-02-26
> **chidge said:**
> VNC disappeared from my list of protocols as well
I got it back by
```
sudo apt-get install vncviewer
```
:KS

edit - maybe it was removed as vinagre is the default VNC client now?

I installed vncviewer, but when I try to connect to the remote machine it just vanishes.. (crash?)

Why was this messed with anyway, it used to work perfectly, with all the protocols available

---

