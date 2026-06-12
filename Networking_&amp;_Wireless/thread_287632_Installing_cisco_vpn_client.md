---
title: "Installing cisco vpn client"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Laalitha on 2006-10-29
I am new to linux and I tried to install cisco vpn client. But I get the following error

```


root@LSIL-PrecisionM60:/home/laalitha/Desktop/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 3.6.2 (A) Linux Installer
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserved.

Please review the license agreement found in license.txt


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes] yes

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by de fault

Directory containing linux kernel source code [/lib/modules/2.6.15-27-386/build]  /usr/src/linux-headers-2.6.15-27-386

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-27-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.15-27-386" will be used to buil d the module.

Is the above correct [y] y

Making module
linuxcniapi.c:19:31: error: linux/modversions.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:2 2,
                 from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from linuxcniapi.c:22:
/usr/src/linux-headers-2.6.15-27-386/include/asm/irq.h:16:25: error: irq_vectors .h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from linuxcniapi.c:22:
/usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:85: error: ‘NR_IRQS’ un declared here (not in a function)
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:9 4,
                 from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from linuxcniapi.c:22:
/usr/src/linux-headers-2.6.15-27-386/include/asm/hw_irq.h:30: error: ‘NR_IRQ_VEC TORS’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from linuxcniapi.c:22:
/usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff.h: In function ‘skb_ad d_data’:
/usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff.h:1128: warning: point er targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedne ss
In file included from /usr/src/linux-headers-2.6.15-27-386/include/net/request_s ock.h:22,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/ip.h:84 ,
                 from linuxcniapi.c:27:
/usr/src/linux-headers-2.6.15-27-386/include/net/sock.h: In function ‘skb_copy_t o_page’:
/usr/src/linux-headers-2.6.15-27-386/include/net/sock.h:1064: warning: pointer t argets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
linuxcniapi.c: In function ‘CNI_LINUXMemAlloc’:
linuxcniapi.c:202: error: invalid lvalue in assignment
linuxcniapi.c: In function ‘CNI_LINUXGetPacketData’:
linuxcniapi.c:518: warning: pointer targets in assignment differ in signedness
linuxcniapi.c: In function ‘CNI_LINUXSetPacketData’:
linuxcniapi.c:621: warning: pointer targets in assignment differ in signedness
linuxcniapi.c: In function ‘CNI_LINUXGetMacAddress’:
linuxcniapi.c:1118: warning: pointer targets in assignment differ in signedness
linuxcniapi.c: In function ‘CNI_LINUXInjectReceive’:
linuxcniapi.c:1275: error: redeclaration of ‘timecount’ with no linkage
linuxcniapi.c:1273: error: previous declaration of ‘timecount’ was here
linuxcniapi.c:1289: error: ‘struct sk_buff’ has no member named ‘stamp’
linuxcniapi.c:1293: warning: pointer targets in passing argument 4 of ‘CniGetPac ketData’ differ in signedness
linuxcniapi.c: In function ‘CNI_LINUXInjectSend’:
linuxcniapi.c:1396: warning: pointer targets in passing argument 4 of ‘CniGetPac ketData’ differ in signedness
linuxcniapi.c:1407: error: ‘struct sk_buff’ has no member named ‘stamp’
interceptor.c:19:31: error: linux/modversions.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:2 2,
                 from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from interceptor.c:24:
/usr/src/linux-headers-2.6.15-27-386/include/asm/irq.h:16:25: error: irq_vectors .h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from interceptor.c:24:
/usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:85: error: ‘NR_IRQS’ un declared here (not in a function)
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:9 4,
                 from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from interceptor.c:24:
/usr/src/linux-headers-2.6.15-27-386/include/asm/hw_irq.h:30: error: ‘NR_IRQ_VEC TORS’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from interceptor.c:24:
/usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff.h: In function ‘skb_ad d_data’:
/usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff.h:1128: warning: point er targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedne ss
In file included from /usr/src/linux-headers-2.6.15-27-386/include/net/request_s ock.h:22,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/ip.h:84 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/net/ip.h:28,
                 from interceptor.c:30:
/usr/src/linux-headers-2.6.15-27-386/include/net/sock.h: In function ‘skb_copy_t o_page’:
/usr/src/linux-headers-2.6.15-27-386/include/net/sock.h:1064: warning: pointer t argets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
interceptor.c: In function ‘handle_vpnup’:
interceptor.c:267: error: ‘MOD_IN_USE’ undeclared (first use in this function)
interceptor.c:267: error: (Each undeclared identifier is reported only once
interceptor.c:267: error: for each function it appears in.)
interceptor.c:278: warning: assignment from incompatible pointer type
interceptor.c:282: error: ‘struct packet_type’ has no member named ‘next’
interceptor.c:287: error: ‘struct packet_type’ has no member named ‘next’
interceptor.c:303: warning: assignment from incompatible pointer type
interceptor.c:304: warning: assignment from incompatible pointer type
interceptor.c:360: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this func tion)
interceptor.c: In function ‘handle_vpndown’:
interceptor.c:369: error: ‘MOD_IN_USE’ undeclared (first use in this function)
interceptor.c:381: warning: assignment from incompatible pointer type
interceptor.c:402: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this func tion)
interceptor.c: In function ‘recv_ip_packet_handler’:
interceptor.c:488: warning: pointer targets in passing argument 2 of ‘CniNewFrag ment’ differ in signedness
interceptor.c:500: warning: pointer targets in passing argument 2 of ‘CniNewFrag ment’ differ in signedness
interceptor.c: In function ‘do_cni_send’:
interceptor.c:573: warning: pointer targets in passing argument 2 of ‘CniNewFrag ment’ differ in signedness
interceptor.c:595: warning: pointer targets in passing argument 2 of ‘CniNewFrag ment’ differ in signedness
IPSecDrvOS_linux.c:20:31: error: linux/modversions.h: No such file or directory
IPSecDrvOS_linux.c: In function ‘GetCurrentTime’:
IPSecDrvOS_linux.c:137: error: incompatible types in assignment
frag.c:9:31: error: linux/modversions.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:2 2,
                 from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from frag.c:11:
/usr/src/linux-headers-2.6.15-27-386/include/asm/irq.h:16:25: error: irq_vectors .h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from frag.c:11:
/usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:85: error: ‘NR_IRQS’ un declared here (not in a function)
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/irq.h:9 4,
                 from /usr/src/linux-headers-2.6.15-27-386/include/asm/hardirq.h :6,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/hardirq .h:7,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/interru pt.h:11,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/rcuref. h:36,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/fs.h:12 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/mm.h:15 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff. h:26,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from frag.c:11:
/usr/src/linux-headers-2.6.15-27-386/include/asm/hw_irq.h:30: error: ‘NR_IRQ_VEC TORS’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.15-27-386/include/linux/if_ethe r.h:109,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/netdevi ce.h:29,
                 from frag.c:11:
/usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff.h: In function ‘skb_ad d_data’:
/usr/src/linux-headers-2.6.15-27-386/include/linux/skbuff.h:1128: warning: point er targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedne ss
In file included from /usr/src/linux-headers-2.6.15-27-386/include/net/request_s ock.h:22,
                 from /usr/src/linux-headers-2.6.15-27-386/include/linux/ip.h:84 ,
                 from /usr/src/linux-headers-2.6.15-27-386/include/net/ip.h:28,
                 from frag.c:16:
/usr/src/linux-headers-2.6.15-27-386/include/net/sock.h: In function ‘skb_copy_t o_page’:
/usr/src/linux-headers-2.6.15-27-386/include/net/sock.h:1064: warning: pointer t argets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
ld: frag.o: No such file: No such file or directory
Failed to make module "cisco_ipsec".

```


