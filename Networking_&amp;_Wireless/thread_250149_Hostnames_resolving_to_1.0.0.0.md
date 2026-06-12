---
title: "Hostnames resolving to 1.0.0.0"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by perlmonkey on 2006-09-03
I've been having a weird problem on my newly installed Ubuntu 6.06 machine. When an application tries to resolve a hostname to an IP address,  most times it gets resolved to 1.0.0.0.

My router (ASUS AAM6020VI) uses dproxy to proxy DNS for my LAN. I would be inclined to believe that the router is causing the problems because when I change the DNS to point away from my router DNS resolution works as expected. However I am not totally convinced the router is the problem as the same setup works fine on Windows XP and Debian and on different machines.

I managed to temporarily resolve the problem by manually editing /etc/resolv.conf and adding different nameservers in. However when my PC is rebooted this file is overwritten and the nameservers are changed back to the IP address of my router. This can also be resolved by pinging the hostname from the command line until it resolves the correct ip and then going back to whatever application you where trying to use.

There is nowhere in my router where I can manually specify DNS to be handed out by DHCP and it has the latest firmware installed (AFAICT from the ASUS website). I have searched these forums and found threads with users describing similar problems but no solutions have been found.

The easiest way I can see to fix this is to have a static /etc/resolv.conf so if anybody can tell me a clean way of doing this (ie: not 'chmod 444 /etc/resolv.conf') that would be great. Or if anybody can offer any other suggestions on what the problem may be or what I can try to fix it it would be greatly appreciated! TIA!

---

### Post by Darkling on 2006-09-03
I have a similar problem with my DLink 504T router. It seems to be a recurring theme with DLink routers, and, apparently, yours. I have had the same problem on Gentoo and SuSE, and its been happening for more than 2 years now since I got the router.

Anyway, I fixed it in Ubuntu by editing the /etc/dhcp3/dhclient-script and commenting out the make_resolv_conf() function. Then adding my dns entries into resolv.conf.
Unfortunately in 2 years of looking, I havent found a better solution than that.

---

### Post by perlmonkey on 2006-09-03
> **Darkling said:**
> I have a similar problem with my DLink 504T router. It seems to be a recurring theme with DLink routers, and, apparently, yours. I have had the same problem on Gentoo and SuSE, and its been happening for more than 2 years now since I got the router.

Interesting that it happens on some distros but not others. I might double check Debian next time I install it and make sure it **was** using my router as a nameserver. It was late and I was getting frustrated with the problem so I may have been incorrect about Debian working ok. It definitely works ok in XP though.

> **Darkling said:**
> Anyway, I fixed it in Ubuntu by editing the /etc/dhcp3/dhclient-script and commenting out the make_resolv_conf() function. Then adding my dns entries into resolv.conf.
Unfortunately in 2 years of looking, I havent found a better solution than that.

Awesome, thats clean enough for me. Thanks!

---

### Post by hantu on 2006-09-05
> **Darkling said:**
> Anyway, I fixed it in Ubuntu by editing the /etc/dhcp3/dhclient-script and commenting out the make_resolv_conf() function. Then adding my dns entries into resolv.conf.
Unfortunately in 2 years of looking, I havent found a better solution than that.

Got the same problem when I was using gentoo as well. I'm on a netcomm nb5 router, i didn't modify the dhclient-script, just edited the nameservers with my dns ip's in both the cases (gentoo, and ubuntu), now its all fine ;)

thanks.

---

