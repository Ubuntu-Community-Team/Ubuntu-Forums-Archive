---
title: "Cannot connect to VPN"
date: 2016-05-19
forum: Networking &amp; Wireless
---

### Post by vincenzo10 on 2016-05-19
Hello ubuntu users,
it's like a week that I've been trying to connect with Ivacy VPN but I always face some errors that I don't know how I could I fix them. I know that there are a lot of thread like this but I didn't find the answer in none of them. I want also to tell you that with an applet of the free service called VPN Unlimited I can connect but when I try to use OpenVPN or PPTP with Ivacy, it's impossible. This is the log when I try to connect with Ivacy VPN.
Thanks a lot to everyone is going to answer.
[PHP]May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.0038] audit: op="connection-activate" uuid="144f6fda-02bc-47b3-8c25-b892d8ec60e6" name="Ivacy PPTP" pid=2342 uid=1000 result="success"
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.0077] vpn-connection[0x1dae7b0,144f6fda-02bc-47b3-8c25-b892d8ec60e6,"Ivacy PPTP",0]: Started the VPN service, PID 5981
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.0152] vpn-connection[0x1dae7b0,144f6fda-02bc-47b3-8c25-b892d8ec60e6,"Ivacy PPTP",0]: Saw the service appear; activating connection
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.0192] vpn-connection[0x1dae7b0,144f6fda-02bc-47b3-8c25-b892d8ec60e6,"Ivacy PPTP",0]: VPN plugin: state changed: init (1)
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.0219] vpn-connection[0x1dae7b0,144f6fda-02bc-47b3-8c25-b892d8ec60e6,"Ivacy PPTP",0]: VPN connection: (ConnectInteractive) reply received
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: ** Message: pppd started with pid 5986
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.0873] vpn-connection[0x1dae7b0,144f6fda-02bc-47b3-8c25-b892d8ec60e6,"Ivacy PPTP",0]: VPN plugin: state changed: starting (3)
May 19 19:08:47 vincenzo-K53SJ pppd[5986]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
May 19 19:08:47 vincenzo-K53SJ pppd[5986]: pppd 2.4.7 started by root, uid 0
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.1277] manager: (ppp0): new Generic device (/org/freedesktop/NetworkManager/Devices/6)
May 19 19:08:47 vincenzo-K53SJ pptp[5991]: nm-pptp-service-5981 log[main:pptp.c:350]: The synchronous pptp option is NOT activated
May 19 19:08:47 vincenzo-K53SJ pppd[5986]: Using interface ppp0
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: Using interface ppp0
May 19 19:08:47 vincenzo-K53SJ pppd[5986]: Connect: ppp0 <--> /dev/pts/19
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: Connect: ppp0 <--> /dev/pts/19
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.1345] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 19 19:08:47 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677727.1350] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 19 19:08:47 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
May 19 19:08:47 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
May 19 19:08:47 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
May 19 19:08:48 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
May 19 19:08:48 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
May 19 19:08:48 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 21939, peer's call ID 8046).
May 19 19:09:18 vincenzo-K53SJ pppd[5986]: LCP: timeout sending Config-Requests
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: LCP: timeout sending Config-Requests
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: Connection terminated.
May 19 19:09:18 vincenzo-K53SJ pppd[5986]: Connection terminated.
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: ** Message: Terminated ppp daemon with PID 5986.
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: <error> [1463677758.1621] platform-linux: do-change-link[7]: failure changing link: failure 19 (No such device)
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: <warn>  [1463677758.1621] device (ppp0): failed to disable userspace IPv6LL address handling
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677758.1640] vpn-connection[0x1dae7b0,144f6fda-02bc-47b3-8c25-b892d8ec60e6,"Ivacy PPTP",0]: VPN service disappeared
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: <info>  [1463677758.1650] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: Terminating on signal 15
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: Modem hangup
May 19 19:09:18 vincenzo-K53SJ pppd[5986]: Terminating on signal 15
May 19 19:09:18 vincenzo-K53SJ pppd[5986]: Modem hangup
May 19 19:09:18 vincenzo-K53SJ pppd[5986]: Child process /usr/sbin/pptp 172.111.136.4 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-5981 (pid 5989) terminated with signal 15
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: Child process /usr/sbin/pptp 172.111.136.4 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-5981 (pid 5989) terminated with signal 15
May 19 19:09:18 vincenzo-K53SJ NetworkManager[1024]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
May 19 19:09:18 vincenzo-K53SJ pppd[5986]: Exit.
May 19 19:09:18 vincenzo-K53SJ pptp[5991]: nm-pptp-service-5981 warn[decaps_hdlc:pptp_gre.c:220]: short read (-1): Input/output error
May 19 19:09:18 vincenzo-K53SJ pptp[5991]: nm-pptp-service-5981 warn[decaps_hdlc:pptp_gre.c:232]: pppd may have shutdown, see pppd log
May 19 19:09:18 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)
May 19 19:09:18 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Request'
May 19 19:09:18 vincenzo-K53SJ pptp[6004]: nm-pptp-service-5981 log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)

