---
title: "NetworkManager and turning off wireless"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by emu on 2008-11-08
hi,

I do not like to have wireless enabled when I have a wired connection, but I am having trouble turning the wireless off.  with NetworkManager, when I right-click on it I see the checkbox for 'enable wireless,' and it is checked, but it is also greyed out so I can't change it.  I've tried 'sudo ifconfig eth1 down', but the NetworkManager still shows that I am connected to wireless (and the light on my laptop that indicates that the wireless is active is still on).  also, when I do 'ifconfig', eth1 still shows up.  however, in this situation when I unplug my ethernet I can't connect to the internet, indicating that I am not using wireless but I am using the wired connection.  

how come NetworkManager won't let me disable wireless?  how do I get it to be consistent about showing me when I am connected to wireless and when I am not?  any help is greatly appreciated.

---

