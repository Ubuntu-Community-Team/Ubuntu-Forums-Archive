---
title: "NETGEAR WG511v2 - Poor signal quality 3 feet from router"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by Jeconti on 2008-07-21
I've used the forums to successfully install a NETGEAR WG511v2 PCMIA wireless card on to my Dell Latitude C600.

I'm sitting about 3 feet from the AP at the moment, and I'm showing a signal quality of about 58/100.

Is this a driver/installation error that I'm seeing, or is my PCMIA card junk?

---

### Post by komputes on 2008-07-22
Do you experience actual cuts in the connection or does it just display that the signal strength is low? Do you see other access points with higher signals even though they are further? What kind of wireless card are you using (with what driver)?

---

### Post by Jeconti on 2008-07-22
It's just very low. The connection does not cut out. Although since my last package update the card sees both APs that I have in my home, and will connect to them, but will not access the internet.

Card is a Netgear WG511v2 PCMIA card, made in China.
I used the drivers availible for download from [this thread]("http://ubuntuforums.org/showthread.php?t=483000&page=4").

---

### Post by Jeconti on 2008-07-22
UPDATED: The problem with connecting to the internet now appears to be confined only to the Xfce desktop environment.

However, sitting next to the router, I'm still only getting 60% signal quality.

---

### Post by komputes on 2008-07-22
I'm guessing this is either the work of the Netgear drivers or NDISwrapper. As long as you can get wireless to the same distance (range) I would say that the signal strength is just being interpreted incorrectly by one of these two. Keep in mind NDISwrapper is a hack/workarround to make Windows drivers work in Linux, and sometimes it work great but it's not perfect. I would do this test with another access point as well. This would also require comparison tests with the same driver in windows. That's the best I've got.

---