### Post by sfaoldun on 2006-09-06
I had this problem on my Thinkpad when put on a network using private IP addresses (the problem didn't manifest itself on public IPs). I fixed it by commenting out the lines in dh-client as mentioned above and by disabling ipv6 (this seems to be confusing my DSL-504T). I also changed the DNS servers in /etc/resolv.conf from 192.168.1.1 to those provided by my ISP.

---

### Post by ray73864 on 2006-09-07
I too had this problem at one stage, however, when i went to forums and all to find out how to resolve it, the same recurring pattern appeared, either people weren't giving enough information, or the people replying with suggestions on how to fix it were just pulling answers out of a hat.

Basically, to fix it, you need to do a few things to get it working all the time.

The answer to the problem, is that D-Link routers (and probably some others) AREN'T actually DNS servers, they are merely DNS forwarders, unfortunately, Ubuntu (and some other linux OSes) don't realise this (Windows has the unique ability to not care about it and use it as a DNS server).

Unfortunately, the router gives Linux the impression that it is a DNS Server, so until router manufacturers start learning the difference between DNS servers and DNS forwarders, OS's like Ubuntu might be plagued with this problem for a while.

if you check /etc/resolv.conf you will find that the only nameserver in there will be to your router, this, is a problem, since it causes Ubuntu to think that the IP address is a DNS server not a DNS forwarder, to get it to work, you need to remove that line, and put the IP address to your ISPs DNS server in there instead, once you have done this, everything will work just fine.

However, Ubuntu has a daemon process that runs called 'dhclient3' this will mangle the /etc/resolv.conf file every time you reboot, or roughly every couple of hours, the way to fix it is to either kill the process and not let it run again (bad idea, since then you won't get a renewed IP address anymore) or, find the section that changes the /etc/resolv.conf line and comment it out.

Hope this helps for you, i have done this several times and it has worked for me....

Ray

---

### Post by sfaoldun on 2006-09-11
In response to Ray's post above, this is the section you should need to comment out of the dhclient script:

```
#make_resolv_conf() {
#    if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
#        # Find out whether we are going to mount / rw
#        exec 9>&0 </etc/fstab
#        rootmode=rw
#        while read dev mnt type opts dump pass junk; do
#            [ "$mnt" != / ] && continue
#            case "$opts" in
#                ro|ro,*|*,ro|*,ro,*)
#                   rootmode=ro
#                   ;;
#                 esac
#         done
#         exec 0>&9 9>&-
# 
#        # Wait for /etc/resolv.conf to become writable
#        if [ "$rootmode" = "rw" ]; then
#            while [ ! -w /etc ]; do
#                sleep 0.1
#            done
#        fi
#
#        local new_resolv_conf=/etc/resolv.conf.dhclient-new
#        rm -f $new_resolv_conf
#        if [ -n "$new_domain_name" ]; then
#            echo search $new_domain_name >>$new_resolv_conf
#        else # keep 'old' search/domain scope
#            egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> $new_resolv_conf
#        fi
#        if [ -n "$new_domain_name_servers" ]; then
#                   for nameserver in $new_domain_name_servers; do
#                       echo nameserver $nameserver >>$new_resolv_conf
#            done
#        else # keep 'old' nameservers
#            sed -n /^\w*[Nn][Aa][Mm][Ee][Ss][Ee][Rr][Vv][Ee][Rr]/p /etc/resolv.conf >>$new_resolv_conf
#        fi
#        chown --reference=/etc/resolv.conf $new_resolv_conf
#        chmod --reference=/etc/resolv.conf $new_resolv_conf
#        mv -f $new_resolv_conf /etc/resolv.conf
#    fi
#}
```

---

### Post by mango.muncher on 2006-09-11
Previous posters, thanks for assistance getting online, for now I can post this from Ubuntu.
My DLink is also being seen as the nameserver IP, however now I can at least input the correct IP and get online. Thanks again.

I commented out the  /etc/dhcp3/dhclient-script (thanks sfaoldun for showing the eg) but the correct IP is still being replaced at boot.
P.S I have opened /etc/dhcp3/dhclient-script and it saved ok.

Editor Note: Since above I have rebooted again and correct IP is being retained.
All is good.

---

### Post by AndrewS on 2006-11-06
> **Darkling said:**
> I have a similar problem with my DLink 504T router. It seems to be a recurring theme with DLink routers, and, apparently, yours. I have had the same problem on Gentoo and SuSE, and its been happening for more than 2 years now since I got the router.

Anyway, I fixed it in Ubuntu by editing the /etc/dhcp3/dhclient-script and commenting out the make_resolv_conf() function. Then adding my dns entries into resolv.conf.
Unfortunately in 2 years of looking, I havent found a better solution than that.
Hi

This thread showed me how to edit the nameserver line in reslov.conf, but as others have remarked, it reverts to the router IP at intervals (or on reboot).  The suggested fis was to edit the daemon out of /etc/dhcp3/dhclient-script.  Problem is, I can't find this file (I'm using Ubuntu 6.10) - any suggestions?

TIA

Andrew

---

### Post by mssever on 2006-11-06
> **AndrewS said:**
> This thread showed me how to edit the nameserver line in reslov.conf, but as others have remarked, it reverts to the router IP at intervals (or on reboot).  The suggested fis was to edit the daemon out of /etc/dhcp3/dhclient-script.  Problem is, I can't find this file (I'm using Ubuntu 6.10) - any suggestions?
You can simply remove write permissions from /etc/resolv.conf.


