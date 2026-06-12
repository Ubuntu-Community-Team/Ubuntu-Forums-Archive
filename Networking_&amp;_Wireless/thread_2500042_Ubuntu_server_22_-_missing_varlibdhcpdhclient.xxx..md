---
title: "Ubuntu server 22 - missing /var/lib/dhcp/dhclient.xxx.leases"
date: 2024-08-20
forum: Networking &amp; Wireless
---

### Post by nonick95 on 2024-08-20
Hello 

on ubuntu 16 i have DHCP client lease file 
/var/lib/dhcp/dhclient.eth0.leases

on ubuntu 22 this file does not exists, is it in a new path? 
is there other lease file for ubuntu22 ?

---

### Post by TheFu on 2024-08-20
The entire way that networking is configured has changed in servers since 16.04.  Netplan is used now, not the old interfaces file.

I don't use DHCP for servers, but I do see a /var/lib/dhcp/ directory. It is empty.  Perhaps find the new DHCP client startup script (systemd-unit file) and see where it gets the config file from, then look in that config file for the location of the runtime files you seem to want.  Or just use the commonly used tools to pull the data you need rather than looking inside files that are likely to change and never intended to be used.   If I had to guess, I'd expect DHCP lease information to be under /var/run/ somewhere, but I don't know.

Servers using DHCP is asking for trouble, IME over the last 30 yrs.  I've seen entire server networks fail to boot when redundant DHCP servers weren't working correctly. This failure didn't just harm the servers but all the desktops too, about 2000 people were unable to work.  It was a bad day.  Since that time, I've always set static IPs on all my servers.

---

### Post by nonick95 on 2024-08-21
thank you for your answer @thefu 

my use case i an offline eco system made from 7 computers,
 one is the master system and DHCP server, all other are "slaves"

with Ubuntu 16 i could add this line:
> also request Tcode;
to  /etc/dhcp/dhclient.conf on the 6 slaves\clients machines
then read the time zone from  /var/lib/dhcp/dhclient.xxx.leases
and pass the time zone to timedatectl to set the time zone on all 6 slaves.
 if you know a better way to achieve this i will be very happy to know about it



my eyes didn't catch the file name in the script.
the DHCP script is:

/sbin/dhclient-script


> #!/bin/sh

# Explicitly set the PATH to that of ENV_SUPATH in /etc/login.defs and unset
# various other variables. We need to do this so /sbin/dhclient cannot abuse
# the environment to escape AppArmor confinement via this script
# (LP: #1045986). This can be removed once AppArmor supports environment
# filtering (LP: #1045985)
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
export ENV=
export BASH_ENV=
export CDPATH=
export GLOBIGNORE=
export BASH_XTRACEFD=


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


# log an error.
error() { logger -p daemon.err "$@"; }


# wait for given file to be writable
wait_for_rw() {
    local file=$1
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


    # Wait for $file to become writable
    if [ "$rootmode" = "rw" ]; then
        while ! { : >> "$file"; } 2>/dev/null; do
            sleep 0.1
        done
    fi
}


