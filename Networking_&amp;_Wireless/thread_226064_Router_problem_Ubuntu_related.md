---
title: "Router problem Ubuntu related?"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by uzd4ce on 2006-07-30
I have a new D-Link WBR-2310 router.  The logs show that the wireless connection to the laptop is reconnecting just about every two minutes.  

Am running NetworkManager.  I can't see the connection drop and reconnect from the laptop side, but my friend says he sees me relogin to instant messenger each time.  Occasionally I see the signal strength drop to 30% or so, but it doesn't seem to drop completely.

The laptop is running Ubuntu 6.06.  I've tried a couple differnet firmwares on the router, and also two different wireless cards, with the same result.  

Does this problem sound familiar to anyone?  I'm tempted to throw my saved Vista Beta image back on this machine to see if that helps, but I'd rather not.

Thanks,
Uzd4ce

Sample router log:
Jul/30/2006 11:31:57 	Wireless PC connected			00-0f-3d-4d-13-b1
Jul/30/2006 11:29:55 	Wireless PC connected			00-0f-3d-4d-13-b1
Jul/30/2006 11:27:53 	Wireless PC connected			00-0f-3d-4d-13-b1
Jul/30/2006 11:25:50 	Wireless PC connected			00-0f-3d-4d-13-b1
Jul/30/2006 11:23:48 	Wireless PC connected			00-0f-3d-4d-13-b1
Jul/30/2006 11:21:46 	Wireless PC connected			00-0f-3d-4d-13-b1
Jul/30/2006 11:19:43 	Wireless PC connected			00-0f-3d-4d-13-b1

---

### Post by malegria on 2006-07-30
The router has nothing to do with your operating system. The problem is the router not Ubuntu. I had the same issues with a router and found the issue in both Windows & Ubuntu.

---

### Post by LookTJ on 2006-07-30
i got that earlier today...checking for attacks and such i cant see it

---

### Post by uzd4ce on 2006-07-30
> **malegria said:**
> The router has nothing to do with your operating system. The problem is the router not Ubuntu. I had the same issues with a router and found the issue in both Windows & Ubuntu.

I was just thinking that maybe the problem wasn't router-based at all, but rather the connection being dropped from the laptop side for some reason.

---

### Post by Swab on 2006-07-30
Try messing around with the beacon interval, thresholds, preamble type settings on the router..  try changing wireless channel also.

---

### Post by uzd4ce on 2006-07-30
Thanks for the tips.

Is there somewhere on the laptop that I can see logs of the wireless connection?

---

### Post by uzd4ce on 2006-07-30
Ok, so now I'm more confused as to whether it's even a problem or not.  

I fired up Networking Tools and told it to ping the router repeatedly.  I watched it for a couple of minutes and it never blipped, even though the router logs showed two separate reconnections in that time.

---

### Post by Swab on 2006-07-30
> **uzd4ce said:**
> Ok, so now I'm more confused as to whether it's even a problem or not.  

I fired up Networking Tools and told it to ping the router repeatedly.  I watched it for a couple of minutes and it never blipped, even though the router logs showed two separate reconnections in that time.

Maybe its dropping the connection during times of inactivity?  I would try raising the beacon interval number on the router.  As I understand it, the beacon is like a sort of pulse for your wireless network, raising it from 50 to 100 might help.

---

