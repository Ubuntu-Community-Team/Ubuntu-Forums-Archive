---
title: "Old NE2000 (ISA) network card - not starting !!!"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by Larry57 on 2006-10-20
Have spent many hours troubleshooting this problem! Initially I installed W98SE to see if this was a viable system. All looked good, no extra drivers required.

The xubuntu server install did not recognise the NE2000, so I continued and after considerable googling found that the 'ne' driver actually worked. I then set up an alias entry in the '/etc/modules' with just 'alias eth0 ne'.

'modprobe eth0' still failed with "SIOCSIFADDR: No such device" error, so I tried 'modprobe ne' and this installed the driver and 'ifconfig -a' showed a eth0 entry, but no IP address.

So looked in /etc/network/interfaces, there was only a 'loopback' entry. So added:
             auto eth0
             iface etho inet dhcp

Rebooted and still no eth0 with 'ifconfig -a'. Look for 'ne' with lsmod and it wasnt there (must be hiding, hmmm). Manually loaded it with 'modprobe ne' and then lsmod'ed and whaalaaa its there and ifconfig shows a IP address as well. Then ping a remote host and that works too. Great.

Rebooted and all is hiding again; blast!  Tried the manual start with 'modprobe ne' and ALL is working, can ping, blah blah.

As a cludge, I put '/sbin/modprobe ne' into the top of the '/etc/init.d/networking' script and now all works on reboot.

***************
A question for the developers:
My question is: What is the proper way to have the ISA ne2000 card started?

---

### Post by helpdeskdan on 2006-11-14
I wonder why has nobody resonded to this?  This is not a hard question.  You add ne to the lists of modules in /etc/modules.  Hope that helps. :)

---

### Post by bjd on 2006-11-14
you can add it to /etc/modules to have it auto load a boot.

-- doh just noticed larry actually answered the question :-p

---

