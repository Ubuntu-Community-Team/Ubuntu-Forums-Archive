---
title: "Desktop Optiplex 7050 lost internet though ethernet &amp; wifi both connect fine"
date: 2023-10-16
forum: Networking &amp; Wireless
---

### Post by jeff982 on 2023-10-16
Desktop Optiplex 7050 Intel Core Processor, Ubuntu 22.04.3 LTS

When this occurred Proton VPN was just starting up, trying to connect with a remote server. Proton never connected, and after that Firefox, Thunderbird and Software Updater could no longer get to the network even though the connection from the computer to the router is fine. The usual ethernet connection checks out, and so does a wifi connection I just tried, recognized on both ends. 
I'm a novice.
Running "Wireless network troubleshooter" showed a "dummy" device just below the real Wifi connection. 
From left to right the 2 lines in green read, under these headings:
    
DEVICE                                   TYPE                     STATE                    CONNECTION
wlx8c883bc144a3        wifi                      connected              ScullyMusic
lpv6leakintrfo                 dummy              connected            pvpn  lpv6leak  protection

Is there a chance that this "dummy" connection is interfering with my software's access? I already uninstalled Proton VPN yesterday, so this "DEVICE" is a leftover.
 In case this is my problem, could you provide me with the commands I could copy and paste into terminal that would disable or eliminate this connection?
Thank you very much, I appreciate your help and expertise!

---

### Post by chili555 on 2023-10-17
Please see: [https://askubuntu.com/questions/1372873/connected-on-wireless-but-no-internet-access-in-ubuntu-20-04](https://askubuntu.com/questions/1372873/connected-on-wireless-but-no-internet-access-in-ubuntu-20-04)

> ipv6leakintrf0(Type-dummy). This issue is caused by Proton VPN to prevent IP leak when you accidentally turn off your system or disconnect from your network without disconnecting the VPN. As long as that connection remains, it will block access to internet on your device.

---

### Post by jeff982 on 2023-10-17
[SOLVED]  Many thanks for that link! 
I simply pasted   nmcli connection delete pvpn-ipv6leak-protection    into terminal, hit enter, and the problem disappeared! You're the greatest!

---

