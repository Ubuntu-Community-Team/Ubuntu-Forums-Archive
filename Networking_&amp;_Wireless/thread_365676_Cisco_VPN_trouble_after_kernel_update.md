---
title: "Cisco VPN trouble after kernel update"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by reader4 on 2007-02-19
Running Edgy on a laptop.  I recently updated the kernel to 2.6.17-11 from 2.6.17-10.  When I tried to run the Cisco VPN client that worked perfectly before, I got an error about not being able to find some modules in the kernel directory.  I didn't figure it would work, but I did try copying the old files to the new directory... of course it didn't.  So I reinstalled vpnclient.  Now, when trying to connect, I need to be a superuser (I'm sure I could just change permisisons) and I get the following output:

```

$ sudo vpnclient connect sample_host
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway ...
User Authentication for sample_host...

Enter Username and Password.

Username []: user
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.
Secure VPN Connection terminated locally by the Client
Reason: Failed to enable Virtual Adapter.
There are no new notification messages at this time.

```

All I could find on this problem on the web were issues with XP and Vista.  Anyone have a similar experience, or know what would cause this problem and how to fix it?  Help is appreciated.

---

### Post by arkangel on 2007-02-23
I have the same problem but not after kernel update

I use the same client for connecting my wireless  and i use another profile to connect when i am outside , so far only the wireless works well 

any merciful soul out there ?

---

### Post by JimTDI on 2007-02-23
Are you both stuck having to use the Cisco VPN client?  I've had alot better luck with vpnc, but I'm on Dapper, not Edgy.

---

### Post by arkangel on 2007-02-23
i am using dapper too ,  
with vpnc i got the following error

vpnc-connect: binding to port 500: Permission denied

i will google for that

---

### Post by reader4 on 2007-02-23
I would prefer not to use the Cisco client, but I have only the pcf file with an encoded password for the VPN server, which vpnc cannot use.  I did figure out the superuser thing... you need to:
```
$ sudo chmod 4111 /opt/cisco-vpnclient/bin/cvpnd
```
after installing to give regular users access.  It doesn't help my virtual adapter problem, though.  I can connect just fine using an XP virtual machine, but this is obviously not ideal.  Any thoughts on troubleshooting the virtual adapter?  Could this somehow be related to the virtual machine?  The problem persists after uninstalling vmware server, so I doubt it.

---

### Post by JimTDI on 2007-02-24
> **arkangel said:**
> i am using dapper too ,  
with vpnc i got the following error

vpnc-connect: binding to port 500: Permission denied

i will google for that

make sure you run "sudo vpnc ..."  - also try running FireStarter and stopping the firewall, and see if that helps you out at all...

---

### Post by arkangel on 2007-02-25
> $ sudo vpnclient connect sample_host
...
Authenticating user.
Negotiating security policies.
Securing communication channel.
Secure VPN Connection terminated locally by the Client
Reason: Failed to enable Virtual Adapter.
There are no new notification messages at this time

Hi I solved my problem, well I duno  know  exactly how
first I installed the LZO compression library
# sudo aptitude install  liblzo
(for compiling  another  client)

then I had a hunch  so I opened  the network manager and see that my wireless and my eth0 (net card) were both active  since i am using a dsl  I deactivated the connection i am not using , ie eth0.  Now the cisco vpn client  is working :)  Hope it solves anyone else's  similar problem

---

### Post by reader4 on 2007-03-01
That didn't solve anything for me.  I reinstalled the client yet again, and it worked fine for a couple of days, but now has gone back to the same error.  I am working on wireless, but I don't think that has anything to do with it... it has worked/not worked on both wireless and wired connections.  Any other ideas?

---

### Post by reader4 on 2007-03-01
Problem solved... sort of.

I had to disable my wired LAN connection to use the Cisco VPN client with wireless.  I'm not sure why this is, but I reinstalled the client with both wireless/wired enabled... no luck.  Disabled the wired connection and it worked perfectly.  Not sure why this might happen, though... anyone?

