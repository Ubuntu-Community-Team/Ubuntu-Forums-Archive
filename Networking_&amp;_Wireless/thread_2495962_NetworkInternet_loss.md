---
title: "Network/Internet loss"
date: 2024-03-09
forum: Networking &amp; Wireless
---

### Post by oldhippie on 2024-03-09
Greetings all,
Serious Ubuntu newby here that needs some help getting the internet running on a new install of 24.04.4.
I've installed it on a dedicated drive in my Windows 10 machine and it installs fine and the network/internet works fine under DHCP. 
If I switch over to Windows, the network/internet still works but when going back to Ubuntu, it stops working but still works on Windows.
I've been reading and searching but need help understanding the terminal commands to figure this out. From what I have seen, it may be trying to use a wrong MAC address for the adapter when it is booted after a Windows session. I set up a admin user to work on this.
Could anyone point me to a good tutorial for this kind of thing? I want to understand it but hitting a dead end with all the terminal commands.
Thanks

---

### Post by TheFu on 2024-03-10
I haven't seen a MAC address matter in decades and even then, it was only with direct CATV ISP connections using a PCI card as the cable modem.  It never mattered if you have a home router and it hasn't mattered with my cable ISP since the 1990s.

Here's a link with commands to be run: [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) 
Run them in order and show your work back here, wrapped in forum 'code' tags.  That's in the advanced editor, use the "#" button just like you would a "B" (bold tag).

From your description, I'd guess you have a realtek NIC and that it will work if you completely power off  the computer (at least 10 seconds) before booting into Linux.  The realtek NIC drivers don't initialize all the device registers, so they are left over from whatever MS-Windows had.  I don't think the MAC as anything to do with it.  When dual booting, reusing the same MAC isn't an issue 99% of the time.

---

### Post by oldhippie on 2024-03-11
Thank you TheFu for the reply. I will work on the commands and try and post. I have tried the power off as well as unplugging the network cable to no avail. So far, the only way it will work and actually connect to the internet is with a new install of Ubuntu with the Windows drive unplugged.

---