# update /etc/resolv.conf based on received values
make_resolv_conf() {
    local new_resolv_conf


    # DHCPv4
    if [ -n "$new_domain_search" ] || [ -n "$new_domain_name" ] ||
       [ -n "$new_domain_name_servers" ]; then
        resolv_conf=$(readlink -f "/etc/resolv.conf" 2>/dev/null) ||
            resolv_conf="/etc/resolv.conf"


        new_resolv_conf="${resolv_conf}.dhclient-new.$$"
        wait_for_rw "$new_resolv_conf"
        rm -f $new_resolv_conf


        if [ -n "$new_domain_name" ]; then
            echo domain ${new_domain_name%% *} >>$new_resolv_conf
        fi


        if [ -n "$new_domain_search" ]; then
            if [ -n "$new_domain_name" ]; then
                domain_in_search_list=""
                for domain in $new_domain_search; do
                    if [ "$domain" = "${new_domain_name}" ] ||
                       [ "$domain" = "${new_domain_name}." ]; then
                        domain_in_search_list="Yes"
                    fi
                done
                if [ -z "$domain_in_search_list" ]; then
                    new_domain_search="$new_domain_name $new_domain_search"
                fi
            fi
            echo "search ${new_domain_search}" >> $new_resolv_conf
        elif [ -n "$new_domain_name" ]; then
            echo "search ${new_domain_name}" >> $new_resolv_conf
        fi


        if [ -n "$new_domain_name_servers" ]; then
            for nameserver in $new_domain_name_servers; do
                echo nameserver $nameserver >>$new_resolv_conf
            done
        else # keep 'old' nameservers
            sed -n /^\w*[Nn][Aa][Mm][Ee][Ss][Ee][Rr][Vv][Ee][Rr]/p $resolv_conf >>$new_resolv_conf
        fi


 if [ -f $resolv_conf ]; then
     chown --reference=$resolv_conf $new_resolv_conf
     chmod --reference=$resolv_conf $new_resolv_conf
 fi
        mv -f $new_resolv_conf $resolv_conf
    # DHCPv6
    elif [ -n "$new_dhcp6_domain_search" ] || [ -n "$new_dhcp6_name_servers" ]; then
        resolv_conf=$(readlink -f "/etc/resolv.conf" 2>/dev/null) ||
            resolv_conf="/etc/resolv.conf"


        new_resolv_conf="${resolv_conf}.dhclient-new.$$"
        wait_for_rw "$new_resolv_conf"
        rm -f $new_resolv_conf


        if [ -n "$new_dhcp6_domain_search" ]; then
            echo "search ${new_dhcp6_domain_search}" >> $new_resolv_conf
        fi


        if [ -n "$new_dhcp6_name_servers" ]; then
            for nameserver in $new_dhcp6_name_servers; do
                # append %interface to link-local-address nameservers
                if [ "${nameserver##fe80::}" != "$nameserver" ] ||
                   [ "${nameserver##FE80::}" != "$nameserver" ]; then
                    nameserver="${nameserver}%${interface}"
                fi
                echo nameserver $nameserver >>$new_resolv_conf
            done
        else # keep 'old' nameservers
            sed -n /^\w*[Nn][Aa][Mm][Ee][Ss][Ee][Rr][Vv][Ee][Rr]/p $resolv_conf >>$new_resolv_conf
        fi


 if [ -f $resolv_conf ]; then
            chown --reference=$resolv_conf $new_resolv_conf
            chmod --reference=$resolv_conf $new_resolv_conf
 fi
        mv -f $new_resolv_conf $resolv_conf
    fi
}


# set host name
set_hostname() {
    if [ -n "$new_host_name" ]; then
        local current_hostname=$(hostname)


        # current host name is empty, '(none)' or 'localhost' or differs from new one from DHCP
        if [ -z "$current_hostname" ] ||
           [ "$current_hostname" = '(none)' ] ||
           [ "$current_hostname" = 'localhost' ] ||
           [ "$current_hostname" = "$old_host_name" ]; then
           if [ "$new_host_name" != "$current_host_name" ]; then
               hostname "$new_host_name"
           fi
        fi
    fi
}


# set the link up and wait for ipv6 link local dad to finish
ipv6_link_up_and_dad() {
    local dev=$1 delay=${2:-0.1} attempts=${3:-60}
    ip link set up dev "$dev" ||
        { error "$dev: failed to set link up"; return 1; }
    local n=0
    while :; do
        n=$((n+1))
        # note: busybox ip does not understand 'tentative' as input
        # so we cannot just use the tentative flag and check for empty
        out=$(ip -6 -o address show dev "$dev" scope link) || {
            error "$dev: checking for link-local addresses failed";
            return 1
        }
        # another note: the output may be empty if the link local tentative addr
        # isn't up just yet, so we need to make sure there is at least one 'inet6'
        # match before returning success.  We need to keep checking for both
        # 'tentative' case and default (no inet6 address) case. (LP: #1718568)
        # Don't reorder tentative/inet6 - we need to check for tentative first.
        case " $out " in
            *\ dadfailed\ *)
                error "$dev: ipv6 dad failed."
                return 1;;
            *\ tentative\ *) :;;
            *\ inet6\ *) return 0;;
            *) :;;
        esac
        [ $n -lt $attempts ] || {
            error "$dev: time out waiting for permanent link-local address"
            return 1;
        }
        sleep $delay
    done
}


# run given script
run_hook() {
    local script="$1"
    local exit_status=0


    if [ -f $script ]; then
        . $script
        exit_status=$?
    fi


    if [ -n "$exit_status" ] && [ "$exit_status" -ne 0 ]; then
        logger -p daemon.err "$script returned non-zero exit status $exit_status"
    fi


    return $exit_status
}


