---
title: "Laptop wireless requires restart"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by atatistcheff on 2008-03-04
I have a Dell Inspiron 1420 with the broadcom wireless card.  I haven't edited any files, just used the Gnome networking applet to configure the wireless.  However, I have discovered that upon boot up the wireless does not work.  To make it work I have to run "sudo /etc/init.d/networking restart".  I've placed a launcher on the desktop that runs this command but it's sort of a pain to have to do that every time I start the computer.  Seems to me that it's trying to find the access point before all the drivers are loaded or some such thing.  So, it fails and then mean time the drivers all load but by then it's too late.  It's just a theory of course as I'm not terribly familiar with all the components that load for the wireless networking.

I've seen a few posts where people have similar problems but I haven't seen any definite solutions.

Any ideas on how to change the load order so the components can do what they're supposed to do?  Maybe just a startup script that runs last and restarts networking?  Don't like that one but at least it would work around the issue.

Thanks!

---

### Post by wieman01 on 2008-03-04
Post 2 of my WPA tutorial (signature) offers a solution that has worked for many others. Check it out. It's a common bug.

---

### Post by atatistcheff on 2008-03-04
Got it - thanks!

---

