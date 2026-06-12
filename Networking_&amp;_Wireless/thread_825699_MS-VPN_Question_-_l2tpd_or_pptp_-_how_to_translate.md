---
title: "MS-VPN Question - l2tpd or pptp - how to translate..."
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by freecode99 on 2008-06-11
Hi all,

VPN question here. I am trying to connect to an MS VPN @ work (previously was conencting to a Cisco VPN w/out issue @ old job) and running afoul of the new environment settings.

I found the MS VPN connection settings, and was wondering how this could be setup using either network manager-vpnc or just vpnc or xl2tpd. IT says it's a pptp VPN, but the settings below indicate otherwise.

I would like to know how to make this work so that I can connect from home - using Hardy Heron 8.04 32-bit (64 bit vpn connection to a 32-bit not so likely).

Settings from Windows:

[VPN Connection]

Encoding=1

Type=2

AutoLogon=0

UseRasCredentials=1

LowDateTime=-220729216

HighDateTime=29936020

DialParamsUID=429470

Guid=$some_var

BaseProtocol=1

VpnStrategy=2

ExcludedProtocols=2

LcpExtensions=1

DataEncryption=256

SwCompression=0

NegotiateMultilinkAlways=0

SkipNwcWarning=0

SkipDownLevelDialog=0

SkipDoubleDialDialog=0

DialMode=0

OverridePref=15

RedialAttempts=3

RedialSeconds=60

IdleDisconnectSeconds=0

RedialOnLinkFailure=1

CallbackMode=0

CustomDialDll=

CustomDialFunc=

CustomRasDialDll=

ForceSecureCompartment=0

DisableIKENameEkuCheck=0

AuthenticateServer=0

ShareMsFilePrint=1

BindMsNetClient=1

SharedPhoneNumbers=0

GlobalDeviceSettings=0

PrerequisiteEntry=

PrerequisitePbk=

PreferredPort=VPN0-0

PreferredDevice=WAN Miniport (L2TP)

PreferredBps=0

PreferredHwFlow=1

PreferredProtocol=1

PreferredCompression=1

PreferredSpeaker=1

PreferredMdmProtocol=0

PreviewUserPw=1

PreviewDomain=1

PreviewPhoneNumber=0

ShowDialingProgress=1

ShowMonitorIconInTaskBar=1

CustomAuthKey=-1

AuthRestrictions=512

TypicalAuth=2

IpPrioritizeRemote=1

IpInterfaceMetric=0

fCachedDnsSuffix=0

IpHeaderCompression=0

IpAddress=0.0.0.0

IpDnsAddress=0.0.0.0

IpDns2Address=0.0.0.0

IpWinsAddress=0.0.0.0

IpWins2Address=0.0.0.0

IpAssign=1

IpNameAssign=1

IpDnsFlags=0

IpNBTFlags=1

TcpWindowSize=0

UseFlags=0

IpSecFlags=0

IpDnsSuffix=

IpCachedDnsSuffix=

Ipv6PrioritizeRemote=1

Ipv6InterfaceMetric=0

Ipv6NameAssign=1

Ipv6DnsAddress=::

Ipv6Dns2Address=::

Ipv6InterfaceId=0000000000000000



NETCOMPONENTS=

ms_msclient=1

ms_server=1

ms_pacer=1

dni_dne=1

eset_epfwndis=1



MEDIA=rastapi

Port=VPN0-0

Device=WAN Miniport (L2TP)



DEVICE=vpn

PhoneNumber=vpn.xxxxx.com

AreaCode=

CountryCode=1

CountryID=1

UseDialingRules=0

Comment=

LastSelectedPhone=0

PromoteAlternates=0

TryNextAlternateOnFail=1

Any ideas on translating that into vpnc or other connections so that I can connect remotely without running Windows in a virtual machine?

AdvTHANKSance.

freecode](*,)

---

### Post by freecode99 on 2008-08-03
Fixed it myself. Seems that the VPN client just works when I removd an old Cisco VPN client install. Oh well - not so much of a problem after all.

freecode

---

### Post by arsham on 2008-11-05
Hi,
Do you have the file format for these information?
I need to know what are these options are and the format and so on.
I mean, I need a documentation.
Do you have any links or documents?

Thank you in advance,
Arsham

---

