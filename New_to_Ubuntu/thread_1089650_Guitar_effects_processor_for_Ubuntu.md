---
title: "Guitar effects processor for Ubuntu?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-03-07
Does anyone know about any *.deb package of some guitar effects program? My eyes dropped out searching for one :-)

---

### Post by gn2 on 2009-03-07
A quick search of Synaptic for "guitar" throws up [Creox]("http://zyzstar.kosoru.com/?creox").

---

### Post by ivanvajar on 2009-03-07
Pink Floyd fan? Love 'em! No, it doesn't work. It's unusable (at least on my machine). I've been trying to get it to work for weeks.

---

### Post by gn2 on 2009-03-07
> **ivanvajar said:**
> Pink Floyd fan? Love 'em!

Yes, but not the post Rick Wright era.

Bummer about Creox, have you tried [Jack Rack]("http://jack-rack.sourceforge.net/")?

---

### Post by ivanvajar on 2009-03-07
Damn! Something just crossed my mind. The bloody thing started with sudo jackd -d alsa | sudo creox 

OK! If anyone else has problem with CREOX: use Synaptic to install jackd. Run Terminal and type **sudo jack -d alsa** and in a new Terminal window **sudo creox**

When you close Creox, press ctrl+c to exit jackd and close Terminal.

---

