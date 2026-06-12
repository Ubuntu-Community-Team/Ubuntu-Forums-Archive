---
title: "Samba PDC problem with client upgrade"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by gacain on 2008-04-28
Hello,

New_server - Ubuntu 6.06.2 LTS (recently updated from Breezy) w/Samba 3.0.22-lubuntu3.6

Old_server - RedHat 8 w/Samba 2.2.5-10 - yes, I know this is old - usually when something works I try not to mess with it.

The RedHat server is functioning as the PDC for this network.  Prior to upgrading the New_server everything was working fine - shares on New_server were accessible just as they should be.  

After upgrading New_server, there now there appears to be a problem with domain validation of users/passwords on this computer.  When trying to connect to a share on New_server from a Windows box, I get the following error:

> C:\Documents and Settings\user\Desktop>net use n: \\New_server\share
System error 58 has occurred.

The specified server cannot perform the requested operation.

I erased the machine account from Old_server and re-added it, then tried net join:

> root@New_server:/scripts# net join
root's password:
[2008/04/28 08:31:12, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: Transport endpoint is not connected
Joined domain LAN.
root@tamago:/scripts#

It appears the network has been joined but I'm still not able to validate users/passwords via the PDC, and I don't understand the apparent error that has been generated here.

Also when running testparm on New_server I get the following message:

> Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_DOMAIN_MEMBER

but I do not have the parameter  "passdb expand explicit" defined in smb.conf.  Here is the [global] section:

> [global]
netbios name=New_server
server string=Backup Server
workgroup = LAN
encrypt passwords = true
security=domain
password server=*
passdb backend=tdbsam
hosts allow=192.168.254.
guest account=guest
map to guest = Bad Password

And here is the [global] section on Old_server:

> [global]
netbios name=Old_server
server string=PDC File Server
workgroup=dandb
encrypt passwords=yes

## SUPPORT FOR WINS & DOMAIN LOGONS
##
wins support=yes
domain master=yes
local master=yes
preferred master=yes
os level=255
security=user
domain logons=yes
logon script=%U.bat
domain admin group=root user administrator
##
## END WINS/DOMAIN SECTION

Any assistance would be greatly appreciated.

---

