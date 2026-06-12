---
title: "How to uninstall VMWare network drivers?"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by e_boulanger on 2008-08-19
I am new to Linux and I have a frustrating problem with VMWare drivers.  When I installed Ubuntu 8.04 in a VMWare 6.0, everything was working perfectly.

Then I decided to install the VMWare tools.  The installation went without problem.  Except now, when Ubuntu is booting, the network is not connected.  I have to start it manually (and then start the firewall).

After searching the internet (and not finding anything useful on this), I decided to uninstall VMWare tools.  The uninstallation went smooth, with the exception of the VMXNET driver that keeps coming up.

I uninstalled it manually (rmmod), but it keeps coming back when Ubuntu is rebooting.

My question is: how can I remove VMXNET for good from Ubuntu and use pcnet32 instead?  I've been working on this for 5 days.  I think I have no other choice but to reinstall Ubuntu.

---

### Post by skidmarks on 2008-09-30
I had this same problem with the network when running under VMware Server. Not sure if it's specific to vmware-tools or not.

Anyways, the fix is easy, once I stumbled across it. Edit the file /etc/network/interfaces. There should be a line that specifies which ones to start automatically. It starts with the word 'auto'. Make sure that it has the interface you have want to bring up, i.e., mine is:

auto lo eth0

hope that helps

---

