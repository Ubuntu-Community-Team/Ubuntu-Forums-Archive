---
title: "Dell XPS 16.04 Changing wired/wireless internet stops working"
date: 2017-04-05
forum: Networking &amp; Wireless
---

### Post by pingram3541 on 2017-04-05
Whenever I switch from wired (usb dongle) to wireless (built-in) or vice versa (not always, but _mostly_ always) I lose name resolution/other network services even though I can check the DHCP connection info via the gui and verify that I do indeed have a valid and usable IP address provided via my DHCP server.  The gateway and DNS where the primary is my router IP, i.e. 192.168.1.1 and secondary DNS is public 8.8.8.8.  Both are setup DHCP.

When this happens, I can often ping IP addresses but resolving name doesn't work. My browser says I have no internet connection.  Other times when I change connections it's as if the entire network stack doesn't work, for example, ping from the command just hangs even with valid IP addresses and not just names.

I also disable wireless when plugging in Ethernet and vice versa so both are not connected to the same network and IP scheme at the same time but in reality it would be optimal if I didn't have to worry about if wireless is enabled while I am wired in to the same network, the stack should be intelligent enough to know it is the same subnet and to use the faster more reliable connection.  This would be more seamless when moving away from my desk and back without extra steps on my part.

!Important note - Rebooting always fixes this issue!

Additionally, if I don't switch connections and work entirely off wireless or I work entirely off Ethernet, I never have any issues and everything is peachy keen.  Any help is greatly appreciated.

---

### Post by wildmanne39 on 2017-04-05
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here, which is where the file will be posted.

Please post one from when it is working and when it is not working, I am not sure I can help with this issue but I will do my best and if not the information will help someone else to help you.

---

### Post by pingram3541 on 2017-05-05
Thanks, I gave it some time but now I can't reproduce this problem which seemed to happen inconveniently every time I was on a customer's site troubleshooting...Murphy's Law I suppose.  One thing you might be able to answer.  Is it possible to use the IP assigned to a NIC when it is not plugged in like in Microsoft products?

For example, say I'm running a local instance of a virtual machine with a static IP of 192.168.1.100 and I want to access a web server running on that instance.  I can set my host NIC with an IP address of 192.168.1.101 for example and then assign a class C subnet.  When I am plugged into anything, regardless of whether anything else is on that subnet I can access the web server on my local virtual client but if I unplug the Ethernet connection I cannot.

Is it necessary to carry a loopback just to access local IP's when not connected to a physical network?

---