[/PHP]

---

### Post by QDR06VV9 on 2016-05-19
Not sure if you have looked at this yet or not but worth a look: [https://support.ivacy.com/kb/how-to-setup-ivacy-pptp-protocol-manually-on-ubuntu/](https://support.ivacy.com/kb/how-to-setup-ivacy-pptp-protocol-manually-on-ubuntu/)
Looks to be straight forward and understandable.
Kind regards

---

### Post by vincenzo10 on 2016-05-19
> **runrickus said:**
> Not sure if you have looked at this yet or not but worth a look: [https://support.ivacy.com/kb/how-to-setup-ivacy-pptp-protocol-manually-on-ubuntu/](https://support.ivacy.com/kb/how-to-setup-ivacy-pptp-protocol-manually-on-ubuntu/)
Looks to be straight forward and understandable.
Kind regards

Thanks for your answer. I' trying to use Ivacy VPN with that setting but the error that I face is after setting a VPN like that.

---

### Post by QDR06VV9 on 2016-05-19
Not sure I can help here but post back the output of this in the terminal
```
gedit /etc/modules-load.d/netfilter.conf
```
Sorry please reread this as i have just added a correction to my code

---

### Post by vincenzo10 on 2016-05-19
> **runrickus said:**
> Not sure I can help here but post back the output of this in the terminal
```
gedit /etc/modules-load.d/netfilter.conf
```
Sorry please reread this as i have just added a correction to my code

Thanks, I appreciate your help!

I opened that file but is empty :???:

---

### Post by QDR06VV9 on 2016-05-19
Ah ha! I have seen a few posts from others having the same problems as you have reported.
They have created a "New text file" and added the below text to it in the same directory "/etc/modules-load.d ".
Name the file or save the file as "netfilter.conf"
```
nf_nat_pptp
nf_conntrack_pptp
nf_conntrack_proto_gre
```
And after a restart should be good to go.
Fingers Crossed..

---

### Post by vincenzo10 on 2016-05-19
> **runrickus said:**
> Ah ha! I have seen a few posts from others having the same problems as you have reported.
They have created a "New text file" and added the below text to it in the same directory "/etc/modules-load.d ".
Name the file or save the file as "netfilter.conf"
```
nf_nat_pptp
nf_conntrack_pptp
nf_conntrack_proto_gre
```
And after a restart should be good to go.
Fingers Crossed..

Thank you! Last question: should I modify the file that I noticed that was empty or should I just create a new one?
I'll give it a try right now!

---

### Post by QDR06VV9 on 2016-05-19
Ether way is ok but to save the text file you will have to have elevated rights.
So Use
```
gksudo gedit /etc/modules-load.d/netfilter.conf
```
Add the above text to it and save and reboot

---

### Post by Gian_Franco on 2016-05-24
Hey there! 
I'm having the same problem that you and follow the instructions to create the netfilter.conf file but does not worck for me :(

Here is the output of  cat [COLOR=#000000][FONT=Ubuntu Mono]/etc/modules-load.d/netfilter.conf

[/FONT][/COLOR]nf_nat_pptp
nf_conntrack_pptp
nf_conntrack_proto_gre
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
Here is my log:

NetworkManager[715]: <info>  [1464104435.0577] audit: op="connection-activate" uuid="a6b70a9c-b196-45d6-a9d6-14e9bb736bd4" name="keepcon" pid=1943 uid=1000 result="success"
NetworkManager[715]: <info>  [1464104435.0602] vpn-connection[0x15615c0,a6b70a9c-b196-45d6-a9d6-14e9bb736bd4,"keepcon",0]: Started the VPN service, PID 2680
NetworkManager[715]: <info>  [1464104435.0652] vpn-connection[0x15615c0,a6b70a9c-b196-45d6-a9d6-14e9bb736bd4,"keepcon",0]: Saw the service appear; activating connection
NetworkManager[715]: <info>  [1464104435.0671] vpn-connection[0x15615c0,a6b70a9c-b196-45d6-a9d6-14e9bb736bd4,"keepcon",0]: VPN plugin: state changed: init (1)
NetworkManager[715]: <info>  [1464104435.0689] vpn-connection[0x15615c0,a6b70a9c-b196-45d6-a9d6-14e9bb736bd4,"keepcon",0]: VPN connection: (ConnectInteractive) reply received
NetworkManager[715]: ** Message: pppd started with pid 2685
NetworkManager[715]: <info>  [1464104435.0728] vpn-connection[0x15615c0,a6b70a9c-b196-45d6-a9d6-14e9bb736bd4,"keepcon",0]: VPN plugin: state changed: starting (3)
pppd[2685]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
NetworkManager[715]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
NetworkManager[715]: ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
pppd[2685]: pppd 2.4.7 started by root, uid 0
NetworkManager[715]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
NetworkManager[715]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
pptp[2690]: nm-pptp-service-2680 log[main: pptp.c:350]: The synchronous pptp option is NOT activated
NetworkManager[715]: <info>  [1464104435.0908] manager: (ppp0): new Generic device (/org/freedesktop/NetworkManager/Devices/5)
pppd[2685]: Using interface ppp0
NetworkManager[715]: Using interface ppp0
NetworkManager[715]: Connect: ppp0 <--> /dev/pts/11
NetworkManager[715]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
pppd[2685]: Connect: ppp0 <--> /dev/pts/11
NetworkManager[715]: <info>  [1464104435.0980] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager[715]: <info>  [1464104435.0980] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
pptp[2702]: nm-pptp-service-2680 log[ctrlp_rep: pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
pptp[2702]: nm-pptp-service-2680 log[ctrlp_disp: pptp_ctrl.c:781]: Received Start Control Connection Reply
pptp[2702]: nm-pptp-service-2680 log[ctrlp_disp: pptp_ctrl.c:815]: Client connection established.
pptp[2702]: nm-pptp-service-2680 log[ctrlp_rep: pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
pptp[2702]: nm-pptp-service-2680 log[ctrlp_disp: pptp_ctrl.c:900]: Received Outgoing Call Reply.
pptp[2702]: nm-pptp-service-2680 log[ctrlp_disp: pptp_ctrl.c:939]: Outgoing call established (call ID 56998, peer's call ID 15685).
pppd[2685]: LCP: timeout sending Config-Requests
pppd[2685]: Connection terminated.
NetworkManager[715]: LCP: timeout sending Config-Requests
NetworkManager[715]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
NetworkManager[715]: Connection terminated.
NetworkManager[715]: ** Message: Terminated ppp daemon with PID 2685.
NetworkManager[715]: <error> [1464104466.1249] platform-linux: do-change-link[6]: failure changing link: failure 19 (No such device)
NetworkManager[715]: <warn>  [1464104466.1250] device (ppp0): failed to disable userspace IPv6LL address handling
NetworkManager[715]: <info>  [1464104466.1251] vpn-connection[0x15615c0,a6b70a9c-b196-45d6-a9d6-14e9bb736bd4,"keepcon",0]: VPN service disappeared
NetworkManager[715]: <info>  [1464104466.1296] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager[715]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
NetworkManager[715]: Terminating on signal 15
NetworkManager[715]: Child process /usr/sbin/pptp 190.221.176.82 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-2680 (pid 2688) terminated with signal 15
NetworkManager[715]: Modem hangup
NetworkManager[715]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
pptp[2690]: nm-pptp-service-2680 warn[decaps_hdlc: pptp_gre.c:220]: short read (-1): Input/output error
pptp[2690]: nm-pptp-service-2680 warn[decaps_hdlc: pptp_gre.c:232]: pppd may have shutdown, see pppd log
pppd[2685]: Terminating on signal 15
pppd[2685]: Child process /usr/sbin/pptp 190.221.176.82 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-2680 (pid 2688) terminated with signal 15
pppd[2685]: Modem hangup
pppd[2685]: Exit.

---

