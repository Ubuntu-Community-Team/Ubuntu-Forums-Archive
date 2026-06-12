---
title: "Really basic problem using ndiswrapper"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by skecherkid on 2006-08-07
I've been trying to follow the many posts and threads already here about installing ndiswrapper and drivers.  I read the ndiswrapper Wiki but instead of obtaining the ndiswrapper package from the link there, I found my ubuntu installation already included it so I did a "sudo modprobe ndiswrapper" to load it.  That worked and its in my list when I do a sudo lsmod.

However the next step to install my winXP driver is to issue the command "sudo ndiswrapper -i /home/me/blah/NETPRISM.inf" but what I get is
sudo:  ndiswrapper: command not found

Soooo  my problem is very basic...  what have I not done?  Did I have to actually get, compile the sourceforge ndiswrapper code?  I have the ndiswrapper.ko in an existing directory so I didn't want to stomp on my ubuntu version unecessarily.  

Argh so near and yet so far it seems.

---

### Post by skecherkid on 2006-08-07
I also did not try to install ndiswrapper_utils.  I just tried to locate that on my ubuntu install and I don't see them.  Is it the ndiswrapper_utils that is needed for the command line?

---

### Post by bensexson on 2006-08-07
Yes, you will need ndiswrapper_utils.  That will install the ndiswrapper util.

---

### Post by darkshadow on 2006-08-07
just incase you don't realize it it is ndiswrapper-utils notice the - instead of a _
Some people would not realize then never find the package

---

