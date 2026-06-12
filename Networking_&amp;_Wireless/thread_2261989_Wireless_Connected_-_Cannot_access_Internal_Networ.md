---
title: "Wireless Connected - Cannot access Internal Network / Router"
date: 2015-01-22
forum: Networking &amp; Wireless
---

### Post by Omar_Zaki on 2015-01-22
I installed Ubuntu 10.10 onto an old Intel Macbook according the instructions found here ([https://help.ubuntu.com/community/MacBook2-1/Maverick](https://help.ubuntu.com/community/MacBook2-1/Maverick)), but I am unable to properly connect the intranet and Internet via WiFi.

I performed a fresh Ubuntu 10.10 install onto the laptop.  I can connect to my wireless router using the network manger, and the computer reports that I am connected.  Using DHCP, I am issued a sane IP address.  When I have the network settings set to "DHCP Automatic", I am unable to access any intranet or Internet resources.  When I try to ping the router, internal IP address, or external named address, I get a message saying the destination is "unreachable".  **I am able to ping an external IP address outside of my LAN**.  When I manually define the DNS server to a public DNS such as 4.2.2.1, I can access named Internet addresses, but no internal network resources are reachable.

I followed the instructions on this thread ([http://ubuntuforums.org/showthread.php?t=1574877](http://ubuntuforums.org/showthread.php?t=1574877)) which describes exactly the same problem.  In that thread, the Internet access problem was solved by setting the DNS manually, but I don't believe the OP actually had the internal intranet problem solved.  I believe this is an issue between my router and my computer.

A couple of additional details:
[LIST]
[*]I connected my laptop to a neighbor's unsecured wireless router, and I was able to access the Internet without any manual configuration.
[*]My router is a Netgear R6250 with WPA2-PSK [AES] security.  I turned security off entirely and had the same results.
[*]I have many systems on my network, and I haven't experienced this issue.  I have Android, Windows, Mac, and a Roku on the wireless network.  I have a CrunchBang linux computer connected to the network via ethernet.
[*]I looked at the router logs, and the router is issuing my Ubuntu computer an IP address.  The address is the same one the computer reports itself as having
[*]When I look at the "attached devices" on the router, my Ubuntu computer is not listed.  Contrast this with the above bullet.
[/LIST]

Do you know how I should go about troubleshooting this issue?  Any help is greatly appreciated.

---

### Post by ajgreeny on 2015-01-22
I would first suggest that there is little point trying to troubleshoot your problem as it will be just about impossible to work with 10.10 any more; it lost support almost three years ago and the repositories are not available without editing the sources.list file.  Even if you do that no updates will be available.

You ought to get and use a newer version but as I have no experience of macbooks, I don't know which version is best for you but I suggest you look at 14.04, the latest LTS version.  This may have updated drivers for the wireless adapter in the laptop, which is, I think, where your problem comes from.

---

### Post by Omar_Zaki on 2015-01-22
Thank you for the reply, ajgreeny.  It's ironic - I bought this router because I got a new Macbook Pro for work, and it didn't play nice with my 2006-era wireless router.  Now I'm having the same issue in reverse.

I am worried a more modern OS won't run well on this machine, but I understand about losing support.  I'll install Ubuntu 14.04, and if that has performance issues, I'll try a more lightweight distro.

Thanks again!

---

