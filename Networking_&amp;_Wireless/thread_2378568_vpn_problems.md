---
title: "vpn problems"
date: 2017-11-24
forum: Networking &amp; Wireless
---

### Post by iebo on 2017-11-24
[COLOR=#000000][FONT=Verdana]hi[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]i can't connect to vpn over pptp and openvpn i use ubuntu 12.04 and other linux distro  , i feel that issue beyond beyond my control and in country isp's because [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]as i have read [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]recently [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]they blocked some vpns [/FONT][/COLOR][COLOR=#000000][FONT=Verdana].

[/FONT][/COLOR]but on another forums some person pointed out that isp can't block all vpn connection but they can block some providers by ip/ports

[COLOR=#000000][FONT=Verdana]how i can know which providers are effected before trying ? [/FONT][/COLOR]i used other port than 1194


[COLOR=#000000][FONT=Verdana]also  i ran some updates for my ubuntu os that may changed something in the settings..i don't know where the problem is and how to diagnosis it .[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]most errors are common nothing were unique to me to find quicker solution on google  ... "vpn connection failed etc"[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]furthermore i have a vps with openvpn setup and it can establish connection sometimes and bind the server but i'm not able to browse internet .[/FONT][/COLOR]

[FONT=Verdana][COLOR=#000000]the other night i tested vpn service via other line/router/isp/linux distro to make sure it's not main os, still i have troubles .[/COLOR][/FONT]

[FONT=Verdana][COLOR=#000000]my openvpn connection with vps don't progress after this lines
[/COLOR][/FONT]```
[FONT=Verdana][COLOR=#000000]
"[/COLOR][/FONT][COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 OpenVPN 2.2.1 i686-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Dec 1 2014[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 Control Channel Authentication: tls-auth using INLINE static key file[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 Outgoing Control Channel Authentication: Using 512 bit message hash 'SHA512' for HMAC authentication[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 Incoming Control Channel Authentication: Using 512 bit message hash 'SHA512' for HMAC authentication[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 LZO compression initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 Control Channel MTU parms [ L:1000 D:010 EF:000 EB:0 ET:0 EL:0 ][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 Socket Buffers: R=[163840->163840] S=[163840->163840][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 Data Channel MTU parms [ L:1000 D:010 EF:000 EB:00 ET:0 EL:0 AF:3/1 ][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 Local Options hash (VER=V4): 'a5xxxxx'[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 Expected Remote Options hash (VER=V4): '14xxxxx'[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 UDPv4 link local: [undef][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:34 2017 UDPv4 link remote: [AF_INET]4x.xx.xx.xx:1195[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thu Nov 23 00:58:35 2017 TLS: Initial packet from [AF_INET]4x.xx.xx.xx:1195, sid=9d00000 410000[/FONT][/COLOR]

```


how i can diagnose this problem?  it's possible that i have openvpn issue but all commercial pptp providers are not working aswell .

i need vpn to work again  because it start to ruin my privacy  .

---

### Post by iebo on 2017-11-26
no vpn expert here to help me ?

---

