---
title: "No VPN connectivity while using data card"
date: 2014-04-01
forum: Networking &amp; Wireless
---

### Post by gopukrishnan on 2014-04-01
Hi all,

I am facing some issues connectng to vpn (pppt) from my ubuntu home pc. I am using MTS Mblaze (datacard)
for the internet connectivity. I have tried to connect the device via gui network connections but was
not working. So I had to manually configure the mts device using wvdial as below :

Configure MTS Mblaze in ubuntu :

Install the following packages :
usb-modeswitch
usb-modeswitch-data
wvdial

Edit /etc/wvdial.conf

[Dialer mts]
Stupid Mode = 1
Inherits = Modem0
Password = mts
Username = [email]internet@internet.mtsindia.in[/email]
Phone = #777
[Modem0]
Init1 = ATZ
SetVolume = 0
Modem = /dev/ttyUSB0
Baud = 115200
FlowControl = Hardware (CRTSCTS)
Dial Command = ATDT


To connect :

**sudo wvdial mts**

Now device is connecting fine and I am able to connect to the ineternet via browser.


_***Now the real issue :***_

*I want to connect to my office vpn from my machine.* Since I have configured the mts device via backend,
vpn from the gui doesnot detect the connection. So again I have configured vpn via backend as below :

edit /etc/ppp/peers/myvpn:

remotename myvpn
linkname myvpn
ipparam myvpn
pty "pptp <My_host_IP> --nolaunchpppd "
name <my_username>
usepeerdns
require-mppe
refuse-eap
noauth

# adopt defaults from the pptp-linux package
file /etc/ppp/options.pptp


and added my credentials as a next line in /etc/ppp/chap-secrets:

<my_username> myvpn <my_password> *

I have connected to vpn using the below command and I can see vpn is showing as connected but still I am not able to ping to the local network IPs:

**pon myvpn nodetach**

Using interface ppp1
Connect: ppp1 <--> /dev/pts/7
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
local  IP address 10.254.254.55
remote IP address 10.254.254.54
primary   DNS address 10.254.254.24


Still I am able to browse all other sites and issue is only with vpn. Kindly let me know how can I connect to the VPN or suggest any other alternate method for my scenario.

Thanks,
Gopu

---

