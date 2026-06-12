---
title: "Diferent problems with fixed and dhcp configurations"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by bengy103 on 2015-02-16
Now here's a thing. I've just done a clean install of Ubuntu 14.04 lts on my workhorse machine. On another machine I have Ubuntu 14.04 server, where I keep the usual photos, music.........

After the new install I tried the server, but couldn't get it. The famous 'Failed to retrieve' message came up.
I pottered around on the Internet a bit, and then I had an idea. My server is fixed at 192.168.1.52, my gateway is 192.168.1.1, so I fixed my computer at 192.168.1.50 and bingo, there was my server. To continue my set up I tried going online, but I couldn't get online. I got a 'Server not found' or some such.

To sum up, when I have a fixed ip I can get my server, but not the internet.
When I have an ip given by dhcp I can get the internet but not my server.

I'll keep trying to sort it out but I'd be grateful for any helpful suggestions.

regards,

brawd

---

### Post by bengy103 on 2015-02-16
Yes once again it was the smb.conf addition of 'name resolve order' though I've never had it in this form before. In 14.04 you tuck it under the Workgroup = workgroup bit.

I really hope that this gets fixed soon. Ubuntu is way too good an OS to have such a snag lingering for so long and tripping me up. 

Maybe there is a reason for keeping it, I don't know.

regards,

brawd

---

