---
title: "wired not connecting"
date: 2018-10-09
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-10-09
I continue to have problems connected with a wired connection.  

I have uploaded two pictures of my wired connection.   I will run, and post the results, of any program you want to see.

I have set the wired connection to run the vpn when connected and also unset same.  It works fine with wi-fi but not wired.

It may have something to do with a killswitch that I installed years ago and sometimes work.  It does work, however with a wifi connection.  The error I get is "activation of network connection failed".  the killswitch consists of two files (contents after "file:"):

/etc/NetworkManager/dispatcher.d/99vpnkillswitch file:
#!/bin/sh

IFFILE=/var/run/vpnkillswitch.iface

interface=$1 status=$2
case $status in
    vpn-up)
        # Get the physical device associated with the VPN connection
        nmcli -f type,device c | awk '$1~/^vpn$/ && $2~/[^\-][^\-]/ { print $2; }' > "${IFFILE}"
    ;;
    vpn-down)
        xargs -n 1 -a "${IFFILE}" nmcli device disconnect
    ;;
esac

/var/run/vpnkillswitch.iface (I have no idea what wlx00231301e738 is or what it means) file:
wlx00231301e738

---

### Post by TheFu on 2018-10-09
Simplify and test.

Is this a wired ethernet problem or a VPN problem?  Ethernet, I can help.

---

### Post by jgw on 2018-10-10
thank you for the reply - I have no idea whether its an ethernet problem or a vpn problem.  I actually makes no difference.  My machine went completely nuts.  I think that my drive is toast and am in the process of creating a new 18.04.1 dvd and will be installing a new, clean, ubuntu onto a new drive.  I am pretty well backed up so I don't expect huge problems and then I can revisit all of this.  

I am also not sure that I need a kill switch if I set the connection to start the vpn automatically.  I am also going to examine the whole kill switch thing as I will probably need to reinstall it.  

Would appreciate any help about the kill switch thing so I do it right.

---

### Post by TheFu on 2018-10-10
IMHO.

Get ethernet working perfectly. Wait a few days.
Get VPN working perfect.  Wait a few days.
Get killswitch working.

If ethernet doesn't work, then none of the others matter at all.
If VPN doesn't work, then killswitch doesn't matter at all.

Good luck you you my friend.

---

