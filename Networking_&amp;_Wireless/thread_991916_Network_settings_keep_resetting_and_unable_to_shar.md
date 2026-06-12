---
title: "Network settings keep resetting and unable to share folders."
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by AceRimmer on 2008-11-24
Hello. since installing 8.10 I have this problem.  I go into network settings and change my wired network connection to manual, set the IP, subnet, gateway and DNS to the proper settings for my router.  Bingo the connection becomes active and I can browse the net.  When I reboot I find that the network icon will tell me its disconnected and when I go check the settings its back to automatic DHCP and my old settings are gone.   

Also when I go to share a folder it keeps telling me I have to install software to do it, SMB, but it opens an installing window with a progress bar that just closes after a second and apparently it hasn't installed anything. 

I'm using a Nforce 3 based motherboard network chip and have never had problems on any of the releases back to the 5's.

---

### Post by superprash2003 on 2008-11-24
you can configure static ip in ubuntu 8.10 like this [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by AceRimmer on 2008-11-24
I'll give that a try, thanks!

---

### Post by AceRimmer on 2009-02-26
> **superprash2003 said:**
> you can configure static ip in ubuntu 8.10 like this [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

In that the poster says
> 
**Step 1 :** Go to the **Terminal**(Applications->Accessories->Terminal) 
**Step 2 :** Then type **sudo gedit /etc/network/interfaces**
**Step 3 :** Now the interfaces file should open on gedit.
**Step 4 :** Now look for the line 
 **iface eth0 inet dhcp** 

 and replace it with
         
 [B]iface eth0 inet static
 address 192.168.1.10
 netmask 255.255.255.0
 gateway 192.168.1.1[/B]****


But my /etc/network/interfaces reads only this. 
> 
auto lo
iface lo inet loopback

Should I just add the eth0 info under that?

---

