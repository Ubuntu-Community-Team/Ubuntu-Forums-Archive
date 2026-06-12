---
title: "RT61 No DHCPOFFERS"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by jeanmarie on 2007-06-09
I've just got linux running on my old PC with a RT61 wireless lan card installed.   The installation was a no brainer and the card detected (wiht the lights on now :-)  However it's not able to obtain an IP from the my wireless hub (WEP enabled and my other PC and MAC have no issue)  ...  The connection and ESSID looks all good - it just wont get an ip???  I've tried the "iwpriv solution" et al but in vain.

The dhclient ra0 command shows:

DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received
No working leases in persistent database - sleeping.


iwconfig ra0: (simplified)
ra0   RT61 Wireless
        Encryption key: XXXX-XXXX-XXX


Is the problem with my linux or my Wireless hub (PC/MAC works fine) ?   
Please help ...

---

### Post by Newbie29 on 2007-06-09
Are you sure, you have the Wireless card's driver installed?

Since its an RT61, try this site :
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page")

---

### Post by chili555 on 2007-06-09
Is your WEP key indeed 11 characters? > Encryption key: XXXX-XXXX-XXX

# 40-or 64-bit ASCII WEP code has five characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters 

Usually, when a card will not connect, the WEP key is incorrect, the ESSID is wrong (myrouter1 is not the same as MyRouter1, etc.) or the access point is shared key and it has not been specified.```
sudo iwconfig ra0 key 0123456789 restricted
```Conversely, sometimes cards respond when 'open' is specified, rather than 'restricted'.

With all respect to my colleague Newbie29, if you see a ra0 under iwconfig and it will take a dhclient command, it is very doubtful you have no driver installed.

---

### Post by balak on 2007-06-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/78037](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/78037) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Can you post the version of the kernel you are using

```
uname -a
```

in a terminal window.

I had the same issue in the kernel 2.6.20-15-generic. However, mine is a laptop so  I could move it closer to the  access point and it usually worked.

[This is assuming you have everything setup correctly - see the previous posts]

Now, I have upgraded to kernel 2.6.20-16-generic and its a little bit better. There are a bunch of bugs filed on this issue - you can check
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/78037](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/78037)

---

