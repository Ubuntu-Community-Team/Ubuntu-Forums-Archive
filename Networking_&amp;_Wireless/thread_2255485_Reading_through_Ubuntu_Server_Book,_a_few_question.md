---
title: "Reading through Ubuntu Server Book, a few questions"
date: 2014-12-05
forum: Networking &amp; Wireless
---

### Post by Deneol on 2014-12-05
I am trying to understand the networking in Ubuntu. My questions will probably seem very basic because I am novice at this.
   
  I do not understand the syntax in the /etc/network/interfaces file.
   
  The default is:
  ```
auto lo

  iface lo inet loopback

```   
  I read that ```
auto
``` on line 1 says the ```
lo
``` interface should be loaded automatically at boot. The second line defines the ```
lo 
```interface. So ```
lo
``` on line 1 refers to definition of ```
lo
``` on line 2.

   
  What other options are available here?


  I read that this:

   
  ```
auto eth0

  iface eth0 inet dhcp


```   

  would, like the example above, start the ```
eth0
``` interface at boot. But what else can be started? What other options besides ```
lo 
```and ```
eth0 
```exist? And does ```
inet 
```stand for? What other options besides ```
loopback 
```and ```
dhcp 
```exist? Are any other definition types besides ```
iface 
```available?

  
A related question:

  Is ```
Subnet Mask 
```on Windows (given by ipconfig)the equivalent of ```
netmask
``` on Ubuntu (given by ifconfig)?

(Sorry that this came out looking so bad, I don't know how to put [CODE] text inline!)

---

### Post by slickymaster on 2014-12-05
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by steeldriver on 2014-12-05
AFAIK the available interfaces are the ones that are detected at boot time (by udev...?) and hence appearing in the /sys/class/net directory

```

ls /sys/class/net

```

For your other questions, have you looked at the online manual page?

```

man interfaces

```

It may not be 100% up to date, but it should give you the basics, for example it tells us that

```

       Stanzas defining logical interfaces start with a line consisting of the
       word  "iface" followed by the name of the logical interface.  In simple
       configurations without mapping stanzas this name should simply  be  the
       name  of  the  physical  interface  to which it is to be applied.  (The
       default mapping script is, in effect, the echo command.)  The interface
       name  is  followed by the name of the address family that the interface
       uses.  This will be "inet" for TCP/IP networking,  but  there  is  also
       some support for IPX networking ("ipx"), and IPv6 networking ("inet6").
       Following that is the name of the method used to configure  the  inter&#8208;
       face.

```

---

