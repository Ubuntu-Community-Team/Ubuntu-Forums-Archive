---
title: "Net connection"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by sunilkumar on 2008-09-09
I am very new to UBUNTU or Linux. This is my first experience.

Now that I got connection to internet after getting support from this forum. Whenever I restart the computer, the net is not connected automatically. I have to give always **sudo dhclient** command. What does that mean? How can I rectify this problem?

I read somewhere that the reason for slow net connection is the internet protocol ipv6 is enabled by default and most ISPs not enabled this latest standard. Is it true? Then how can I rectify that? How to revert to ipv4?


Regards,
-S-

---

### Post by tbehrens on 2008-09-09
> If you're having problems in Synaptic or Firefox, if you're a newbie like me, here's the process at it's most basic:

ipv6 is a protocol not handled by many routers. It's new and will be needed someday (which means a long time from now (like years) you're gonna have to buy a new one. In the meantime, config linux not to use it by:

1. Open a Terminal Window
2. Type sudo gedit /etc/modprobe.d/blacklist
3. In the gedit window at the end of the file, type: blacklist ipv6
4. Save the file and reboot.

To make sure you no longer have ipv6 running, open a terminal window and type:
ip a | grep inet6

Many thanks to mhael for this process!

Try ^ this.

---

### Post by Iowan on 2008-09-09
Check the **/etc/network/interfaces** file for an "auto eth0" line. Another option might be to set up your network connection for DHCP (instead of Roaming, static, or zeroconf.

---

### Post by sunilkumar on 2008-09-10
> Check the /etc/network/interfaces file for an "auto eth0" line. Another option might be to set up your network connection for DHCP (instead of Roaming, static, or zeroconf.

Ya, my question is how can I do that? I configure through Ststem>Network Tools. Still everytime I have to give sudo dhclient command. Infact what is this command, I dont know!

Configuring ipv6, let me try in the evening.

Regards,
-S-

---

