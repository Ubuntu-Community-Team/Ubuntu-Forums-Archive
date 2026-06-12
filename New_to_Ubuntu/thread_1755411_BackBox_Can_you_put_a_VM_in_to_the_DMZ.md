---
title: "BackBox: Can you put a VM in to the DMZ?"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by -Outlaw- on 2011-05-11
Hello ubuntu pro's.

I am running BackBox linux which i beleive is based on Ubuntu.

I would like to run a VM in BackBox and have it sat at a static IP of 192.168.0.200 in the DMZ to host a small site.

This is what i would like to have

Router 192.168.0.1
Host;BackBox 192.168.0.150
VM;Damn Small linux; running in BackBox 192.168.0.200

on which machine do i configure the static IP's?

Cant the VM request an IP or does the host supply it?

Thanx in advance for answering this :)

---

### Post by taseedorf on 2011-05-12
Yes, the VM can request an IP over the network through DHCP as long as it is configured properly OR it can run using a static IP.  Make sure that you aren't using NAT though on the VM and make sure it has a separate MAC address.

---

