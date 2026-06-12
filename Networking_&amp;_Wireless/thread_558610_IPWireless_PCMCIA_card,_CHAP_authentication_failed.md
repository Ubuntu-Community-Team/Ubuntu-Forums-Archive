---
title: "IPWireless PCMCIA card, CHAP authentication failed"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by AustinMarton on 2007-09-24
Hi there,

I'm finally making head way on getting my IPWireless PCMCIA card from Woosh to work. This fabulous little tutorial has made the lights come on:
[https://help.ubuntu.com/community/IpwirelessPcmcia?highlight=%28IpwirelessPcmcia%29](https://help.ubuntu.com/community/IpwirelessPcmcia?highlight=%28IpwirelessPcmcia%29)

I'm trying to connect now but after a few hours I haven't had any luck. I'm using the Network tools in the System menu. I'm sure it's on 'ttyIPWp0' and I'm dialing '*99#' as I have been told by the woosh wireless tech support. (one point that confuses me is how does it know it's dialing woosh? It must be programmed into the modem already?)

I've been monitoring what's happening in the /var/log/syslog file and it seems to try connect and then I get the error: 'CHAP authentication failed: Bad Password'
I know the password is correct.

Any help? Ideas? 

Thanks for reading,
Austin.

---

### Post by AustinMarton on 2007-09-25
My problem is solved! I had to add "@woosh.co.nz" to the end of my username.

---

