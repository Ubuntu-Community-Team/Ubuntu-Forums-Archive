---
title: "Speeding up DSL Broadband"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by Sierra_Dave on 2007-01-02
Hi,

Another brain fart...I cant remember how to edit the file in order to get this fix for DSL speed:

"Add the following to /etc/sysctl.conf (substituting your window size in place of 524288, if necessary):

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

Then to have the settings take effect immediately, run:

sysctl -p"

I need the command to get to the point where I can add the above text.
Thanks for any Help!
Dave](*,) ](*,)

---

### Post by LinuxJosh on 2007-01-03
just use [PHP]sudo gedit /etc/sysctl.conf[/PHP]

---

### Post by Sierra_Dave on 2007-01-03
Thanks LinuxJosh !! :)

---

### Post by gewitty on 2007-03-30
I've been running some tests on my broadband connection speed and discovered to my surprise that my Ubuntu (Edgy) box is running at **half** the speed of a Windows XP box on the same connection!

I tried installing the tweaks above and also disabled ipv6 as suggested ([https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)), but this seems to have made no difference. Can anyone suggest what the cause of the speed difference is and how I can correct it? 

I'm new to Linux, so stick to newbie language please :(

---

