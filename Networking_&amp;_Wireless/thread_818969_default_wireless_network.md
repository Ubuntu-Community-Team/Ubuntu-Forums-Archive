---
title: "default wireless network"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by le_vainqueur on 2008-06-04
I want to change the priority of wireless networks that my laptop connects to.  In my room I get my personal wireless which is a strong connection and a very weak connection from an adjacent building.  I found similar problem here:

> [http://ubuntuforums.org/showthread.php?t=508050](http://ubuntuforums.org/showthread.php?t=508050)

In my case, however, I do not want to delete the other network since sometimes I am in that building and that is the access that I need.  I have been deleting the adjacent building signal every time I come back home, but that gets tedious.  Is there any way to simply change the priority of the connections?


Thanks,

LV

---

### Post by spd106 on 2008-06-05
This is a little non-intuitive but what you need to do is alter the time that you last connected to the network in nm-editor. Network-Manager works by a kind of last-in first-out (LIFO) method.
On 8.04 you access nm-editor by right-clicking the icon and selecting Edit Wireless Networks. 
See this wiki page for more [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by le_vainqueur on 2008-06-05
Awesome, thanks!  The only thing that took me a while to figure out is that I needed to disable my wireless network before doing that (yeah, it seems obvious in retrospect).

---