# run scripts in given directory
run_hookdir() {
    local dir="$1"
    local exit_status=0


    if [ -d "$dir" ]; then
        for script in $(run-parts --list $dir); do
            run_hook $script
            exit_status=$((exit_status|$?))
        done
    fi


    return $exit_status
}


# Must be used on exit.   Invokes the local dhcp client exit hooks, if any.
exit_with_hooks() {
    local exit_status=$1


    # Source the documented exit-hook script, if it exists
    if ! run_hook /etc/dhcp/dhclient-exit-hooks; then
        exit_status=$?
    fi


    # Now run scripts in the Debian-specific directory.
    if ! run_hookdir /etc/dhcp/dhclient-exit-hooks.d; then
        exit_status=$?
    fi


    exit $exit_status
}




# The 576 MTU is only used for X.25 and dialup connections
# where the admin wants low latency.  Such a low MTU can cause
# problems with UDP traffic, among other things.  As such,
# disallow MTUs from 576 and below by default, so that broken
# MTUs are ignored, but higher stuff is allowed (1492, 1500, etc).
if [ -z "$new_interface_mtu" ] || [ "$new_interface_mtu" -le 576 ]; then
    new_interface_mtu=''
fi




# The action starts here


# Invoke the local dhcp client enter hooks, if they exist.
run_hook /etc/dhcp/dhclient-enter-hooks
run_hookdir /etc/dhcp/dhclient-enter-hooks.d


