---
title: "Ubuntu 8.10 in Virtualbox on MBP 3,1"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by GTRichey on 2009-03-06
I'm having trouble finding any help anywhere on getting things working in this setup. I cannot get sound or wireless working.

---

### Post by linuxuser21 on 2009-03-06
You do not need a wireless setup.  Virtual box should automatically have a internet connection set up and your OS should pick it up.  I cannot get sound to work either on any of the systems in Virtualbox.

---

### Post by andrew.46 on 2009-03-06
Hi GTRichey,

> **GTRichey said:**
> I'm having trouble finding any help anywhere on getting things working in this setup. I cannot get sound or wireless working.

I am running a Jaunty guest on a Slackware host with working sound and network, I attach screenshots to show the relevant settings that work for me. You do not specifically need *wireless* as the network connection is virtual.

All the bext,

Andrew

---

### Post by huzzam on 2009-03-06
For sound, in the ubuntu virtual machine settings, set "enable audio", use the "core audio" host audio driver, and "ich ac97" as the audio controller. You also have to make sure your Machine Type on the General tab is set to "Ubuntu". (I lost sound once by accidentally having it set to "Linux 2.6")

As linuxuser21 said, you shouldn't need to set up wireless, as VirtualBox should create a bridge, which will look like a wired connection, but will use whatever active net connection your MacOSX is using. In case you wanna double check your settings, under the Network tab of the settings, Adapter 1, set "Enable Network Adapter", type = "Intel PRO/1000...", Attached to "NAT", and "Cable connected. 

hope this helps
peter

---

### Post by GTRichey on 2009-03-07
Thanks for the replies. I did figure it out. Turns out I was looking on information regarding Ubuntu and it turns out the problem was in Virtualbox's settings.

---

