---
title: "Swfdec Flashplayer &amp; Gnash SWF Viewer in 9.04"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-11-07
Can anyone tell me how to get Firefox to work with one of the free flash players in Ubuntu 9.04 instead of constantly asking for Adobe Flash Player?  Thanks!

---

### Post by Excedio on 2009-11-07
[Swfdec]("http://swfdec.freedesktop.org/wiki/Installation")

Try this..good luck :-)

EDIT: Removed the Gnash link...realized it was not really what you are needing.

---

### Post by yeats on 2009-11-07
Quoting from [this awesome page]("http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html")

> I also recommend you at least give a fair chance to Gnash, an open source flash player on the list of high priority Free software projects. To install, you'll first have to make sure you don't have Adobe's flash player installed via Synaptic or Terminal.

Command:

sudo apt-get purge flashplugin-installer nspluginwrapper


Finally, you can install the Gnash plugin via Synaptic of Terminal.

APT Line: ppa:gnash/ppa
Click here to install or use the following command:

sudo apt-get install mozilla-plugin-gnash

---

### Post by lovinglinux on 2009-11-07
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