I tried the patch given in popey.com then it gives

```

root@LSIL-PrecisionM60:/home/laalitha/Desktop/vpnclient# patch -p0 < vpnclient-linux-4.7.patch.txt
patching file linuxcniapi.c
Hunk #1 succeeded at 1276 with fuzz 2 (offset 1000 lines).
Hunk #2 FAILED at 1291.
Hunk #3 FAILED at 1394.
Hunk #4 FAILED at 1436.
3 out of 4 hunks FAILED -- saving rejects to file linuxcniapi.c.rej
root@LSIL-PrecisionM60:/home/laalitha/Desktop/vpnclient#

```
When I tried to compile the file (make) it says
```

make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by underdog512 on 2006-10-29
try installing vpnc. it is available through synaptic

---

### Post by Laalitha on 2006-10-29
My school has said to use cisco vpn client. It has not given the info needed to configure vpnc which is the IPSec ID and the IPSec Secret.
So I have to install vpn client

---

### Post by underdog512 on 2006-10-29
> **Laalitha said:**
> My school has said to use cisco vpn client. It has not given the info needed to configure vpnc which is the IPSec ID and the IPSec Secret.
So I have to install vpn client

Ahh, that would be a problem

---

### Post by Laalitha on 2006-10-29
The school has given a .pcf file. I installed kvpnc and imported the profile thru that file. But when I try to connect it gives an error saying
```

Loading of module "tun" failed

```

---

### Post by ryan555 on 2006-10-29
You can still use VPNC.  Inside of the PCF file you will find the IPSec ID which is under "GroupName".  The IPSec secret is under "enc_GroupPwd" and is obfuscated.  You can unscramble it with something like Cain & Abel.

I had to do this when I got VPN access at work.  Nobody could remember the IPSec group password.

---

### Post by lo900 on 2006-10-30
thanks for the tip
vpnc is working fine for me.

I have nm, wireless, wpa

---

