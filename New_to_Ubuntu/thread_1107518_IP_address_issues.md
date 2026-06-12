---
title: "IP address issues"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Tamnakz on 2009-03-26
I've been having a problem on the public network I use 3-5 times a week.

I've got internet at home, but it's slowly and rediculously limited. I can connect to my home network with no issues. I've tried removing the network, but it'll still recognize properly and assign an IP address.

The first time I had issues on the public network, I used the Ubuntu help. I have 8.10. It walked me through a few steps.
I was able to see the network.
I could not ping the network, not any other site.
It had me verify that my wireless devices were working, and that they were enabled.
The last thing it had me do is disable ipv6. I did this, and it worked.

A few days later I wasn't able to connect again, so I turned ipv6 back on, restarted, turned it off, tried changing EVERY option I could with network/wireless setting one at a time, and changed them back after they didn't work.

I can get on this network with my Windows laptop with no problem, and there are half a dozen other people on the network when I'm having issues.

Can anyone help me?

---

### Post by superprash2003 on 2009-03-26
post output of the following commands from the terminal
1)iwconfig
2)ifconfig

---

### Post by Tamnakz on 2009-03-29
> **superprash2003 said:**
> post output of the following commands from the terminal
1)iwconfig
2)ifconfig

Thanks, but I found someone in the irc that was able to help me.

Still don't know what the problem was, but he helped me revert back to all default settings, eveyhing is peachy so far. . .

---

