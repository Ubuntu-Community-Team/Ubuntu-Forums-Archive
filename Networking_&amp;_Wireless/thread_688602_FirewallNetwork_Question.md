---
title: "Firewall/Network Question"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by redneonrt on 2008-02-05
Hello all,

First let me explain what I am trying to do...

My company has a firewall in place with a DSL connection hooked up to it.  Unfortunately I can not get rid of this firewall but I would like to make have some stronger rules in place for outgoing activity. 

My thought is to hook up the DSL line to my linux box then hook the linux box to the firewall.  That way I am hoping to have better control of who makes it through to the firewall.  I am also hoping there is something available in linux to help with QoS on the network by limiting IP's speed and ability to connect to the internet at all.

Is this a possibility? Maybe there is another solution I am not thinking of?  Could anyone offer some sort of instruction on how to set this up?

Thanks for looking,
Chris

---

### Post by mveltre on 2008-02-05
that's pretty easy to set up. You may like to use two ethernet cards for it, then enable NAT over both interfaces and bring up the firewall. For both, try out using webmin which usally helps a lot with such tasks. Download the debian .deb-file from [www.webmin.com](www.webmin.com) and install it from the console via dpkg -i webmin...deb. (just install the perl-dependencies via apt-get install ....) Then log-in on https://<yourMachinesIp:10000

---

### Post by redneonrt on 2008-02-05
> **mveltre said:**
> that's pretty easy to set up. You may like to use two ethernet cards for it, then enable NAT over both interfaces and bring up the firewall. For both, try out using webmin which usally helps a lot with such tasks. Download the debian .deb-file from [www.webmin.com](www.webmin.com) and install it from the console via dpkg -i webmin...deb. (just install the perl-dependencies via apt-get install ....) Then log-in on https://<yourMachinesIp:10000

Actually I already have Webmin setup on the box.  Also I dont know if it matters or not but DHCP is NOT handeled by the existing network firewall.  There is another server on my network that does this.  Hopefully this does not interfere with what I would like to do.

---

### Post by mveltre on 2008-02-05
i would look for HowTo's letting you know how to set-up a bridge with a firewall. For example:
[http://www.debian.org/doc/manuals/securing-debian-howto/ap-bridge-fw.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-bridge-fw.en.html)

Markus

(usally debian-howto's are usable for ubuntu)

---

### Post by rickyjones on 2008-02-05
OK, so I have a picture here, your current network is similar to:
```

                        Internet
                           |
                           |
                     Firewall Device
                           |
                           |
                          LAN

```
On your LAN you have, obviously, your servers and clients. The goal is to give yourself more definite control of your network, over what goes in and out, correct?

What you are proposing to do is create something that looks like this:
```

                        Internet
                           |
                           |
                     Firewall Device
                           |
                  New Firewall Device
                           |
                           |
                          LAN

```

Is this correct?

If so then you should be able to throw two NICs into this new router device and follow one of the many how-to's to enable NAT in order to share the connection from firewall 1. Obviously you might run into IP issues so you might need to figure out if you can change the internal IP for the first firewall or change the network on the LAN side. 

I hope this helps!

-Richard

---

### Post by redneonrt on 2008-02-05
**EDIT** 

```

Internet
|
|
Existing Firewall
|
|
NEW Firewall
|
|
LAN

```

This would be the proposed setup.

---

### Post by redneonrt on 2008-02-06
Using the setup show above I have a question in regards to the hookup of the new firewall behind the existing one.

The existing firewall(Watchguard Firebox SOHO 6) has 5 ports on the back 1 labeled WAN and the others are 0-3.  In the current setup I have a 1(in the WAN slot) hooked to a router, another in the 0 spot hooked to a set of switches and the sport marked 1 is hooked to my DSL line. 

For the new setup I was thinking I should get a small network switch and hook all but the DSL line into the switch with 1 cable running from the switch to eth0 on the linux box and then 1 cable from eth1 to the existing firewall.  

Does that sound about right?


Thanks to everyone for their help so far.

Regards,
Chris

---

