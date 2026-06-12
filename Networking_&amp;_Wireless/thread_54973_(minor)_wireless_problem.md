---
title: "(minor) wireless problem"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by w0073r on 2005-08-06
Hey,

My desktop has a Linksys wireless card (a WMP54G). I set it up with ndiswrapper and the driver off the CD, and it works fine, except that it doesn't seem to activate itself. That is, when I boot up my computer sits at "Loading ndiswrapper" or somesuch for a good minute, then boots without working internet. When I get into Gnome, I have no network until I go into network-admin, open the properties for my wireless, and hit accept. After it initialises there, I'm good. Strangely enough, doing /etc/init.d/networking stop followed by /etc/init.d/networking start doesn't work.
 
 If it's relevant, I have two wireless networks here (an 802.11b and an 802.11g -- it chooses the g to start with).
 
 Any thoughts?

---