---

### Post by reader4 on 2007-05-05
Not sure why either, but that solved it for me.  Thanks!

---

### Post by sarcangeli on 2007-09-12
> **arkangel said:**
> Hi I solved my problem, well I duno  know  exactly how
first I installed the LZO compression library
# sudo aptitude install  liblzo
(for compiling  another  client)

then I had a hunch  so I opened  the network manager and see that my wireless and my eth0 (net card) were both active  since i am using a dsl  I deactivated the connection i am not using , ie eth0.  Now the cisco vpn client  is working :)  Hope it solves anyone else's  similar problem

This hint helped me to solve the same issue! I actually didn't need to install the library :)
I just disabled the wired ethernet interface and everything went fine (I was connecting through the wireless).

Anyway, for those who are using the cisco client just because they have an encrypted group password that they cannot import in vpnc, there's a much better solution to it:
[http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

(I'm still stuck with the cisco client cause in my case vpnc is still having some troubles to connect).

---

### Post by funkjunkie on 2007-10-18
I am still having some headaches with getting my Cisco vpn client to authenticate properly after upgrading to 7.10

Ive tried everything in this thread, though i got this error when earching for that liblzo package 'Couldn't find package "liblzo".'  


this is my output:
# vpnclient connect <profile>
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at xxx.xxx.xxx.xx
Contacting the gateway at xxx.xxx.xxx.xv (balancing)
User Authentication for <profile>...

Enter Username and Password.

Username [username]: 
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.
Secure VPN Connection terminated locally by the Client
Reason: Failed to enable Virtual Adapter.
There are no new notification messages at this time.


any other suggestions?

---

### Post by funkjunkie on 2007-10-22
went with a clean install of 7.10 rather than wrestling with the upgrade and it solved 99% of my issues. highly recommend clean install over upgrade,

still havnt gotten my dual-head to work, but im going to keep digging. 

thanks,

---

### Post by Donik on 2007-11-04
It seems to me that the cisco vpn client is not able to correctly detect the (really) active interface if there are multiple interfaces up, but not all connected.

I am using network-manager to configure my wireless network, but my wired interface is still configured using ifup and ifdown (i.e. it is listed in /etc/network/interfaces and there it is given a static ip-address, something network-manager can't do yet). Therefore my system (a Debian lenny, not an Ubunut, but I guess this applies to Ubunut too) brought up the wired interface eth1 even when it was not connected, while network-manager brought up the wireless eth0.

Using my cisco vpnclient when I was connected only through the wireless interface eth0  failed with the error message "Reason: Failed to enable Virtual Adapter." in this case. When I then deactivated the wired interface eth1 (using "ifdown eth1"), the vpn client failed with the error message "Reason: Unable to resolve server address." It seems as if the vpnclient needs the interface it's supposed to use to be listed in /etc/network/interfaces, although it still can be configured using network-manager. So listing my wireless interface eth0 as "iface eth0 inet dhcp" without any further parameters (not even an "auto eth0") allowed network-manager to configure it and my vpnclient to connect. 

Hope this helps.

---

### Post by helpdeskdan on 2007-11-07
In regards to : "Reason: Failed to enable Virtual Adapter," this has been my experience.


There are two Problems:

#1.  You get this error sometime before the username prompt.  
Soultion: ifdown all interfaces that you do not need, with the exception of lo.  For instance, I wrote a simple script to start my vpn connection:
sudo ifdown eth0
sudo vpnclient connect my_vpn

#2.  You get this error after the username prompt.  (Probably after Kernal Upgrade)
Solution:  Uninstall the client. (in the vpnclient dir where you installed, there is also a script called vpn_uninstall)  Do a make clean.  Reinstall the client with ./vpn_install.  Reboot.  (I tried restarting the vpnclient_init instead of rebooting - it did not seem to work)

This worked for me - hopefully it will help others.

---

