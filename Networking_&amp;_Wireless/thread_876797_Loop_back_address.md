---
title: "Loop back address"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by sulekha on 2008-08-01
Hi all,

The following is the definition of loop back  address ,i saw in the book tcp/ip guide

special range of addresses ,127.0.0.0 to 127.255.255.255 , is set aside for loop back functionality.IP datagrams sent by a host  to a 127.x.x.x loop back address are not passed down to the data link layer for transmission,instead they loopback
to the source device at the IP level. In essence this short circuits the normal protocol stack; data is sent by a device's layer 3 IP implementation and immediately received by it.

This loopback range is used for testing the TCP/IP protocol implementation on a host. since the lower layers are short circuited ,sending to a loopback address allows you to isolate and test the higher layers ,IP and above without interference from lower layers. 127.0.0.1 is the address most commonly used for testing purposes  

now my question is as follows

1)This loopback range is used for testing the TCP/IP protocol implementation on a host. since the lower layers are short circuited ,sending to a loopback address allows you to isolate and test the higher layers

can any  one give example(s) for this or a situation where this is used ?

---

### Post by tamoneya on 2008-08-01
If i install an apache server on my computer and I want to test it without going to another computer I can open firefox (or any web browser) and go to 127.0.0.1 and I can see if everything is configured right.

---

### Post by Iowan on 2008-08-01
```
ping 127.0.0.1
```
[http://what-is-what.com/what_is/127.0.0.1.html]("http://what-is-what.com/what_is/127.0.0.1.html")

---

