---
title: "Ubuntu defaulting to wrong wireless access point"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by blisterpeanuts on 2007-08-05
I've searched but can't find the answer to this question:  how do I get Ubuntu 7.04 feisty faun to default to my wireless access point?  Every time I boot it up or re-enable wifi networking, for some reason it locks onto a neighbor's network even though my wifi router is right in the same room and gives the strongest signal.  There seems to be no way in the GUI tools to remove the other networks from the list or set a default.  Other than this, Ubuntu with ndiswrapper rocks!  Is there a how-to or fix for this?  Thanks,
Blisterpeanuts

---

### Post by sfarber53 on 2007-08-05
If I recall correctly, you need to go into Administration ===> Network.  In there you should find the ability to set the ESSID for the network you want to connect to along with other settings that you can set at the same time.

I'm sorry for being so vague, but I'm not in front of my Feisty box at the moment.  You should be able to set a static IP (if desired) as well as give the box DNS information that will facilitate your access to the internet.

Cheers! 

Steve

---

### Post by sgornick on 2007-08-28
gconf-editor, as described in the Answer to my question here:
  [https://answers.launchpad.net/ubuntu/+question/12327](https://answers.launchpad.net/ubuntu/+question/12327)

---

