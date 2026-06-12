---
title: "Bluetooth Internet Connection Sharing"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by karlhm76 on 2008-08-21
Hi All,

I'm having problems getting this to work on Hardy on my eee. I previously had it working in Gutsy on my desktop.

I do the 'sudo modprobe bnep'
then I do the 'sudo pand --connect <bt address>' and it connects!

ifconfig bnep shows I have an IP address
netstat -r shows routes for bnep0 which all look ok.

I can ping across the internet by name (ping [www.google.com.au](www.google.com.au) works!). Excitement builds..

Then I open firefox and it all stops working! arrg..! :confused:

The syslog says something about ipv6 routers not present or something. After that I can't ping anything outside.
ping [www.google.com.au](www.google.com.au) just waits forever and if I ping by address it comes back saying destination unreachable.

What am I doing wrong?

---

### Post by diafygi on 2008-08-30
I am trying to achieve the same thing. Have you found an answer yet? I am trying to figure out how to do it with [Blueman Bluetooth Manager]("http://blueman.tuxfamily.org/").

So far, I have been able to establish a connection with my wireless phone (which has internet connection sharing), which creates a bnep0 entry in my ifconfig. Then, if I go to System>Administration>Network and set the bnep0 properties to DHCP, I get an ip address for the connection (verified through ifconfig). So, it appears I'm at the same step as you.

How can we get an internet connection from here?

---

### Post by diafygi on 2008-08-30
Okay, I found a difference between your setup and mine. I use the command:
```
~$ sudo dhclient bnep0
```
to get an ip address (I used the [blueman tutorial]("http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=58")). But that shouldn't make a difference, since we both get ip addresses.

I can confirm that we are able to ping out with the ip address. I was also able to wget an html page from my personal website. So that means we have internet connectivity, but Firefox doesn't know it. How can we get Firefox to recognize we have internet connectivity?

Oh, to release the ip address from bnep0, I use the command:
```
~$ sudo dhclient -r bnep0
```

---

### Post by karlhm76 on 2008-09-08
Ok, I've had no new ideas to try, and subsequently had no success. Bluetooth connection sharing working perfectly on Gutsy is taunting me.. but I have some theories. 

I've found that its not only Firefox that kills the connection but anything I run in Gnome that accesses the internet does.

Anything in the terminal works fine, I can even apt-get and install software no problems.

So it seems the connection is limited only to the bounds of the terminal!!

And as soon as Gnome or X or whatever tries to access the connection it just dies and can't be salvaged without killing pand and stopping and restarting bluetooth.

That's diabolical, but how to fix this?

---

### Post by karlhm76 on 2008-09-08
Oh, and I also tried starting applications from the terminal that run in gnome and it made no difference, it still killed the connection.

---

### Post by diafygi on 2008-09-08
> **karlhm76 said:**
> That's diabolical, but how to fix this?

I've been trying to figure that out, too. Does anyone know how to troubleshoot this? I installed the test version of Intrepid (Alpha 5) to see if the new Network Manager (0.7) would help, but Blueman doesn't work with the new version, so back to square one.

Anyone know how to troubleshoot this problem of selective connectivity?

---

### Post by karlhm76 on 2008-09-25
i was surfing around and found this site. 
[http://peterbouda.blogspot.com/2008/04/linux-eeepc-and-windows-mobile-internet.html](http://peterbouda.blogspot.com/2008/04/linux-eeepc-and-windows-mobile-internet.html)

one of the comments looks very interesting; it mentions some code to put into /etc/network/interfaces that is meant to make the PAN connection available to the GUI. 

when i try it i get errors which say the system cant read the interfaces file when using anything network related but perhaps some kind soul can decipher it.

This allows PAN connection trough the GUI. It works (don't trust the error msg).

```

iface lan5 inet manual
down dhclient3 -r -pf /var/run/dhclient.bnep0.pid -lf /var/run/dhclient.bnep0.leases bnep0
down ifconfig bnep0 down
up pand -e bnep0 --search
up ifconfig bnep0 up
up dhclient3 -cf /etc/dhcp3/dhclient.$LOGICAL.conf -pf /var/run/dhclient.bnep0.pid -lf /var/run/dhclient.bnep0.leases bnep0

```

---

### Post by karlhm76 on 2008-09-26
I've kind of given up on this and written it off to something that was broken from gutsy to hardy. Its happened before and bluetooth seems to be the most affected during dist upgrades - I've been a heavy user of bluetooth since edgy.

I eventually managed to get the mobile phone working as a modem using a USB cable and installing the latest rndis-lite from subversion.

When I did this I noticed something very interesting:

Upon the first time I connected using the USB cable I didnt have the rndis0 interface set up for roaming mode and I noticed the connection would not work outside of the terminal window - exactly the same problem for the bnep0 interface.

However as soon as I enabled roaming mode the connection appeared in network manager and I was able to select it as a connection. Then magically firefox and everything started working!

As a hunch I tried the same thing with the bnep0 interface and it didn't work - network manager would not add the interface. Obviously the problem lies with getting the bnep0 interface into network manager so it can be recognised.

It is also interesting to note that on my gutsy box where bluetooth internet connection sharing DOES work, the bnep0 interface appears in network manager.

So I have a feeling if I install the same network manager as I have on gutsy I may in fact be able to get this thng to work.

For the moment though I'll press on using the ugly USB cable. From past experience playing with network manager only results in sadness.

---