# Execute the operation
case "$reason" in


    ### DHCPv4 Handlers


    MEDIUM|ARPCHECK|ARPSEND)
        # Do nothing
        ;;
    PREINIT)
        # The DHCP client is requesting that an interface be
        # configured as required in order to send packets prior to
        # receiving an actual address. - dhclient-script(8)


        # ensure interface is up
        ip link set dev ${interface} up


        if [ -n "$alias_ip_address" ]; then
            # flush alias IP from interface
            ip -4 addr flush dev ${interface} label ${interface}:0
        fi


        ;;


    BOUND|RENEW|REBIND|REBOOT)
        set_hostname


        if [ -n "$old_ip_address" ] && [ -n "$alias_ip_address" ] &&
           [ "$alias_ip_address" != "$old_ip_address" ]; then
            # alias IP may have changed => flush it
            ip -4 addr flush dev ${interface} label ${interface}:0
        fi


        if [ -n "$old_ip_address" ] &&
           [ "$old_ip_address" != "$new_ip_address" ]; then
            # leased IP has changed => flush it
            ip -4 addr flush dev ${interface} label ${interface}
        fi


        if [ -z "$old_ip_address" ] ||
           [ "$old_ip_address" != "$new_ip_address" ] ||
           [ "$reason" = "BOUND" ] || [ "$reason" = "REBOOT" ]; then
            # new IP has been leased or leased IP changed => set it
            ip -4 addr add ${new_ip_address}${new_subnet_mask:+/$new_subnet_mask} \
                ${new_broadcast_address:+broadcast $new_broadcast_address} \
                ${new_dhcp_lease_time:+valid_lft $new_dhcp_lease_time} \
                ${new_dhcp_lease_time:+preferred_lft $new_dhcp_lease_time} \
                dev ${interface} label ${interface}


            if [ -n "$new_interface_mtu" ]; then
                # set MTU
                ip link set dev ${interface} mtu ${new_interface_mtu}
            fi


     # if we have $new_rfc3442_classless_static_routes then we have to
     # ignore $new_routers entirely
     if [ ! "$new_rfc3442_classless_static_routes" ]; then
      # set if_metric if IF_METRIC is set or there's more than one router
      if_metric="$IF_METRIC"
      if [ "${new_routers%% *}" != "${new_routers}" ]; then
   if_metric=${if_metric:-1}
      fi


      for router in $new_routers; do
   if [ "$new_subnet_mask" = "255.255.255.255" ]; then
       # point-to-point connection => set explicit route
       ip -4 route add ${router} dev $interface >/dev/null 2>&1
   fi


   # set default route
   ip -4 route add default via ${router} dev ${interface} \
       ${if_metric:+metric $if_metric} >/dev/null 2>&1


   if [ -n "$if_metric" ]; then
       if_metric=$((if_metric+1))
   fi
      done
     fi
        else # RENEW||REBIND
            ip -4 addr change ${new_ip_address}${new_subnet_mask:+/$new_subnet_mask} \
                ${new_broadcast_address:+broadcast $new_broadcast_address} \
                ${new_dhcp_lease_time:+valid_lft $new_dhcp_lease_time} \
                ${new_dhcp_lease_time:+preferred_lft $new_dhcp_lease_time} \
                dev ${interface} label ${interface}
        fi


        if [ -n "$alias_ip_address" ] &&
           [ "$new_ip_address" != "$alias_ip_address" ]; then
            # separate alias IP given, which may have changed
            # => flush it, set it & add host route to it
            ip -4 addr flush dev ${interface} label ${interface}:0
            ip -4 addr add ${alias_ip_address}${alias_subnet_mask:+/$alias_subnet_mask} \
                dev ${interface} label ${interface}:0
            ip -4 route add ${alias_ip_address} dev ${interface} >/dev/null 2>&1
        fi


        # update /etc/resolv.conf
        make_resolv_conf


        ;;


    EXPIRE|FAIL|RELEASE|STOP)
        if [ -n "$alias_ip_address" ]; then
            # flush alias IP
            ip -4 addr flush dev ${interface} label ${interface}:0
        fi


        if [ -n "$old_ip_address" ]; then
            # flush leased IP
            ip -4 addr flush dev ${interface} label ${interface}
        fi


        if [ -n "$alias_ip_address" ]; then
            # alias IP given => set it & add host route to it
            ip -4 addr add ${alias_ip_address}${alias_subnet_mask:+/$alias_subnet_mask} \
                dev ${interface} label ${interface}:0
            ip -4 route add ${alias_ip_address} dev ${interface} >/dev/null 2>&1
        fi


        ;;


    TIMEOUT)
        if [ -n "$alias_ip_address" ]; then
            # flush alias IP
            ip -4 addr flush dev ${interface} label ${interface}:0
        fi


        # set IP from recorded lease
        ip -4 addr add ${new_ip_address}${new_subnet_mask:+/$new_subnet_mask} \
            ${new_broadcast_address:+broadcast $new_broadcast_address} \
            ${new_dhcp_lease_time:+valid_lft $new_dhcp_lease_time} \
            ${new_dhcp_lease_time:+preferred_lft $new_dhcp_lease_time} \
            dev ${interface} label ${interface}


        if [ -n "$new_interface_mtu" ]; then
            # set MTU
            ip link set dev ${interface} mtu ${new_interface_mtu}
        fi


        # if there is no router recorded in the lease or the 1st router answers pings
        if [ -z "$new_routers" ] || ping -q -c 1 "${new_routers%% *}"; then
     # if we have $new_rfc3442_classless_static_routes then we have to
     # ignore $new_routers entirely
     if [ ! "$new_rfc3442_classless_static_routes" ]; then
      if [ -n "$alias_ip_address" ] &&
         [ "$new_ip_address" != "$alias_ip_address" ]; then
   # separate alias IP given => set up the alias IP & add host route to it
   ip -4 addr add ${alias_ip_address}${alias_subnet_mask:+/$alias_subnet_mask} \
       dev ${interface} label ${interface}:0
   ip -4 route add ${alias_ip_address} dev ${interface} >/dev/null 2>&1
      fi


      # set if_metric if IF_METRIC is set or there's more than one router
      if_metric="$IF_METRIC"
      if [ "${new_routers%% *}" != "${new_routers}" ]; then
   if_metric=${if_metric:-1}
      fi


      # set default route
      for router in $new_routers; do
   ip -4 route add default via ${router} dev ${interface} \
       ${if_metric:+metric $if_metric} >/dev/null 2>&1


   if [ -n "$if_metric" ]; then
       if_metric=$((if_metric+1))
   fi
      done
     fi


            # update /etc/resolv.conf
            make_resolv_conf
        else
            # flush all IPs from interface
            ip -4 addr flush dev ${interface}
            exit_with_hooks 2
        fi


        ;;


    ### DHCPv6 Handlers
    # TODO handle prefix change: ?based on ${old_ip6_prefix} and ${new_ip6_prefix}?


    PREINIT6)
        # ensure interface is up
        ipv6_link_up_and_dad "$interface"


        # flush any stale global permanent IPs from interface
        ip -6 addr flush dev ${interface} scope global permanent


        ;;


    BOUND6|RENEW6|REBIND6)
        if [ "${new_ip6_address}" ]; then
            # set leased IP
            ip -6 addr add ${new_ip6_address} \
                dev ${interface} scope global
        fi


        # update /etc/resolv.conf
        if [ "${reason}" = BOUND6 ] ||
           [ "${new_dhcp6_name_servers}" != "${old_dhcp6_name_servers}" ] ||
           [ "${new_dhcp6_domain_search}" != "${old_dhcp6_domain_search}" ]; then
            make_resolv_conf
        fi


        ;;


    DEPREF6)
        # set preferred lifetime of leased IP to 0
        ip -6 addr change ${cur_ip6_address} \
            dev ${interface} scope global preferred_lft 0


        ;;


    EXPIRE6|RELEASE6|STOP6)
        if [ -z "${old_ip6_address}" ]; then
            exit_with_hooks 2
        fi


        # delete leased IP
        ip -6 addr del ${old_ip6_address} \
            dev ${interface}


        ;;
