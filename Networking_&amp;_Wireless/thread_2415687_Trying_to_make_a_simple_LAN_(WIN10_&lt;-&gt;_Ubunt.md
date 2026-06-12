---
title: "Trying to make a simple LAN (WIN10 &lt;-&gt; Ubuntu)"
date: 2019-03-29
forum: Networking &amp; Wireless
---

### Post by mra90 on 2019-03-29
Hello,

I try to create a very simple local network between two of my laptops. One has windows 10 installed and the second one Ubuntu 18.04. 
Right now I am stuck on Ubuntu side, first of all I use external (USB) network card from Edimax and it causes a lot of problem. For setting the LAN I follow this article [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html) it says "...[COLOR=#445263][FONT=Arimo]replace eth0 with your network interface card[/FONT][/COLOR]" - and this is the place where I am stuck right now. When I type "lsusb" I don't see that external network card. If I unplug and plug it to other usb port it will show up for a while but another "lsusb" and its gone again...why is that? For the moment it is listed its record says "Bus 0001 Device 012 ID xxxx ASIX Elec. Corp. AX88179 Gigabit Ethernet"
So how should I replace eth0 with it?
Can you please guide me gow to set up this network properly?

Thanks in advace :)

---

### Post by TheFu on 2019-03-29
That article is very old and networking isn't configured that way on 18.04.  netplan is the newer method, not the interfaces file, which will be ignored.  When looking for how to accomplish things, it is important to use the release in your search.  There are a number of other issues, since the 2 computers, directly connected LAN is unusual and missing normal routing capabilities, DNS and DHCP.

Directly connected computers need to have manual routing rules setup to send packets at each other.  But a $10 router will handle that routing trivially and provide a dhcp server.  

Anyways, to see the current network devices, use either **ifconfig** or **ip addr** or **sudo lshw -C network**.  The 1st is becoming deprecated.  The 2nd makes ugly output and the last requires that a tool not usually installed be preinstalled.  There are other methods too.

BTW, I think I'm using the same USB3-to-GigE adapter and the device name for mine takes the unique MAC and appends it with "enx000".  My driver is driver=ax88179_178a according to lshw.

If I wasn't clear, the easiest solution to this is to get a cheap router, connect both systems to it, and all the connections, dhcp and routing between both computers will work.

---

### Post by mra90 on 2019-04-02
A router? Really? To connect just two laptop together I do need a router? o.0

Can't I create a very simple local LAN for these two?

---

### Post by TheFu on 2019-04-02
> **mra90 said:**
> A router? Really? To connect just two laptop together I do need a router? o.0

Can't I create a very simple local LAN for these two?

Yes, you can and I've stated what you must manually do to make it work, twice in my reply above.

I also suggested that a $10 router would do those things, but which method you go is completely up to you.

I don't use 18.xx releases, so I don't feel confident in providing more instructions. Sorry.

---

