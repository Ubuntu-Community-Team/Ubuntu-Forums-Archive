---
title: "Counts externally accessed IP addresses via iptables or something similar"
date: 2022-06-04
forum: Networking &amp; Wireless
---

### Post by florinmarian on 2022-06-04
Hello!
I own a hosting company and I often face the situation where my clients using weak passwords end up being broken and at the same time my VPSs become the source of scans on other hosting companies.
I managed to block through Suricata the situation in which a client scans a certain IP address for several ports or several passwords for the SSH port.
What I fail to do is prevent a client from sending TCP or UDP packets to detect on a subnet / 24 which IP addresses have port 22 or another specific port open.
I recently tried iptables using the "hashlimit" module but from what I've tested, hashlimit doesn't make the difference between accessing 3 times the same 4 IP addresses in the last x seconds and accessing 12 different IP addresses in the same time frame.
Any help is welcome.
Thanks!

---

### Post by Doug S on 2022-06-05
Hi, and welcome to Ubuntu forums.

I think the "recent" module is the one you might want to try. Here is an example use for detecting and preventing incoming SSH attacks on my server:

```
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --mask $BIT_MASK --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --mask $BIT_MASK --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --mask $BIT_MASK --set --name BADGUY_SSH -j ACCEPT

``` Where:

```

IPTABLES=/sbin/iptables
EXTIF="enp1s0"
BIT_MASK="255.255.252.0"
UNIVERSE="0.0.0.0/0"

```

And, of course, this rule is somewhere earlier:

```
# Allow any related traffic coming back to the server in.
#
#
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
```

I do not understand enough about your application to know if such code would need to be modified to go in the OUTPUT or FORWARD chain. Depending on the magnitude of your issues and your desired hitcounts, you might need to increase table sizes from the default values.

---

### Post by florinmarian on 2022-06-05
Thank you very much, although I had passed this option, I think it can still be useful.


I control the OUT chain because I recursively apply the rules at the host level but over each interface that belongs to a certain VM.
Unlike your example, I need to check if my client has ever accessed 10 IP addresses from the X.X.X.X / 24 network in the last 10 seconds or something similar.

---

### Post by Doug S on 2022-06-05
Okay, thanks. Yes, this is a challenge. I do not have any good ideas. I do have a not very good idea, with flaws. In pseudo code would be:

```

use iptables recent module to watch for outgoing per IP tcp connections to port 22.
If the hitcount gets to 2, then reset the /24 table.

If the /24 table gets to a hitcount of 10 within 10 seconds then make a log entry and DROP the attempt.

```The flaws are that 2 attempts to one address is all it takes to delete the table, and the entire table is deleted, which might include an in progress count up on another subnet.

It would take me awhile to convert the pseudo code to actual iptables rules.

---

