---
title: "VPN Through VMWare WinXP using Cisco VPN"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Stelmate on 2008-04-12
I need to connect to my work using VPN and have tried the following:
[LIST]
[*]Using the Cisco VPN client for Linux
[*]Using kVPNC
[*]Using VMWare with a WinXP Image and the Windows Cisco Client
[/LIST]

My work requires use of a user certificate. I had it working fine before on an older windows laptop but that got a bad virus so I need to way to just VPN in from linux.
[B]
Progress from the linux side:[/B]
-The user certificate I was given was base64 which the linux Cisco VPN client didn't like so I converted it over to DER and it imported fine. I stuck a valid connection profile under /etc/opt/cisco-vpnclient/Profiles which is in this form:

[main]
Description=
Host=myworkhost.com
AuthType=3
GroupName=
GroupPwd=
enc_GroupPwd=
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPPhonebook=
ISPCommand=
Username=username
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=1
TcpTunnelingPort=443
CertStore=0
CertName=
CertPath=
CertSubjectName=cn=My  Work
CertSerialHash=<certificate thumb print>
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0

When I try to connect I get this:

Initiating TCP to ***.***.***.***, port 443
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

Any ideas on this?

**From the windows side**

I managed to get everything installed and the certificate imported in my VMWare image  (which is connected through my network using NAT) but when I try to connect I get the following error:
Secure VPN connection terminated locally by the Client.
Reason 412: The remote peer is no longer responding.

It is if the response is getting block when trying to get back through to VMWare?
Any ideas?

---

