---
title: "How to make my Smart TV get internet?"
date: 2018-12-10
forum: Networking &amp; Wireless
---

### Post by Mailosealsul on 2018-12-10
Hello All

I bought Smart TV recently and installed it under my NAS(with Ubuntu 18.04).
NAS get private IP from router(sorry for missing router in the attached picture, Router is between ISP modem and switch)
NAS has two wired network interfaces , one is eth0(WAN from switch) and another is eth1(To Smart TV)
I'd like to make my Smart TV have different IP but in same Network with NAS(To use DNLA fucntion from other device)

I did lots of try with brctl(bridge-utill) but no success and already messed up much to explain what I tried

So, I make /etc/network/interfaces back to
auto lo
iface lo inet loopback

I already googled during last 3 days but no clear help from them.
Can you anyone help me on this matter?

[IMG]https://lh3.googleusercontent.com/47tXSm0NBLPEZxn8VQ546oxxszq8Mzn9ch233xu494qhmbLDBLnacvw7U-xHRyigvnaK4ahwlDgaAH-t79YYFOp1Uvcy_6-qHj3Pk_IS0fc93aMOFzaAO2sUsce8jNowD8S4LEzIWEYzbnGKNwsDCcmkDKUrXdbDXseOhhH4D6clylQFAoioKW9HYjFKJYW3dZWIMnt2ht43qaF1WTiOMGLWpFbgVbV6oAV2Ob-yjl-64W4tVCVCJBLZQMDZdokr7X4BNOFuQbnKW5Q6AFdSLgD7Oa0lffe-XS1g78mq91XmWgwg6iY_0S1rY_TrIG20cpiZUhWo9_4zXttI9S9rNTk9LX0ZRE3QiCdIRvDB4sq_vaHcd3xK0a0nn8AGY3nu-H6PWKgxwmdAIQA8PPqdYIVi-dhOi-wjWwxXw_9Flz62ZM_s4_5g4cMT4VjvFQ4zaUn7mZ8H9pP-jTDPAhwBBGvntC3pAk2-eQT8nDAs_o5uyfb2k2zmokrR7ABhClKLz51NL9ZDmtltwwCYx8JdUbarQUApK8Fzt3sxE5pEAa3Q6Iy5mUaZi__0-uT0MFUozFCk_SF8bMRvnuSzpJBC1h8GyM2qtY3yxC4bIq-cS9N1iAnlkCkF39aHUNvMtyV-LwX2S1-_wrxNTdcSkfLEenBd=w931-h734-no[/IMG]

---

### Post by aromo2 on 2018-12-10
Why don't you connect the TV directly to the switch?

---

### Post by Mailosealsul on 2018-12-30
Because, only 2 wired UTP port on the wall available and it's already occupied by others.
But, it's solved already since below worked well in /etc/network/interfaces

> auto lo br0
iface lo inet loopback

iface eth0 inet manual
iface eth1 inet manual

iface br0 inet dhcp
bridge_ports eth0 eth1
bridge_stp off
bridge_fd 0
bridge_maxwait 0

---

