---
title: "VPNC no longer reliably working on Ubuntu 22.04"
date: 2023-05-15
forum: Networking &amp; Wireless
---

### Post by extraspecialbitter2 on 2023-05-15
I've been using vpnc as a Linux-friendly command line alternative to Palo Alto Network's GlobalProtect for over 4 years, and it's worked very reliably until recently. I upgraded to version 22.04 several months ago, but I've made no major updates since then.

The error always looks like this:

```

user@server=> vpnc <conf-file>
vpnc: no response from target
```

I'm curious to see if others have reported this, and if there's something new I need to do to get this working again.

Thanks!

Paul

---

### Post by #&amp;thj^% on 2023-05-15
from an upgrade, and only a stab in the dark....it's necessary to properly close previously open connection with "vpnc-disconnect"
That helped me in 2020(Year not version)
If that don't work then run it as:
```
sudo vpnc <mycommand> --debug 99
```
Might give a little more insight.

---

### Post by extraspecialbitter2 on 2023-05-15
Thanks for the suggestion. As one would expect, there was plenty of output, but the last few lines seemed interesting:

```

   PARSING PAYLOAD type: 00 (ISAKMP_PAYLOAD_NONE)
   PARSE_OK
   initial_iv: 3cb42ae7 89291087 f46dcd11 eb8db4df
   NAT-T mode, adding non-esp marker
   Received UDP NAT-Keepalive bug nat active mode incorrect: 3
   Received UDP NAT-Keepalive bug nat active mode incorrect: 3
vpnc: no response from target

```

---

### Post by #&amp;thj^% on 2023-05-15
Nothing there helps me, but is openssl installed?:
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> apt policy openssl
openssl:
  Installed: 3.0.8-1ubuntu1.1
  Candidate: 3.0.8-1ubuntu1.1
  Version table:
 *** 3.0.8-1ubuntu1.1 500
        500 http://archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.0.8-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages

``` 
Again I'm guessing, but this is why I ask:
```
PARSING PAYLOAD type: 00 (ISAKMP_PAYLOAD_NONE)
```

---

### Post by extraspecialbitter2 on 2023-05-16
Thanks for the reply. As it turns out, openssl is installed.

```

root@tiburon-7080:/etc/vpnc# apt policy openssl
openssl:
  Installed: 3.0.2-0ubuntu1.9
  Candidate: 3.0.2-0ubuntu1.9
  Version table:
 *** 3.0.2-0ubuntu1.9 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.0.2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

I'm reading that vpnc stopped working with 22.04, but that doesn't match with my experience, which is that it worked up until 2 or 3 weeks ago.

---

### Post by extraspecialbitter2 on 2023-05-16
A strange thing just happened. I decided to run `vpnc <config-file> --debug 99 | tee <output-file>` so that I can share more of it here, and the command worked successfully. Apart from multiple reboots and restarts of the network, I've made no changes.

---

### Post by #&amp;thj^% on 2023-05-16
Is it working now then?

---

### Post by extraspecialbitter2 on 2023-05-16
> **1fallen said:**
> Is it working now then?

Well - sort of. Within minutes after successfully connecting, my VPN connection failed. Then, after stopping and starting my WiFi connection, I was able to connect again.

---

### Post by #&amp;thj^% on 2023-05-16
Is the WiFi your main choice? You may want to play with power settings if that is the case.

---

### Post by extraspecialbitter2 on 2023-05-17
> **1fallen said:**
> Is the WiFi your main choice? You may want to play with power settings if that is the case.

On this particular desktop, a Dell OptiPlex 7080, it's my only option. I set up the power options to keep it "always on", as it is my primary workhorse.

As a matter of interest, my VPN connection stayed up all night, just as it used to.

---

