---
title: "Wireless reconnect at boot"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by converted on 2008-04-26
I've moved to Ubuntu from another Linux distro just within the past few weeks.  I'm not quite a complete noob, but definitely still a novice within linux.  

I don't think this question is hardware related, but I can provide hardware specs if required.

Currently I have Ubuntu running on 3 machines.

2 *nearly* identical laptops.

1 desktop.

The desktop and one laptop had 7.10 installed, and were both upgraded to 8.04 shortly after the RC was released. <-- This may not be relevant in any way, but it seems like it might be worth mentioning.

The other laptop just had 8.04 installed fresh last night. 

On the two machines which were *upgraded* to 8.04, I'd been meaning to post for a few days regarding the fact that I have to manually reconnect to my WLAN (WPA-PSK) after every reboot.

I was pleasantly surprised today to find that when I rebooted the laptop with the fresh 8.04 install, and it reconnected to my WLAN on boot.

So, if I do a fresh 8.04 install on the other boxes, will my problems magically disappear, or is there some other way to solve this problem on those machines?

I have indeed searched the forum, but I'm not sure that similar posts I've found have actually been the same problem.

[This post]("http://http://ubuntuforums.org/showthread.php?t=624900") is describes my symptoms precisely.

Thanks!

---

### Post by justin_acklin on 2008-04-26
I also installed 8.04RC first and later upgraded.  I am also experiencing this exact same problem, except I am using wpa2.

Another way to make the connection start is
sudo ifdown wlan0
sudo ifup wlan0

---

### Post by dhysk on 2008-04-27
Justin, did you do a new install or an upgrade install?

The reason I ask is i have this problem intermitantly, and have since 7.10

---

### Post by kevdog on 2008-04-27
You may want to add a preup sleep 20 in the /etc/network/interfaces file in the section pertaining to your specific adapter.  This will give a chance for other modules to load first if this is the problem.

---

### Post by justin_acklin on 2008-04-27
This was a new install of 8.04RC, since upgraded to 8.04LTS.

---

### Post by converted on 2008-04-28
I didn't see the replies on this until just now, I'll try the suggestions above later today.

I did, however, want to clarify one detail of the OP -- on the machines that don't connect to the WLAN at boot, BOTH of them were experiencing the same issue under 7.10, and at no time did they ever reconnect to my WLAN automatically.  This may make no difference, but I wanted to be sure I was clear.

Thanks!

---