esac


exit_with_hooks 0




---

### Post by TheFu on 2024-08-21
I don't use DHCP.

When a system gets installed here, we set the machine to use UTC and the timezone to be whatever is local. 

When setting up new systems, we use Ansible.  I consider 5 systems the point where Ansible starts making more and more sense to use. Setting the timezone with Ansible is trivial:
[https://docs.ansible.com/ansible/latest/collections/community/general/timezone_module.html#examples](https://docs.ansible.com/ansible/latest/collections/community/general/timezone_module.html#examples)
```
- name: Set timezone to Asia/Tokyo
  become: true
  community.general.timezone:
    name: Asia/Tokyo
```
Of course, about 5 lines in a playbook header are needed before calling this task/role.  1 or 2000 systems, doesn't really matter.
Choose your poison.  I'm less inclined to look deep into a file created by the system, that isn't a published interface than to use a tool that runs on-demand and provides the answer.

---

### Post by nonick95 on 2024-08-22
Hi

in my case its system made from 7 COM express cpu's\pc's
the system is offline system 
i need the ability to have some kind of 0 configuration
i move or install new cpu and i need it to know its physical location in the system, get the correct ip for this location, get the same time zone from the main system 
and some more configuration are puled from the main system without any intervention, so ansible not good for my case 

is there anyway to find the lease file or make it generate it on ubuntu 22  ?

---

### Post by TheFu on 2024-08-22
I'm confused.  You have DHCP, so there is a network. I've assumed there is a network between the 7 computers.  Then ansible makes perfect sense.  No internet is needed.  Heck, you can run ansible locally on each machine, but that defeats the usefulness.

I do see a setting in dhcpclient that let's you specify the location of the lease file at startup.  This can be either a command line argument or in the .conf file.  Maybe that will fit your needs?  I'm a little surprised that asking the dhcpclient program for information about the current lease isn't supported.  There is no mention in the manpage of timezone data at all.

In a "See Also", there's mention of asking netplan about leases.
```
$ netplan ip leases [COLOR="#FF0000"]eth0[/COLOR]
```
Of course, you'll need to know the interface name on each device.  Ansible knows that. ;)

---

### Post by nonick95 on 2024-08-25
@thefu

can you please point me to the [COLOR=#000000]specify the location of the lease file at startup.
[/COLOR]

---

### Post by TheFu on 2024-08-25
> **nonick95 said:**
> @thefu

can you please point me to the [COLOR=#000000]specify the location of the lease file at startup.
[/COLOR]

If it isn't in  /var/lib/dhcp/dhcp/ then I don't know.  Again, I don't use DHCP on Servers. I set static IPs on the system. This doesn't help you. Sorry.
When I look in that directory, which does exist, it is empty.  On 20.04 systems, that same directory has a lease file for each interface during the initial install (where DHCP was used) that wasn't cleaned up.  

One of the 20.04 Servers has a single lease file that has 5 entries. I suspect the system was rebooted 5 times before I got around to setting the static IP. It was a new type of system, so an Ansible playbook wasn't read for it.

On my few 22.04 Servers, **locate lease |egrep dhcp** finds nothing. I have locate/updatedb running on all my systems.  Just to be certain, I did a '**sudo find / -iname "*lease*" 2>/dev/null  | egrep -i dhcp**' as well. Nothing found.

Perhaps someone else with 22.04 servers that uses DHCP can aid?

---

