---
title: "webkit version of Epiphany--Can anyone point me to it?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by khaos28 on 2009-05-18
I need the webkit version of Epiphany. 

Can anyone get me int he right direction of the sudo code i put into the terminal, or a link or something?

---

### Post by Dark_Stang on 2009-05-18
Webkit version of epiphany? If you're asking for a web developers version of epiphany... I don't think such a thing exists.

---

### Post by SunnyRabbiera on 2009-05-18
You could try midori

---

### Post by gandaran on 2009-05-19
> **khaos28 said:**
> I need the webkit version of Epiphany. 

Can anyone get me int he right direction of the sudo code i put into the terminal, or a link or something?
the epiphany-webkit browser is no longer available from the jaunty 9.04 repository but you can get it from [intrepid 8.10 repository ]("http://packages.ubuntu.com/intrepid/epiphany-webkit") it should work in jaunty too but I must say it's a waste of time installing it, epiphany-webkit or midori crashes every time you click a link, they are not ready, if you need a webkit browser try [chromium]("https://launchpad.net/~chromium-daily/+archive/ppa") (linux google chrome) it's still in testing phase but at least it doesn't crash all the time.

---

### Post by Stemp on 2009-05-19
[Webkit Team PPA ]("https://edge.launchpad.net/~webkit-team/+archive/ppa") : epiphany-webkit 2.27.1

---

### Post by nortexoid on 2009-05-23
> **gandaran said:**
> the epiphany-webkit browser is no longer available from the jaunty 9.04 repository but you can get it from [intrepid 8.10 repository ]("http://packages.ubuntu.com/intrepid/epiphany-webkit") it should work in jaunty too but I must say it's a waste of time installing it, epiphany-webkit or midori crashes every time you click a link, they are not ready, if you need a webkit browser try [chromium]("https://launchpad.net/~chromium-daily/+archive/ppa") (linux google chrome) it's still in testing phase but at least it doesn't crash all the time.

But if you like flash, then chromium is useless. Also, I didn't find epiphany THAT bad, though if I had to use it, I would stick with the gecko version.

---

### Post by Tibuda on 2009-05-23
> **Dark_Stang said:**
> Webkit version of epiphany? If you're asking for a web developers version of epiphany... I don't think such a thing exists.

WebKit is the rendering engine used by Chrome, Safari and Midori. Firefox and Epiphany (by default) uses Gecko, Opera uses Presto, and MSIE uses Trident.

@khaos28
To install Epiphany WebKit, use the PPA linked by Stemp.

---

### Post by Scott Jackson on 2009-05-30
I installed it from :
[https://launchpad.net/~webkit-team/+archive/ppa]("https://launchpad.net/%7Ewebkit-team/+archive/ppa")
By following the directions provided, I was able to use "sudo apt-get install epiphany-webkit". Please note that if you just run epiphany-browser, you will start the "gecko" version. You have to run epiphany-webkit; check Help-About to confirm the version.

If you want and are able to do-it-yourself, the directions are at:
[http://live.gnome.org/Epiphany/WebKit](http://live.gnome.org/Epiphany/WebKit)

---

### Post by Sef on 2009-05-30
> You could try midori


Midori is nice, but it is in early stages of development, so some features do not work.

---