Alternately, here's my (unmodified) /etc/dhcp3/dhclient-script (owned by root:root, permissions 755):
```
#!/bin/bash

# dhclient-script for Linux. Dan Halbert, March, 1997.
# Updated for Linux 2.[12] by Brian J. Murrell, January 1999.
# Modified for Debian.  Matt Zimmerman and Eloy Paris, December 2003
# Modified to remove useless tests for antiquated kernel versions that
# this doesn't even work with anyway, and introduces a dependency on /usr
# being mounted, which causes cosmetic errors on hosts that NFS mount /usr
# Andrew Pollock, February 2005
# Modified to work on point-to-point links. Andrew Pollock, June 2005
# Modified to support passing the parameters called with to the hooks. Andrew Pollock, November 2005

# The alias handling in here probably still sucks. -mdz

make_resolv_conf() {
    if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
        # Find out whether we are going to mount / rw
        exec 9>&0 </etc/fstab
        rootmode=rw
        while read dev mnt type opts dump pass junk; do
            [ "$mnt" != / ] && continue
            case "$opts" in
                ro|ro,*|*,ro|*,ro,*)
                   rootmode=ro
                   ;;
                 esac
         done
         exec 0>&9 9>&-
 
        # Wait for /etc/resolv.conf to become writable
        if [ "$rootmode" = "rw" ]; then
            while [ ! -w /etc ]; do
                sleep 0.1
            done
        fi

        local new_resolv_conf=/etc/resolv.conf.dhclient-new
        rm -f $new_resolv_conf
        if [ -n "$new_domain_name" ]; then
            echo search $new_domain_name >>$new_resolv_conf
        else # keep 'old' search/domain scope
            egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> $new_resolv_conf
        fi
        if [ -n "$new_domain_name_servers" ]; then
                   for nameserver in $new_domain_name_servers; do
                       echo nameserver $nameserver >>$new_resolv_conf
            done
        else # keep 'old' nameservers
            sed -n /^\w*[Nn][Aa][Mm][Ee][Ss][Ee][Rr][Vv][Ee][Rr]/p /etc/resolv.conf >>$new_resolv_conf
        fi
        chown --reference=/etc/resolv.conf $new_resolv_conf
        chmod --reference=/etc/resolv.conf $new_resolv_conf
        mv -f $new_resolv_conf /etc/resolv.conf
    fi
}

run_hook() {
    local script="$1"
    local exit_status
    shift    # discard the first argument, then the rest are the script's

    if [ -f $script ]; then
        . $script "$@"
    fi


    if [ -n "$exit_status" ] && [ "$exit_status" -ne 0 ]; then
        logger -p daemon.err "$script returned non-zero exit status $exit_status"
        save_exit_status=$exit_status
    fi

    return $exit_status
}

run_hookdir() {
    local dir="$1"
    local exit_status
    shift    # See run_hook

    if [ -d "$dir" ]; then
        for script in $(run-parts --list $dir); do
            run_hook $script "$@" || true
            exit_status=$?
        done
    fi

    return $exit_status
}

# Must be used on exit.   Invokes the local dhcp client exit hooks, if any.
exit_with_hooks() {
    exit_status=$1

    # Source the documented exit-hook script, if it exists
    if ! run_hook /etc/dhcp3/dhclient-exit-hooks "$@"; then
        exit_status=$?
    fi

    # Now run scripts in the Debian-specific directory.
    if ! run_hookdir /etc/dhcp3/dhclient-exit-hooks.d "$@"; then
        exit_status=$?
    fi

    # notify dhcdbd on success
    if [ -n "${dhc_dbus}" -a $exit_status -eq 0 ]; then
        /usr/bin/dbus-send \
            --system \
            --dest=com.redhat.dhcp \
            --type=method_call \
            /com/redhat/dhcp/$interface \
            com.redhat.dhcp.set \
            'string:'"`env | /bin/egrep -v '^(PATH|SHLVL|_|PWD|dhc_dbus)\='`";
    fi

    exit $exit_status
}

set_hostname() {
    local current_hostname=$(hostname)
    if [ -z "$current_hostname" -o "$current_hostname" = "(none)" ]; then
        hostname "$new_host_name"
    fi
}

if [ -n "$new_broadcast_address" ]; then
    new_broadcast_arg="broadcast $new_broadcast_address"
fi
if [ -n "$old_broadcast_address" ]; then
    old_broadcast_arg="broadcast $old_broadcast_address"
fi
if [ -n "$new_subnet_mask" ]; then
    new_subnet_arg="netmask $new_subnet_mask"
fi
if [ -n "$old_subnet_mask" ]; then
    old_subnet_arg="netmask $old_subnet_mask"
fi
if [ -n "$alias_subnet_mask" ]; then
    alias_subnet_arg="netmask $alias_subnet_mask"
fi
if [ -n "$new_interface_mtu" ]; then
    mtu_arg="mtu $new_interface_mtu"
fi
if [ -n "$IF_METRIC" ]; then
    metric_arg="metric $IF_METRIC"    # interfaces(5), "metric" option
fi


# The action starts here

# Invoke the local dhcp client enter hooks, if they exist.
run_hook /etc/dhcp3/dhclient-enter-hooks
run_hookdir /etc/dhcp3/dhclient-enter-hooks.d

# Execute the operation
case "$reason" in
    MEDIUM|ARPCHECK|ARPSEND)
        # Do nothing
        ;;
    PREINIT)
        # The DHCP client is requesting that an interface be
        # configured as required in order to send packets prior to
        # receiving an actual address. - dhclient-script(8)

        if [ -n "$alias_ip_address" ]; then
            # Bring down alias interface. Its routes will disappear too.
            ifconfig $interface:0- inet 0
        fi
        ifconfig $interface inet 0 up

        # We need to give the kernel some time to get the interface up.
        sleep 1
        ;;
    BOUND|RENEW|REBIND|REBOOT)

        set_hostname
        
        if [ -n "$old_ip_address" -a -n "$alias_ip_address" -a \
             "$alias_ip_address" != "$old_ip_address" ]; then
            # Possible new alias. Remove old alias.
            ifconfig $interface:0- inet 0
        fi

        if [ -n "$old_ip_address" -a \
             "$old_ip_address" != "$new_ip_address" ]; then
            # IP address changed. Bringing down the interface will delete all routes,
            # and clear the ARP cache.
            ifconfig $interface inet 0

        fi

        if [ -z "$old_ip_address" -o "$old_ip_address" != "$new_ip_address" -o \
            "$reason" = "BOUND" -o "$reason" = "REBOOT" ]; then

            ifconfig $interface inet $new_ip_address $new_subnet_arg \
                $new_broadcast_arg $mtu_arg

            for router in $new_routers; do
                route add default dev $interface gw $router $metric_arg
            done
        fi

        if [ "$new_ip_address" != "$alias_ip_address" -a -n "$alias_ip_address" ];
            then
            ifconfig $interface:0- inet 0
            ifconfig $interface:0 inet $alias_ip_address $alias_subnet_arg
            route add -host $alias_ip_address $interface:0
        fi

        make_resolv_conf

        ;;

    EXPIRE|FAIL|RELEASE|STOP)
        if [ -n "$alias_ip_address" ]; then
            # Turn off alias interface.
            ifconfig $interface:0- inet 0
        fi

        if [ -n "$old_ip_address" ]; then
            # Shut down interface, which will delete routes and clear arp cache.
            ifconfig $interface inet 0
        fi

        if [ -n "$alias_ip_address" ]; then
            ifconfig $interface:0 inet $alias_ip_address $alias_subnet_arg
            route add -host $alias_ip_address $interface:0
        fi

        ;;

    TIMEOUT)
        if [ -n "$alias_ip_address" ]; then
            ifconfig $interface:0- inet 0
        fi

        ifconfig $interface inet $new_ip_address $new_subnet_arg \
            $new_broadcast_arg $mtu_arg

        set -- $new_routers
        first_router="$1"

        if ping -q -c 1 $first_router; then
            if [ "$new_ip_address" != "$alias_ip_address" -a \
                -n "$alias_ip_address" ]; then
                ifconfig $interface:0 inet $alias_ip_address $alias_subnet_arg
                route add -host $alias_ip_address dev $interface:0
            fi
        
        # point to point
        if [ "$new_subnet_mask" == "255.255.255.255" ]; then
            for router in $new_routers; do
                route add -host $router dev $interface
            done
        fi

            for router in $new_routers; do
                route add default dev $interface gw $router $metric_arg
            done

            make_resolv_conf
        else
            # Changed from 'ifconfig $interface inet 0 down' - see Debian bug #144666
            ifconfig $interface inet 0
            exit_with_hooks 2 "$@"
        fi

        ;;
esac

exit_with_hooks 0
```I'm running edgy, but upgraded from dapper. I don't know whether or not this is a dapper relic.

