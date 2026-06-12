---
title: "What does net.ipv4.tcp_app_win do exactly?"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by pacawaca on 2013-10-12
Hello all,

I'm new in all this tcp-ip stuff. At my University, I was asked to optimize tcp for some specific scenarios, and they gave me a list of parameters I was able to change. One of them is net.ipv4.tcp_app_win, but I'm not sure of understanding what that parameter do. According to man tcp:

> 
              This variable defines how many bytes of the TCP window are reserved for buffering overhead.


              A  maximum  of  (window/2^tcp_app_win, mss) bytes in the window are reserved for the application buffer.  A value of 0 implies
              that no amount is reserved.


Is that TCP window the receive window, or the congestion one? Thank you!

---

