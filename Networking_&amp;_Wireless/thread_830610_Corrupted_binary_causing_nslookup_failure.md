---
title: "Corrupted binary causing nslookup failure?"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by johnzbesko on 2008-06-16
I developed a bizarre problem. I am unable to browse the internet. I successfully receive a dhcp IP and default gateway. I can mount a remote NFS share. My eth1 is bridged and within a virtual machine, I can browse the internet. I can also browse if I boot a Knoppix CDROM.

Therefore, I conclude my physical network is working, but something on the software side is messed up. The command, "nslookup cnn.com" returns an error, "no servers could be reached." Typing an IP address in the Firefox address box results in "Though the site seems valid, the browser was unable to establish a connection." The command "iptables -L" shows that everything is accepted and forwarded. (This PC is not my internet server ;-)

So, what could possibly be the matter? If some binary got corrupted, what packages should I attempt to reinstall? I'm running Kubuntu 8.04 x86. I'm at wit's end!

Thank you for your help.

---

### Post by johnzbesko on 2008-06-17
The mystery deepens. The problem is related to the system settings GUI on the Kubuntu start menu. When I set my network device to be manual with a static IP, the change doesn't "take" but when I reboot, I'm able to connect to the internet, even though I'm receiving a DHCP IP. Maybe there is a bug with System Settings?

---