---

### Post by stream303 on 2006-11-07
Ray! I've been searching for the real reason the cheaper hardware fakes out DNS for years and couldn't find it until now.  Thanks!

If you know your real nameserver IP addresses, the easiest way to make sure that /etc/resolv.conf gets written correctly (and stays that way) by dhclient is to edit (as root)

/etc/dhcp3/dhclient.conf

Look for the prepend line that is commented out:

#prepend domain-name-servers 127.0.0.1;

and either copy it and uncomment it out and put in your nameservers:

prepend domain-name-servers 123.45.67.89;
(in the case of only one dns server)

or in the case of multiple servers:
prepend domain-name-servers 123.45.67.89, 123.45.67.90;

where you substitute your real ip addresses of course.

Note that domain-name-servers has an "s" at the end, and don't forget the comma and trailing semicolon.

Reboot or more elegantly bring your ethernet interface down and back up.

---

### Post by AndrewS on 2006-11-07
Hi

I picked up that solution from "Handy" on another thread (he gave you due credit!) - works fine.

Thanks

Andrew

---

### Post by jmfv on 2006-11-25
Hi

I have a DLINK 624T and got it working using other way. I'm posting it because it allows for IPV6 and does not involve messing with the dhcp files in your linux box. Since changing the dhcp configuration files (as proposed in the other posts) may get you into trouble when trying to connect to other networks (at work, at a friend's place, etc.), here goes my 2 cents.


