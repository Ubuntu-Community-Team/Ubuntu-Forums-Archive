---
title: "ipsec-tools and openvpn not starting on boot"
date: 2016-12-19
forum: Networking &amp; Wireless
---

### Post by jcwjcw42 on 2016-12-19
I've had a couple networking problems during boot since I upgraded to 16.04 LTS from 14.04 LTS. The first is that it seems setkey (from ipsec-tools) is not starting correctly. The NFS shares listed in /etc/fstab do not mount correctly and it delays the boot by 1.5 minutes each time. Once I get booted and logged in I need to run

$ sudo service setkey restart; sudo mount -a

to get the mounts completed. (racoon seems to be running fine, though)

The second is that openvpn doesn't start. The cure to this is

$ sudo service openvpn restart

I'm able to ssh in once the mounts time out and restart everything if I'm accessing remotely, but it is a bit of pain to go through these steps on a couple machines after every security update. Any suggestions? I can any logs that may be relevant if you let me know what they are. (Running "grep setkey *" in /var/log doesn't reveal anything obvious.)

---

