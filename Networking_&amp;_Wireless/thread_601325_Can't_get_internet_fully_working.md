---
title: "Can't get internet fully working"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Andos on 2007-11-03
I recently installed Ubuntu 7.10 on my Dell Inspiron 1520 which has built in wireless.  My wireless card was supported "out of the box" and it connects to my router fine.  To start with I couldn't view any websites but turning off IPv6 in Firefox fixed this.

However, when I use apt-get/Synaptic/Update Manager I can't connect to any of the repositories.  I also can't use wget or ftp from the terminal as they time out and can't connect.  I tried disabling IPv6 system wide, and added my ISP's DNS servers to /etc/resolv.conf  but I still have this problem.  Can anyone help me please?

---

### Post by charles woodward on 2007-11-03
I've posted a possible solution to your problem on the `problems connecting to network on boot..` thread.

I am assuming that the problem you are getting is the same as almost everyone else - if you connect to the internet you have slow speeds, or you keep dropping your connection.  Sometimes you cannot connect at all, but `iwlist scan` picks up the router - so the hardware is working.  

Try that solution - I picked it up from various threads and it does seem to solve a lot of problems.

---

### Post by Andos on 2007-11-03
Thank you very much Charles, the second fix worked a treat!  Must be my flaky router, I've had trouble with it scrambling DNS settings on Windows as well!

---

