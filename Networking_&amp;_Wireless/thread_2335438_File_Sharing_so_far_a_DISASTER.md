---
title: "File Sharing so far a DISASTER"
date: 2016-08-28
forum: Networking &amp; Wireless
---

### Post by 2468rocks on 2016-08-28
I want to move files from Microsoft to Ubuntu. I have tried a few how-to articles on the topic of sharing, but I run into problems I do not know how to resolve. I have too many files to move to use sneaker-net or email.

The laptop is a Lenovo Flex 2-15D formatted NTFS running Win7. After building a number of desktops and installing Ubuntu without issue, it never occurred to me that a computer could be incompatible with Ubuntu, but the Flex 2 will not load or run Ubuntu. After this discovery, I tried to return it to the store but because I had screwed up the Win8 installation they would not accept the return, so I installed Win7 and gave it to my mom.

My desktop is based on an Asus M4A89TD Pro, formatted ext4, running Ubuntu 14.04 Gnome and a USB WiFi.

Both computers have internet connectivity over an N router. I also have a crossover cable as an option if that would be easier.

Any help greatly appreciated.

---

### Post by TheFu on 2016-08-28
Install openssh-server and fail2ban on the Ubuntu machine. The ssh-server provides ssh, sftp and scp servers all on the same port.

Use WinSCP from Windows to connect to it with the Linux account/password. Drag and drop files from Windows to Linux.

Wifi will make this slow. Use wired GigE network, if possible. Wired networking is **always** faster.

If you won't know much about networking, use the IP addresses for the systems in the connection. Both should be on the same subnet, to make it easy. You can do this over the internet, but that is harder (too hard for many people).

Using wifi means having to leave the file transfers going overnight. GigE would be about an hour.

---

### Post by 2468rocks on 2016-08-28
@TheFu... Thank you for the help so far. I never came across this method in Google.

So far I've installed openssh-server and fail2ban to Ubuntu using the software center, and I've installed WinSCP to the Win7 machine.

I'm lost from here. I tried looking up the internal IP on Ubuntu but when I click on System Settings, the system gives me a message about an internal error even after a reboot. I never had that trouble until I upgraded from 12 to 14 today. Even if I knew the internal IP, I don't know where to enter it.

EDIT: I just remembered my Ubuntu machine is 1 number off of the Win7 machine, used that, it's working now. THANK YOU!!!

---

### Post by TheFu on 2016-08-29
You are using sftp, hopefully. It is secure and how Unix people transfer files. Windows doesn't have something like that, which is why you've never heard about it before. Pretty much all the built-in Windows-ways to transfer files aren't secure.

If you are going to have a network, it would be nice to make it so you can use "names" instead of IP addresses locally.  Many home routers can make this easier.  [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)  IMHO, this is the first and most important step to having a network.You can also use /etc/hosts to tell the machines about each other, but if they are using DHCP, then the IPs can change.  At home, all my devices have IPs that don't change using "DHCP Reservations" for the portable devices like smartphones and laptops. For servers and desktops that don't move, I just setup static IPs in their network configuration. That is easier for me.
Having static IPs on the internal LAN is necessary if you want to access these files over the internet.

Anyway - glad it is working and doing what you need.  This is the easiest way that I know.  Usually people would setup something called "samba" for Windows to access Linux storage, but that is much harder with subtle configuration settings that aren't always easy to figure out.  Plus samba doesn't really have much security.

---