The problem is the router's automatic DNS, so make it manual _in the router_ and keep the changes in your computer to a minimum, as follows

**Router Configuration**
Enable "*Manual DNS Mode*" in the router configuration. The *Primary DNS* is the your ISP's DNS (ask your ISP or look in the router, DLINK 624T shows it in Home/DNS tab) and the *Secondary DNS* is your router's IP (usually 192.168.1.1). For example

*Primary DNS:* 123.111.222.121
*Secondary DNS:* 192.168.1.1

**Linux Configuration**
Now tell your Linux distro the DNS servers for your home connection. I'm using Debian and wpa_supplicant, so my */etc/network/interfaces* file looks something like this
[INDENT][I]
iface eth1-home inet dhcp
wpa-driver wext	
	wpa-conf /etc/wpa_supplicant.conf
	dns-nameservers 123.111.222.121 192.168.1.1

iface eth1-default inet dhcp
	wpa-driver wext	
	wpa-conf /etc/wpa_supplicant.conf[/I][/INDENT]

The */etc/wpa_supplicant.conf* file contains
[I]
[INDENT]#Home
network={
       ssid="HOMEDLINK"    #wireless SSID at home
        key_mgmt=NONE
        wep_key0=1234567890 #your wep key
        priority=5
}

#Associate with any open access point (weak priority)
network={
        ssid=""
        key_mgmt=NONE
        priority=0
}[/INDENT][/I]

