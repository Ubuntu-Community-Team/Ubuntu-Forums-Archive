---
title: "Network Manager and DHCP versus AD authentication"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by ahopper on 2007-10-29
Hi, folks-

I'm fairly new to Ubuntu and Linux in general. I've managed to successfully configure my shiny new Gutsy box to authenticate against AD (yay!) but the problem is that when I reboot, authentication fails with the good old "no login servers" error message. I did some detective work, and it appears that what's happening is that winbindd is starting before I have an IP address, and once it can't reach the DC, we're done. In fact, if I log in as root after rebooting (and getting the "no logon servers" message) and restart winbindd, everything is happy again and I can proceed to logon against AD (yay!).

So, my question to you folks is: is there a way to restart winbindd when Network Manager acquires an IP address? I'm sure there's a way to do this, I just don't know enough Ubuntu voodoo yet.

Thanks in advance!
-Andy Hopper

---

### Post by Lambert on 2007-10-30
upstart is the program used in ubuntu to control loading services at boot. I'm not that familiar with upstart and how to modify things but it might be best to post in general help or another forum area to find someone with knowledge.

I'm sure you can do either of the following.

1. Modify the start up so winbindd loads later (after network is running)
2. create a script so at the end it restart winbindd.

---

### Post by ahopper on 2007-10-31
So this turned out to be a problem with the trinity of Network Manager, Roaming, and winbind. Here's what I did to get things working properly:

1. Set winbind to restart when an IPv4/6 interface comes up:
#---------- /etc/network/if-up.d/winbind ----------
#! /bin/sh
# Reload the winbind service when an interface comes up, to allow it to
# connect to the Active Directory DC

set -e

# Don't bother to restart winbind when lo is configured.
if [ "$IFACE" = lo ]; then
        exit 0
fi

# Only run from ifup.
if [ "$MODE" != start ]; then
        exit 0
fi

# winbind only talks over inet and inet6.
if [ "$ADDRFAM" != inet ] && [ "$ADDRFAM" != inet6 ]; then
        exit 0
fi

# Is winbindd present?
if [ ! -e /usr/sbin/winbindd ]; then
        exit 0
fi

# Restart the winbind daemon
/etc/init.d/winbind restart >/dev/null 2>&1 || true

exit 0
#----------------------------------------

(also, mark it as executable with 'chmod 755 /etc/network/if-up.d/winbind')

2. Set the wireless connection up to be manual instead of roaming. It appears that NetworkManager doesn't obtain a DHCP address until you login if it's set to roaming, but winbind can't authenticate you if it's not able to connect to the DC.

Now, it's possible that this could be solved by just setting NetworkManager to manual, but in my humble opinion it makes more sense to have winbind refresh when an interface comes up seeing how it depends upon the interface being present to function.

-Andy

---

### Post by leif81 on 2008-01-25
> **ahopper said:**
> 
2. Set the wireless connection up to be manual instead of roaming. It appears that NetworkManager doesn't obtain a DHCP address until you login if it's set to roaming, but winbind can't authenticate you if it's not able to connect to the DC.


I'm having the same problem as you originally described but on Fedora 8. I'm not sure what "Roaming" is though? Google points to something that sounds like a ubuntu specific tool ([https://wiki.ubuntu.com/NetworkRoaming](https://wiki.ubuntu.com/NetworkRoaming)). I imagine this roaming tool is just a fancy interface to some network scripts. Any idea what exactly it's doing that would allow NetworkManager to give you an ip before login?

---

