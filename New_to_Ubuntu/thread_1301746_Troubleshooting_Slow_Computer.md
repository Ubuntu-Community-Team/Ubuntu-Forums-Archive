---
title: "Troubleshooting Slow Computer"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by kyalee on 2009-10-26
My dad's computer has been running slowly lately, especially with regards to streaming videos on Hulu and such. Videos are jumpy at times. He recently updated to Ubuntu 9.04, but says that the problem pre-dated that.

Best ways to troubleshoot this? I'd really like to avoid having to re-install the whole operating system, but will if I have to.

---

### Post by squee on 2009-10-26
> **kyalee said:**
> My dad's computer has been running slowly lately, especially with regards to streaming videos on Hulu and such. Videos are jumpy at times. He recently updated to Ubuntu 9.04, but says that the problem pre-dated that.

Best ways to troubleshoot this? I'd really like to avoid having to re-install the whole operating system, but will if I have to.

Try running the Computer Janitor in System>administration

Apart from that, make sure that all your software is up to date with the update manager.

---

### Post by kyalee on 2009-10-26
Computer Janitor didn't bring anything up.

Everything is up to date.

---

### Post by H3l0 on 2009-10-26
System Specs???

---

### Post by philinux on 2009-10-26
> **kyalee said:**
> My dad's computer has been running slowly lately, especially with regards to streaming videos on Hulu and such. Videos are jumpy at times. He recently updated to Ubuntu 9.04, but says that the problem pre-dated that.

Best ways to troubleshoot this? I'd really like to avoid having to re-install the whole operating system, but will if I have to.

On a panel right click and add the cpu frequency scaling monitor.

If it's supported on your dad's pc try changing the setting to conservative or performance instead of ondemand. You left click the applet to get the dialogue drop down.

Full screen flash is now jerky at all for me with the above change.

---

### Post by lavinog on 2009-10-26
What video card is installed?
Did you enable the restricted drivers?
Is this a 64bit install?  If so did you manually install the 64bit flash?

---

### Post by candtalan on 2009-10-26
The amount of RAM will have a big effect on stuff, particularly for older computers.

Can be examined with system>administration>system monitor
or  faster with fewer resources, using htop
hth

---

