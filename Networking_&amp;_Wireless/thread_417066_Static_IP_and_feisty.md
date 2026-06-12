---
title: "Static IP and feisty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by sunny boy on 2007-04-21
a big hola from a new convert,

I have used Ubuntu for about a year, and have just downloaded Feisty, and would love to try it!!
Snag is...i cannot get on line...I must use Static IP, and i cannot find a way of entering my numbers, it just refuses to accept!
I am still a beginner, and already i hate using Windows.
Any help available?

---

### Post by RandomJoe on 2007-04-21
What do you mean when you say it refuses to accept?  Also, do you mean when you are booted to the Live CD or have you gotten it installed already?

I just booted a machine w/ the Ubuntu CD and you should be able to set the IP by clicking on the network icon to the right side of the top toolbar (should appear as two monitor windows, if your connection is active).  The bottom option is "Manual configuration...", select that and the Network Settings window appears.  Select the network connection, click Properties.  Change the Configuration to "Static IP Address" then enter your IP information.

I have DHCP on my network, so I did run into a little issue where it kept wanting to use my DHCP-served IP.  Not sure if that might be your trouble.  I got it to use the fixed IP by going back into Manual configuration and unchecking the box to the left of the Ethernet adapter (disabling the interface), closing the window, then going back into Manual configuration and rechecking it.  When I did that, it came up using the fixed IP I entered.

---

### Post by wieman01 on 2007-04-24
> **RandomJoe said:**
> What do you mean when you say it refuses to accept?  Also, do you mean when you are booted to the Live CD or have you gotten it installed already?

I just booted a machine w/ the Ubuntu CD and you should be able to set the IP by clicking on the network icon to the right side of the top toolbar (should appear as two monitor windows, if your connection is active).  The bottom option is "Manual configuration...", select that and the Network Settings window appears.  Select the network connection, click Properties.  Change the Configuration to "Static IP Address" then enter your IP information.

I have DHCP on my network, so I did run into a little issue where it kept wanting to use my DHCP-served IP.  Not sure if that might be your trouble.  I got it to use the fixed IP by going back into Manual configuration and unchecking the box to the left of the Ethernet adapter (disabling the interface), closing the window, then going back into Manual configuration and rechecking it.  When I did that, it came up using the fixed IP I entered.
That's exactly the question I had... So Feisty DOES support the use of Static IP, right? The workaround you are referring to must be a bug then.

---

### Post by Erlander on 2007-04-24
After install I had some trouble getting it to accept my fixed Ip addresses on 2 pc's.  I found that if I set the router to DCHP and in network properties in Feisty and then changed the router back to DHCP off that I was then able to setup the fixed Ip addresses.

It may be something I had done or my setup but this worked for me and is still working.

Rob

---

