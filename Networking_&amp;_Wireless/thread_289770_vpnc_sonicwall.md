---
title: "vpnc sonicwall"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by mega on 2006-10-31
I setup a standard vpnc for my client on a sonicwall firewall

my config file for vpnc looks like this

IPSec gateway myfirewallip
IPSec ID WAN GroupVPN
IPSec secret mysecret
Xauth password mypass
Xauth username myname


I get this error from vpnc
vpnc: response was invalid [1]: ISAKMP_N_INVALID_EXCHANGE_TYPE(7)


and this error on the firewall

10/31/2006 10:30:41.624    Warning    VPN IKE    IKE Responder: Proposed IKE ID mismatch    clientip, 500 (sysadmin)    firewallip, 500    VPN Policy NOT found for proposed ID type: KEY ID 


any ideas?

---

### Post by mega on 2006-10-31
2 views, guess nobody uses sonicwall's?

---

### Post by alaman on 2006-10-31
check to see if you have black characters at the end of your vpnc conf secret line.  It may be using the blank as part of the secret causing it to be incorrect.

---

### Post by mega on 2006-10-31
no blank spaces, verified everything is right

the firewall rejects it every time

---

### Post by alaman on 2006-10-31
what are the IKE settings on your firewall (should be under VPN, settings, proposals)?  You can check out the doc here --> [http://www.vpnc.org/InteropProfiles/](http://www.vpnc.org/InteropProfiles/)  for Sonicwall screenshots.

The other thing that jumped out at me was after your IPSec ID - you have WAN then your key....I don't think WAN should be there - just IPSEC ID ******

---

### Post by mega on 2006-10-31
> **alaman said:**
> what are the IKE settings on your firewall (should be under VPN, settings, proposals)?  You can check out the doc here --> [http://www.vpnc.org/InteropProfiles/](http://www.vpnc.org/InteropProfiles/)  for Sonicwall screenshots.

The other thing that jumped out at me was after your IPSec ID - you have WAN then your key....I don't think WAN should be there - just IPSEC ID ******

the new sonicwall firmware is nothing like that

I have 3 screenshots from the firewall config here..

[http://freddy.geekopolis.com/gallery2/main.php?g2_view=core.ShowItem&g2_itemId=4059]("http://freddy.geekopolis.com/gallery2/main.php?g2_view=core.ShowItem&g2_itemId=4059")

I made this change to vpnc.conf

IKE DH Group 2

and get this error

vpnc: IKE DH Group "2" unsupported

---

### Post by alaman on 2006-10-31
try this config - 

IPSec gateway myfirewallip
IPSec ID WAN GroupVPN
IPSec secret secert
Xauth username 
Debug 2

dh2 is default so you shouldn't need to force it. and can you send the messages from both the client & gateway - this should increase the debugging so we can isolate the issue a bit more.

---

### Post by mega on 2006-10-31
same error on the firewall

vpnc says this

mega@mainpc:/etc/vpnc$ sudo vpnc vpnc.conf
vpnc version 0.3.3
S1
S2
S3
using interface tun0
S4
S4.1
S4.2
S4.3
S4.4
vpnc: response was invalid [1]: ISAKMP_N_INVALID_EXCHANGE_TYPE(7)

---

### Post by alaman on 2006-11-01
it looks like it should work.  Can you up the debug to 3 and lets see what the fw & client don't agree on?

---

### Post by mega on 2006-11-20
here's the debug3 log

hex_test: 00010203
vpnc version 0.3.3
S1
S2
S3
using interface tun0
S4
S4.1
i_cookie: 424ece16 7e579267
i_nonce: 3716f68b 592f265f 596132ce c5ad3f66 2df848e9
S4.2
dh_public:
e9f149ce 8b9e0c50 a4d394a6 aff75eeb 663bd874 c50c5b41 05577227 f7df5fcc
0860685d 337f659f 1f22161c f40598fd abc51b99 6f6fcea0 915fb36b 432bc2e7
5cbf1fb8 8482645e 8e22c8d8 14d9539b 9ca86b15 97626280 2b889c95 920a0777
b53c4bf7 47edf87c 28c418f6 3c0f4389 5d1ef34f 78519de0 87d30ac6 8bec2f09
S4.3

 sending: ========================>

BEGIN_PARSE
i_cookie: 424ece16 7e579267
r_cookie: 00000000 00000000
payload: 01
isakmp_version: 10
exchange_type: 04
flags: 00
message_id: 00000000
len: 00000384
PARSING PAYLOAD type: 01
next_type: 04
length: 0284
sa.doi: 00000001
sa.situation: 00000001
PARSING PAYLOAD type: 02
next_type: 00
length: 0278
p.number: 00
p.prot_id: 01
p.spi_size: 00
length: 10
p.spi: 
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 00
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 0100
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0002
t.attributes.type: 0003
t.attributes.u.attr_16: fde9
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 01
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 0100
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0001
t.attributes.type: 0003
t.attributes.u.attr_16: fde9
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 02
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 00c0
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0002
t.attributes.type: 0003
t.attributes.u.attr_16: fde9
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 03
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 00c0
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0001
t.attributes.type: 0003
t.attributes.u.attr_16: fde9
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 04
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 0080
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0002
t.attributes.type: 0003
t.attributes.u.attr_16: fde9
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 05
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 0080
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0001
t.attributes.type: 0003
t.attributes.u.attr_16: fde9
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0024
t.number: 06
t.id: 01
t.attributes.type: 0001
t.attributes.u.attr_16: 0005
t.attributes.type: 0002
t.attributes.u.attr_16: 0002
t.attributes.type: 0003
t.attributes.u.attr_16: fde9
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0024
t.number: 07
t.id: 01
t.attributes.type: 0001
t.attributes.u.attr_16: 0005
t.attributes.type: 0002
t.attributes.u.attr_16: 0001
t.attributes.type: 0003
t.attributes.u.attr_16: fde9
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 08
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 0100
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0002
t.attributes.type: 0003
t.attributes.u.attr_16: 0001
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 09
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 0100
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0001
t.attributes.type: 0003
t.attributes.u.attr_16: 0001
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 0a
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 00c0
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0002
t.attributes.type: 0003
t.attributes.u.attr_16: 0001
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 0b
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 00c0
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0001
t.attributes.type: 0003
t.attributes.u.attr_16: 0001
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 0c
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 0080
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0002
t.attributes.type: 0003
t.attributes.u.attr_16: 0001
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0028
t.number: 0d
t.id: 01
t.attributes.type: 000e
t.attributes.u.attr_16: 0080
t.attributes.type: 0001
t.attributes.u.attr_16: 0007
t.attributes.type: 0002
t.attributes.u.attr_16: 0001
t.attributes.type: 0003
t.attributes.u.attr_16: 0001
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 03
length: 0024
t.number: 0e
t.id: 01
t.attributes.type: 0001
t.attributes.u.attr_16: 0005
t.attributes.type: 0002
t.attributes.u.attr_16: 0002
t.attributes.type: 0003
t.attributes.u.attr_16: 0001
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 03
next_type: 00
length: 0024
t.number: 0f
t.id: 01
t.attributes.type: 0001
t.attributes.u.attr_16: 0005
t.attributes.type: 0002
t.attributes.u.attr_16: 0001
t.attributes.type: 0003
t.attributes.u.attr_16: 0001
t.attributes.type: 0004
t.attributes.u.attr_16: 0002
t.attributes.type: 000b
t.attributes.u.attr_16: 0001
t.attributes.type: 000c
t.attributes.u.lots.length: 0004
t.attributes.u.lots.data: 0020c49b
DONE PARSING PAYLOAD type: 03
PARSING PAYLOAD type: 00
DONE PARSING PAYLOAD type: 02
PARSING PAYLOAD type: 00
DONE PARSING PAYLOAD type: 01
PARSING PAYLOAD type: 04
next_type: 0a
length: 0084
ke.data:
e9f149ce 8b9e0c50 a4d394a6 aff75eeb 663bd874 c50c5b41 05577227 f7df5fcc
0860685d 337f659f 1f22161c f40598fd abc51b99 6f6fcea0 915fb36b 432bc2e7
5cbf1fb8 8482645e 8e22c8d8 14d9539b 9ca86b15 97626280 2b889c95 920a0777
b53c4bf7 47edf87c 28c418f6 3c0f4389 5d1ef34f 78519de0 87d30ac6 8bec2f09
DONE PARSING PAYLOAD type: 04
PARSING PAYLOAD type: 0a
next_type: 05
length: 0018
ke.data: 3716f68b 592f265f 596132ce c5ad3f66 2df848e9
DONE PARSING PAYLOAD type: 0a
PARSING PAYLOAD type: 05
next_type: 0d
length: 0014
id.type: 0b
id.protocol: 11
id.port: f401
id.data: 57414e20 47726f75 7056504e
DONE PARSING PAYLOAD type: 05
PARSING PAYLOAD type: 0d
next_type: 0d
length: 000c
ke.data: 09002689 dfd6b712
DONE PARSING PAYLOAD type: 0d
PARSING PAYLOAD type: 0d
next_type: 0d
length: 0014
ke.data: 12f5f28c 457168a9 702d9fe2 74cc0100
DONE PARSING PAYLOAD type: 0d
PARSING PAYLOAD type: 0d
next_type: 00
length: 0014
ke.data: 90cb8091 3ebb696e 086381b5 ec427b1f
DONE PARSING PAYLOAD type: 0d
PARSING PAYLOAD type: 00
PARSE_OK

S4.4

BEGIN_PARSE
i_cookie: 424ece16 7e579267
r_cookie: 28ccee9d 4ae4c80e
payload: 0b
isakmp_version: 10
exchange_type: 05
flags: 00
message_id: 00000000
len: 00000064
PARSING PAYLOAD type: 0b
next_type: 00
length: 0048
n.doi: 00000000
n.protocol: 01
n.spi_length: 10
n.type: 0012
n.spi: 424ece16 7e579267 28ccee9d 4ae4c80e
n.data:
00060004 00000000 00040020 00000054 68652049 4420696e 666f726d 6174696f
6e206973 20696e76 616c6964
DONE PARSING PAYLOAD type: 0b
PARSING PAYLOAD type: 00
PARSE_OK
vpnc: response was invalid [1]: ISAKMP_N_INVALID_EXCHANGE_TYPE(7)

---

### Post by lee_connell on 2007-02-28
i have same problem on cisco firewalls that require not only a group name and password but also a username and password.  same error as posted.

---

### Post by rodda on 2007-03-07
Same problem here using Sonicwall Pro 4060 + Ubuntu Edgy.  I've tried about every configuration on the Sonicwall but no difference.

---

### Post by MikeDX on 2007-03-12
Hmm

this isn't great is it...

I too need to login to a sonicwall vpn to remote access to the office network, but without a linux client I fear I may have to reinstall windows or use a virtual machine just to network!!! That really sucks.

---

### Post by fortran01 on 2007-08-21
Any updates on Linux client for sonicwall vpn?

---

### Post by fortran01 on 2008-05-05
Sonicwall to some extent suckz!

---

