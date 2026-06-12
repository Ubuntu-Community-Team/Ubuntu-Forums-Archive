---
title: "RAlink ra61 wireless issue"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by gbpacker on 2007-01-17
Hello,

I tried following the instructions from the following link on my AMD 64 bit machine. I am running drapper 6.06 version.

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

But my system is stuck while rebooting. It says:

Bringing up ra0
Internet Systems Consortium DHCP client V3.0.3
interface inet 0 upnt-script: line 155: 3716 killed ifconfig $interface int 0 up

And it hangs here.

Can anyone pls suggest how to revert back the changes or how do I bypass this step?

Thanks

---

### Post by cal6n on 2007-02-03
*Bump*

I'm having this issue too.

Any suggestions

*edit* Found it!

Towards the end of the instructions mentioned:

> 
(a) Do not use the "Networking" tool (network-admin). You will get a lock-up at boot time at the point where the network interfaces are bieng configured. If you have used the Networking tool, you will have to comment out the entries in the file "/etc/network/interfaces." to do this:

Code:
$ sudo vi /etc/network/interfaces   # replace vi with your editor of choice (nano, gedit, kate etc.)
it should look like this:

Code:
auto lo
iface lo inet loopback

#iface ra0 inet dhcp
#wireless-essid xxxx
#auto ra0



---