At home, I bring the network up by running
[INDENT]*ifup eth1=home*[/INDENT]
and at other places I use
[INDENT] *ifup eth1=default*[/INDENT]
I find this much more flexible than having to change the dhcp configuration files all the time. If you want to automate things even more, try using the ifscheme (but that's another story...)

Moreover, since this solution bypasses the router's DNS and connects directly to the ISP's DNS server, you can enable IPV6 back.

I hope someone finds this interesting 
Cheers.

---

### Post by Hachi-Roku on 2006-12-05
Hey.
I changed that line in dhclient.conf and put my isp DNS addy's in the DNS list in system>admin>network>DNS .... rather than my router address.

all seems good now.

cheers!
Jon

---

### Post by macjones on 2007-01-22
Could someone at Canonical look at this !!

Heaps of people all over the net are having issues with certian models of router sending back 1.0.0.0 for any DNS request. 

Answers include 
- Set DNS in the router manually
- Set DNS in the computer manually (and lock/stop changing of resolv.conf)
- Disabling ipv6 as well.

In my situation I have a standard build that needs to go worldwide with no editing or setting of manual DNS in the PC. (This also means that I can't access a clients ADSL modem to put the DNS settings in there).

Windows machines work fine (as noted in the DNS Server / Forwarder post by ray73864 above.

On some of the routers, installing later firmware fixes it.

These solutions are not actually solutions at all, they are workarounds, I'm unable to find a fix for it that does not involve setting manual DNS in the PC or router, but without this I can't use Ubuntu for my clients !!!

Why can't we do whatever windows does and have it "just work".

Do a google search for Ubuntu 1.0.0.0 and you'll see how many times this issue is happening !

(One forum suggested it could it be an MTU too high / iptables issue?) 

Regards
Mac
New Zealand

---

### Post by jmfv on 2007-02-12
Hi, macjones

Sorry to disagree, but this router actually doesn't work with IPV6 _**in Windows**_. That is, you have to follow the "workaround" even in Windows to get IPv6 working (or disable IPV6 completely) . 

[http://whirlpool.net.au/forum-replies-archive.cfm/476006.html](http://whirlpool.net.au/forum-replies-archive.cfm/476006.html)

If you look in other forums, you can see that the 1.0.0.0 problem is due to the routers DNS relay service that is buggy, so it is not a Linux specific problem. 
[http://www.linuxquestions.org/questions/showthread.php?t=341857](http://www.linuxquestions.org/questions/showthread.php?t=341857)

Moreover, you can't expect an Operating System to solve peripherals' bugs all the time. It is up to the manufacturer to support its own hardware, right?

> Why can't we do whatever windows does and have it "just work".
If you are willing to solve the problem, you can always submit a patch. This is open source world, buddy! ;) 


Cheers 
J.V.

---

