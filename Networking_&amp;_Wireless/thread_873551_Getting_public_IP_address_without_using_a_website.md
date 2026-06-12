---
title: "Getting public IP address without using a website?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by recyclebin on 2008-07-29
Is there any way to get my public (external) IP address using the command line without having to resort to websites like [http://whatismyip.org](http://whatismyip.org) or telnetting into my DSL modem?

TIA

---

### Post by Tom--d on 2008-07-29
I use whats my IP for conky, which then displays my external IP

I dont know a command, as of yet, which displays tho. (Would like to know tho :))

---

### Post by sstusick on 2008-07-29
Type > ifconfigin the terminal.

---

### Post by PilotJLR on 2008-07-29
I can't take credit for this gem, but it works very well:

```

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

```

---

### Post by Kevbert on 2008-07-29
The only way to get your static fixed IP address (allocated by your ISP) offline is to go into your router setup.  For my Netgear router it's just called IP address.  The ifconfig command only gives the local IP address and not the one that the outside world sees.  Outside anyone can ping your static IP.  You can turn off the router responding to pings, in its' setup program, for added security.

---

### Post by PilotJLR on 2008-07-29
Well, that's not the ONLY way. You just need some form of communication to something external to the NAT, in order to relay back the public address.  :-)

Copy and paste the command I posted... add it to a bash script if you want to "create" a command for it. It's predicated on the services of dyndns.org, but you could do something like this on your own website, if you were so inclined.

---

### Post by recyclebin on 2008-07-29
I already have a PHP script on my website that returns my IP, but that does slow stuff down a little bit (possibly due to my slow internet connection). I was looking for a way to find my public IP without having to:

[LIST]
[*]Rely on any website.
[*]Telnet into/use the webUI for any sort of hardware. :-k
[/LIST]

In other words, I am looking for something similar to ifconfig <interface name>, but not quite, so I can find my public IP address.

Thank you for your input.

---

### Post by recyclebin on 2008-07-29
> **PilotJLR said:**
> I can't take credit for this gem, but it works very well:

```

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

```

As an aside, George Carlin > * :popcorn:

---

### Post by mcurran on 2010-02-04
Here are multiple commands for retrieving your router's public ip-address:

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

curl -s checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

curl -s [http://whatismyip.org/](http://whatismyip.org/)

lynx -dump checkip.dyndns.org

lynx -dump [www.whatismyip.com](www.whatismyip.com) | grep 'Your IP'


SOURCE/CREDIT GOES TO:  ggarron - [http://www.go2linux.org/what-is-my-public-ip-address-with-linux](http://www.go2linux.org/what-is-my-public-ip-address-with-linux)


I want to put all of these commands into a BASH script for multiple verification by simply putting a semicolon at the end of each command, but it's not working.  Setting up single command scripts for each one works, but I want to do them all-in-one.  Please let me know if you have any suggestions on correcting my script below:

#!/bin/bash

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//';

curl -s checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//';

curl -s [http://whatismyip.org/;](http://whatismyip.org/;)

lynx -dump checkip.dyndns.org;

lynx -dump [www.whatismyip.com](www.whatismyip.com) | grep 'Your IP';

exit

---

### Post by doas777 on 2010-02-04
thers a firefox addon called publicIP that will tell you in your browser status bar, if that suits your needs. many folks use it with torbutton or foxyproxy just to confirm that the proxy is working.

---

