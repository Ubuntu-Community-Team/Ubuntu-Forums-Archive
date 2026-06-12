---
title: "Find mac address of wireless adapter?"
date: 2014-11-10
forum: Networking &amp; Wireless
---

### Post by w.allen on 2014-11-10
Hi, I'm very new to Ubuntu.

I'm running Ubuntu 14.04 on a Dell Latitude D630 (About seven years old), originally designed for Windows XP.

I can't seem to figure out the MAC address of my wireless adapter.

I've browsed the web and this forum, but I can't seem to find anything that really explained well enough for me to understand, or it just doesn't apply to me.

Ask me for any information I may have not provided that is necessary to formulate a solution to my problem.

Thanks.

Note: Multitasking right now, may be late on reading replies and posting further replies.

Note II: I forgot to mention that my wireless hasn't been set up yet/I'm having problems, being that I'm searching for the MAC address due to advice from a friend. Using ethernet right now.

---

### Post by papibe on 2014-11-10
Hi w.allen. Welcome to the forum ):P

Graphical way: open 'Network Connections' and then press edit on your wireless connection to see the details.

Terminal: open a 'Terminal' and run this command 'ifconfig'. Your wireless interface probably would be called wlan0.

Hope it helps. Let us know if you have more questions.

Come here often and have fun.
Regards.

---

### Post by w.allen on 2014-11-10
wlan0 did not show.

Should I post the code? 

I am thinking it is something wrong with my computer.

---

### Post by The Cog on 2014-11-10
sometimes **ifconfig -a** can show interfaces that aren't fully working that plain **ifconfig** doesn't show.

Or **lshw** lists hardware and gives the MAC address as the serial number.

Or **ip link** might show something.

---

### Post by Hadaka on 2014-11-10
Hi, you may also find it by clicking
[B]System settings >> Network>>Wireless
[/B]This will display your..
Hardware Address:  MAC Address
 .........IP Address:   IP Address

---

