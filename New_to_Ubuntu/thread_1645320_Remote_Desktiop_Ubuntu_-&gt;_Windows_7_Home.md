---
title: "Remote Desktiop: Ubuntu -&gt; Windows 7 Home"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Maciej Miklas on 2010-12-14
Hi,

Windows 7 Home does not have remote desktop service.

I would like to access my Win7 computer from Ubuntu trough remote desktiop. I need to install service on my win7 computer and also have a client on my Ubuntu computer to access it. It should be also free ;)

Does any one know such software? Is it worth using?

---

### Post by HermanAB on 2010-12-14
UltraVNC

---

### Post by bprins on 2010-12-14
or [http://www.realvnc.com/](http://www.realvnc.com/)

or jfgi, there are tons of alternatives :)

---

### Post by Maciej Miklas on 2010-12-14
Thank you!!! It works just great!!

I've installed ultra vnc server on windows and on ubuntu I am using tsclient. I was unable to select VNC protocol in tsclient, but this has solved the problem: sudo apt-get install xtightvncviewer

---

### Post by pricetech on 2010-12-14
I prefer tightvnc under windows, but that's personal preference.

---

