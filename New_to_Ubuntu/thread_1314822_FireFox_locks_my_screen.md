---
title: "FireFox locks my screen"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Devon64327 on 2009-11-04
I noticed that after upgrading to 9.10 whenever im on flash heavy sites like Kongregate.com or even just facebook my screen will lockup forcing a hard reboot. What can I do to fix this? 
I have reinstalled firefox, deleted all plugins/extensions and no dice
thnx

---

### Post by wojox on 2009-11-04
[ Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

Try that.

---

### Post by fooman on 2009-11-04
what flash do you have installed?

try this:  open synaptic (system > administration > synaptic package manager)...search for flash

scroll through the results and uninstall anything with gnash or swfdec (including libswfdec) in its name.

then install the flashplugin-installer

close firefox if it is open...then open it again and see if its any better.

hope that helps.

---

### Post by merlyn on 2009-11-05
I've noticed the same mostly when viewing Flash intensive sites, latest FF and official Flash plugin using Kubuntu 9:10.

Many might say that Flash itself is the problem.

However I have no problems whatsoever with Flash intensive sites on my Debian SID install, FF (Iceweasel), and the latest Flash Plugin on the same system.

Go figure.

---

