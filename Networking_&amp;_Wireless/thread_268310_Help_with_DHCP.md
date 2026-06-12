---
title: "Help with DHCP"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by jjakspaw6 on 2006-09-29
Hi all! 

I am having a bit of a problem with ubuntu. Every time I have to restart my PC i have to go into terminal and run dhclient to reaquire an Ip address from my ISP. This has been going on for about a week now and its starting to bother me. can some one please give me an Idea as how to fix this.  I've only just started using linux (full time) recently and don't know a whole lot about the system yet..... 


Thanks in advance


Jason

---

### Post by BoneKracker on 2006-09-30
I don't have a clean answer, but here's what comes to mind:

In the terminal, type
```
ls /var/run
```
If dhclient is running you should see "dhclient.blahblah.pid".
If you don't see that, it's not running.
If you see that, but don't see one like "dhclient.eth0.pid", then your network settings are probably wrong (in menu system > admin).

If it's not running, then you either hosed a rc-type configuration file that governs dhcp, or you b0rked the init system.  If this is the case, and you're pretty much new to unix, you might just want to back up your personal files and reinstall.  Alternatively:

a) Enable the Universe repository in synaptic and install the package named "BUM".  Use it to check if the dhcp service is configured to start automatically.  Be careful with this package or you'll screw up your system even worse.
b) Revisit any network-related configuration files you have edited in the /etc directory.
c) Uninstalling dhclient (using the option to "completely" uninstall it) and reinstalling it, might reset any screwed-up config files to their defaults.

---

### Post by JGuru on 2006-09-30
You don't have to run 'dhclient' every time. Do the following procedure,
 your problem will be solved!!
 
 Open the Terminal Window & type:

 $ **gksu network-admin**

  This will open the **Network Settings** dialog.Now select **Ethernet Connection**,
 Click on the 'Properties' button (top-right).Now under 'Connection Settings'
 'Configuration' Change it from 'DHCP' to 'Static IP address'.
 Now fill in your ISP's IP address, subnet mask(255.255.255.0), & Gateway address.
 Now click on 'OK' & again click on 'OK' button. That's it. Your problem
 should be solved!!

---

### Post by BoneKracker on 2006-10-01
That will work for a while, but it doesn't fix the system.

---

### Post by Iowan on 2006-10-01
From a terminal, you could also```
ps ax |grep "dhcp"

```
Another thing would be to verify that (as mentioned) System>Administration>Networking>Connection properties is set for DHCP.

---

