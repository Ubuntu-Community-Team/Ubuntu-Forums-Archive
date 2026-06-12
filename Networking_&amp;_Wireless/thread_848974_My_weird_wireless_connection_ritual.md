---
title: "My weird wireless connection ritual"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by sharp11 on 2008-07-04
So, I installed my wireless adapter and was able to connect to my router using WPA2 security. It basically just worked .. yay, Ubuntu! (I'm on Gutsy.)

But every time I booted, I got network-manager's "Passphrase required" screen, so I noodled around to try to get it to remember my passphrase. And that sort of worked ... Now here's the weird part. 

Every time I boot, I still get that "Passphrase required" screen. I just hit escape, and then click on the n-m icon and select my essid -- it connects and then immediately disconnects. Then, I do it again, and it connects fine.

That's my ritual: escape, connect, connect. Works every time. But why ...? How do I make it just connect when I boot?

---

### Post by Bubba64 on 2008-07-04
> **sharp11 said:**
> So, I installed my wireless adapter and was able to connect to my router using WPA2 security. It basically just worked .. yay, Ubuntu! (I'm on Gutsy.)

But every time I booted, I got network-manager's "Passphrase required" screen, so I noodled around to try to get it to remember my passphrase. And that sort of worked ... Now here's the weird part. 

Every time I boot, I still get that "Passphrase required" screen. I just hit escape, and then click on the n-m icon and select my essid -- it connects and then immediately disconnects. Then, I do it again, and it connects fine.

That's my ritual: escape, connect, connect. Works every time. But why ...? How do I make it just connect when I boot?

Here is a solution and explanation I gave somebody else yesterday it sounds like your running the network manager with roam.
[http://ubuntuforums.org/showthread.php?t=831050](http://ubuntuforums.org/showthread.php?t=831050)
Note the restart after setting the manual to get it to work, if you set everything up correctly. :)

---

### Post by sharp11 on 2008-07-05
Thanks, but inputting my settings manually into network-manager is basically what I did already. It does remember them, sort of ...

---

### Post by Bubba64 on 2008-07-05
> **sharp11 said:**
> Thanks, but inputting my settings manually into network-manager is basically what I did already. It does remember them, sort of ...

So if you run the network manager on manual is a password prompt coming up. The funny thing is that the wired pat of the manager has a roam setting as well, I always set it, to roam on a new install then start the process of the manual wireless and get things working immediately, but I have a external wireless card that worked out of the box. I am curious of what you mean by the sort of.

---

