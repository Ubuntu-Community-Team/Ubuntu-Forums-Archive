---
title: "Network not starting"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by ExemplarUbuntu on 2007-01-05
Following a problematic upgrade to Breezy I have a problem with the network eth0 not being enabled once booted. I have to manually enable the eth0 from the network panel.
It used to be enabled automatically.

It may not be related but usb sticks are no longer detected when plugged in.

During boot there are a couple of errors from modprobe but I am not sure if they are significant.

Can anyone help ?

---

### Post by ExemplarUbuntu on 2007-01-09
While trying to get samba working again (partially deleted by the update process for some reason) I found this error in var/log/samba/log.192.168.1.6  from attempts to connect.

smbd/oplock.c;init_oplocks(1357)
open_oplock_ipc: Failed to get local UDP socket for address 100007f. Error was Cannot assign requested address

A search for this error produced this:

Error Message: open_oplock_ipc
An error message is observed in the log files when smbd is started: 
open_oplock_ipc: Failed to get local UDP socket for address 100007f. Error was Cannot assign requested.

Your loopback device isn't working correctly. Make sure it is configured correctly. The loopback device is an internal (virtual) network device with the IP address 127.0.0.1. Read your OS documentation for details on how to configure the loopback on your system. 

===

So I tried to ping localhost and I see 100% packet loss.  Can anyone explain why this is ?

/etc/network/interfaces 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
name Ethernet LAN card
address 192.168.1.16
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.254

----------------------------------------

During the early stages of the boot there was an error about failing to create a folder
/var/run/network

I created this folder and re-booted. There was an error about failing to open ifstate in that folder. However once booted there is an ifstate file in there with just two lines:

lo=lo
eth0=eth0

The eth0 was activated without me having to manually start it and I was able to Samba via a Windows PC.

I'd still like to stop it giving the error at boot. I am using kernel 2.6.10-5 and breezy

---

