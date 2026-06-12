---
title: "Ubuntu DNS behaviour"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by John_T on 2008-02-02
I'm a little confused as to networking interoperability between Ubuntu and Windows hosts on a LAN.

I have:
2 Ubuntu 7.10 machines
2 Windows machines, 1 XP, one Windows 2000
A Netgear router providing DHCP and the shared ADSL internet connection

None of the machines have any internet connection or browsing issues.
The Windows machines can see and ping each other and the Ubuntu machines by hostname or IP address.
The Ubuntu machines can only ping other local machines (Ubuntu or Windows) by IP Address.
I can log into the Ubuntu machines using tightvnc viewer from the windows machines using the Ubuntu machines hostname.
I can log into the Ubuntu machines using tightvnc viewer from another Ubuntu machine, but have to  use the IP address.

Is this normal / expected behavior?

On the Ubuntu machines, I have installed zeroconf.
The netgear router's IP address is listed in the[FONT="Courier New"] /etc/resolv.conf[/FONT] file

I found [this thread]("http://ubuntuforums.org/showpost.php?p=515404&postcount=14") about using winbind, but it seems a little old,.and I thought I'd check with others before forging ahead.

If push comes to shove, I can create static IP's for all the machines and add entries to the hosts files, but it seems strange that I have to go to such extents.

Any feedback would be appreciated.

---

### Post by kurtpete on 2008-02-02
Despite that thread you mention being old, it worked perfectly for me in a mixed windows/ubuntu (4 windows xp machines, 1 gutsy laptop, 1 gutsy pc (both 64 bit)) LAN environment.  Just completed those two steps (install winbind, edit nsswitch.conf) and I get name resolution on gutsy of all machines on the LAN.

---

