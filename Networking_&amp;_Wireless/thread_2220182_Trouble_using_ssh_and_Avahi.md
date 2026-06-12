---
title: "Trouble using ssh and Avahi"
date: 2014-04-27
forum: Networking &amp; Wireless
---

### Post by thatSeniorGuy on 2014-04-27
Greetings all, I'm having trouble using SSH'ing from my netbook to my desktop using a .local hostname. Every so often, I have to reset the router I use, which resets the addresses it give out to my devices, so a while ago I set up Avahi to get around this*. The /etc/avahi/services/ssh.service file is the standard one copied from the documentation:

```

<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">


<!-- See avahi.service(5) for more information about this configuration file -->


<service-group>


  <name replace-wildcards="yes">%h</name>


  <service>
    <type>_ssh._tcp</type>
    <port>22</port>
  </service>


</service-group>

```

This used to work fine, but now for some reason when I try to ssh from my netbook to my desktop, I get the following error message (note I changed my pc's hostname in this output):
```

>> ssh pc.local -vvv
OpenSSH_6.2p2 Ubuntu-6ubuntu0.3, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /home/username/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: Could not resolve hostname pc.local: Name or service not known

```

I *can* ssh from my netbook to my PC when I put in the IP address manually, and when I've set up /etc/hosts correctly (so the daemon on my PC is working fine), it only stops working when I try to use the .local address. SSH'ing in the other direction (PC->netbook) works fine, even when using a .local hostname. Avahi also appears to be working fine:
```

>> avahi-browse -a -t+  
+  wlan0 IPv6 netbook                                  SSH Remote Terminal       local
+  wlan0 IPv6 netbook [<MAC address>]       Workstation                       local
+  wlan0 IPv6 netbook                                  Remote Disk Management local
+  wlan0 IPv4 netbook                                  SSH Remote Terminal       local
+  wlan0 IPv4 netbook [<MAC address>]       Workstation                       local
+  wlan0 IPv4 netbook                                  Remote Disk Management local
+  wlan0 IPv4 pc                                          SSH Remote Terminal       local
+  wlan0 IPv4 pc [<MAC address>]               Workstation                       local
+  wlan0 IPv4 pc                                          Remote Disk Management local
+  wlan0 IPv6 pc                                          SSH Remote Terminal       local
+  wlan0 IPv6 pc [<MAC address>]               Workstation                      local
+  wlan0 IPv6 pc                                          Remote Disk Management local

```

The netbook is running Lubuntu 13.10; note that I did change to Lubuntu recently, and I only recall seeing this error with Lubuntu and not with plain Ubuntu. My desktop is running Ubuntu 13.10.

Any help would be appreciated!

* I am aware that can set up my router to permanently give set addresses to both devices, and I will do that if I can't resolve this issue, but I'd prefer to try and fix this rather than work around it.

---

### Post by thatSeniorGuy on 2014-05-03
Bump. Anyone willing to lend a hand?

---

