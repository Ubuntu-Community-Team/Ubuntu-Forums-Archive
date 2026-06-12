---
title: "Reliance Wimax"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by rishabhsagar on 2008-02-10
Hi All,

    I am having Reliance Wimax internet connection which picks up signal from a POE antenna and gives me the signal thru the ethernet cable.  I have newly installed Ubuntu Gutsy Gibbon, but unable to connect to the internet thru this connection....

     This is what I know about the connection:

1> The connection tags using my MAC address.
2> I tried switching on the antenna only after connecting the cable, but this did not work out.
3> The connection is based on DHCP.
4> Unable to use dhcpcd command, since it is not yet installed.

Can someone please help me connecting to internet with this connection pls.

---

### Post by rishabhsagar on 2008-02-16
BUMP.... Someone reply please....

---

### Post by pk_rulz on 2008-02-21
i even installed dhcpcd from the debian repo still no use somebody please help

---

### Post by pk_rulz on 2008-02-25
Finally fixed the problem... The issue was avahi daemon... it was assigning a IPv6 addr to my eth0 ...

So I brought it down using
sudo /etc/init.d/avahi-daemon stop

then used
sudo ifconfig eth0 down
sudo ifconfig eth0 up

basically restart ur eth0

then u may use ( I dont think its necessary)
sudo dhcpcd eth0

if u got an IP

chk ifconfig again u should get a IPv4 addr

Dats it click ur browser n de dana dan 


Remove the link of avahi from /etc/init.d to stop it from coming up at boot

Cheers Happy Hackin

-----------------------------

Bye the way one more  observation

my dhcpcd succeeds only if i have acquired a lease thru windows bfore booting 2 linux ... 2 BAD

---

