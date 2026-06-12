---
title: "vpn setting does not contain valid data"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by lnthai2002 on 2008-08-10
Hi guys,
I'm trying to import vpn setting from a pcf file (i got from the cisco VPN client for windows) to connect to my company network using network manager but I got the following error:
```
the VPN setting file "xxx.pcf" does not contain valid data
```
I dont know what format the vpn should be, here the content of the pcf file that I have:
```

[main]
Description=
Host=#sorry, it's the company secret
AuthType=1
GroupName=#sorry, it's the company secret
GroupPwd=#sorry, it's the company secret
enc_GroupPwd=#sorry, it's the company secret
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPPhonebook=
ISPCommand=
Username=#sorry, it's the company secret
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0

```
Does anyone know what's wrong?

---

