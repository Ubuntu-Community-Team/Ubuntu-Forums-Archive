---
title: "dhclient-script"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by michaelm66 on 2006-10-17
having never seen or heard linux before, i have installed ubuntu on a spare pc today and to my surprise it is still working. i had problems connecting to the internet until i read a reply from python regarding d link dsl 504t router. i managed to find out the isp's dns nameservers and i put them in the networking (dns tab). the entries are also in the /etc/resolv.conf (i have no idea how i managed to find it). i also managed to find /etc/dhcp3/dhclient-script but since i'm a complete linux virgin, i don't know how to comment out lines in the script. also, my script looks quite different than the one python quoted ([http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d+link+dsl+504t+adsl+router](http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d+link+dsl+504t+adsl+router))
my script looks like this:
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
    shift	# discard the first argument, then the rest are the script's

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
    shift	# See run_hook

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
    metric_arg="metric $IF_METRIC"	# interfaces(5), "metric" option
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

can someone please, please, please tell me what and how to do! i would love to make this work. i've just begun finding about linux, but i have a feeling it will be a long friendship...

---

### Post by louieb on 2006-10-17
Is the PC hooked to the router with wire or wireless?
Do you have other computers connected to the internet thru the router? Wire or wireless?
I have 3 computers running Linux and connected to the router vis wire.  and have tried more than a dozen distros on them. Every time I have done an install the network card was detected and I had internet access with doing anything special. 
The reason I ask about wireless is I have my home wireless access configured to allow only certain MAC addresses to connect (a mac address identifies the wireless card in a PC each card has its own unique address). 
I can't imagine you would have to edit the dhcliet-script so I trying to figure what is diffrent about your setup.

---

### Post by handy on 2006-10-17
I take it that you are using the current Dapper not the previous Breezy version of Ubuntu?

**Python's** wonderful solution does not work in Dapper unfortunately.

I do know what does, after a great deal of trying & inventing workarounds, someone called **Mips**, finaly pointed me to the solution. :KS 

So if your propblem is that your ISP's DNS addresses keep being lost after a reboot (sometimes it takes more than one reboot, sometimes it happens without a reboot!!)

The following solution, hidden between the dashes, is courtesy of **Stream303** I've just made it easier for new users.
----------------
I don't like editing dhclient-script directly, so *this way* is to prepend the resolv.conf file with your known good isp nameservers.

_**To Edit** **/etc/dhcp3/dhclient.conf**_

Enter the following line in the **Terminal:** (If you are unfamiliar with using the **Terminal** have a look down this page @ **Post 6.** for a few simple tips.) 

**sudo gedit /etc/dhcp3/dhclient.conf**

and just before the **request** line in your **dhclient.conf** file that you are looking at in **gedit**, add the following line:

**prepend domain-name-servers 123.45.678.90, 123.45.678.91;**

(Swapping your isp's DNS addresses for the ones in the above line of course).

For multiple addresses, separate with a comma and don't forget the semicolon at the end.

This will have the effect of prepending **your isp nameservers** and of having your routers dns address automaticaly come up at the bottom of the list in **resolv.conf**:

Reboot or just bring your interface down and up again by entering the following in the Terminal:

**sudo ifdown eth0**

**sudo ifup eth0**

------------------

After doing the above, the repositories are allways available as well as other forms of download & communication.

Also, if you find that you can't access the web through Firefox, do the following:

Enter **about:config** in the address field.

Enter **ipv6** in the new **Filter:** field.

Double click on the line left in the display window to change it's boolean value to **true**.

Restart Firefox.

& that should be that... 

All the best & wellcome... :D

**[Edit:]** [I]The reason for the first problem which strikes lots of modem/routers is due to their windoze centric design.

The reason for the 2nd problem is due to the cheap quality of the router, which is also responsible for the first problem...[/I]

---

### Post by michaelm66 on 2006-10-18
the router is d link g604t and the pc is connected to it with the cable. when i input the dns nameserver in the networking screen and restart firefox, the internet is working. it works for about 20 minutes, then the dns nameserver goes back to 192.168.1.1 (the d link box) and internet stops. so whenever i lose connection i have to change these server entries... it's all quite dynamic, really...

---

### Post by michaelm66 on 2006-10-18
i, handy, thank you for a very detailed reply. i'll try it tonight. i think i am using the dapper version, i downloaded ubuntu a few weeks ago. since the whole concept is completely new to me, i have no idea how to access script editing, i need to get to know the conventions and  the ways of doing things... it is all a little frustrating but also quite fascinating...

---

### Post by handy on 2006-10-18
> **michaelm66 said:**
> i, handy, thank you for a very detailed reply. i'll try it tonight. i think i am using the dapper version, i downloaded ubuntu a few weeks ago. since the whole concept is completely new to me, i have no idea how to access script editing, i need to get to know the conventions and  the ways of doing things... it is all a little frustrating but also quite fascinating...

You will get used to it surprisingly quickly :) 

Most often you can just **Copy** the commands directly from the forum (or anywhere else) & **Paste** it into the **Terminal** or any other field that accepts text.  It won't take too long to get used to doing that, & it saves typing & typo's too.

If you highlight text by left mouse button dragging over the desired text you can use keyboard combo's to manipulate it.

**The most used 2 finger Key Combo's follow:**

**Copy** = < **ctrl** > + < **c** >

**Paste** = < **ctrl** > + < **v** >

**Move** = < **ctrl** > + < **x** > Followed by the **Paste** combo'.

*When manipulating text with Key Combo's, in the **Terminal**, (which is extremely useful) you are required to use the same combinations as above, with the addition of the < **shift** > key, making them 3 finger combo's.*

The Terminal is your friend...

You will find both the **Terminal** & **Text Editor** in the ***Menu:* Applications / Accessories**

The Text Editor (**gedit** is it's name if you call it from the **Terminal**) is both simple & powerful.

Searching for answers in the forums is harder when you are new to Ubuntu, & the contents is perpetualy growing, which makes it harder to find what you want to know as well. So don't be afraid to ask about anything you don't know, it is only these forums & the willingness of people to help other people that has made it possible for many new linux users to enthusiasticaly adopt Ubuntu as their operating system of choice. These users, often in turn help others where they can, & on it goes... :KS

**I have edited [B]*_Post 3_*** in this thread to make it a little clearer to go step by step with.  I hope it helps?[/B]

---

### Post by Iowan on 2006-10-18
Whilst you're editing the **dhclient.conf** file, you might delete the  **domain-name-servers** from the **request** line.

Many of **handy's** suggestions appear in [THIS ]("http://www.ubuntuforums.org/showthread.php?t=177441") thread (or the thread referenced by this thread).

---

### Post by handy on 2006-10-19
**Post removed, because I was way off the track!**

---

### Post by louieb on 2006-10-19
Found this in the Gentoo installation handbook it might help.

DHCP (Dynamic Host Configuration Protocol) makes it possible to automatically receive networking information (IP address, netmask, broadcast address, gateway, nameservers etc.). This only works if you have a DHCP server in your network (or if your provider provides a DHCP service). To have a network interface receive this information automatically, use dhcpcd.

```
# dhcpcd eth0
Some network admins require that you use the
hostname and domainname provided by the DHCP server.
In that case, use
# dhcpcd -HD eth0 
```

---

### Post by Iowan on 2006-10-19
Removing **domain-name-servers** from the **requests** line may only be housekeeping... if you're not gonna use the information, why even risk overwriting (adding superfluous) data?

---

### Post by handy on 2006-10-19
> **Iowan said:**
> I certainly hope it was misinterpretation - no egotism (on my part) was intended!  In fact, I was intending to point out your efforts in a previous (somewhat more detailed?) post.  I thought the information it contained was also good - not realizing you'd rewritten it intentionally. My post was certainly **NOT** intended to have the effect it seems to have had. Keep up the ***great*** work!
Removing **domain-name-servers** from the **requests** line may only be housekeeping... if you're not gonna use the information, why even risk overwriting (adding superfluous) data?

***Sorry Iowan!** (I was a bit fragile, & I surely can be wordy...*)

Thanks for your posts. I think that between us we have been giving the best that we have to give, as far as helping is concerned...

& that's really all there is to it! :KS

---

### Post by michaelm66 on 2006-10-19
hello again, handy! i performed the procedure exactly word for word as you prescribed and it worked! i will be grateful to you forever! now, whenever firefox connects to the internet, i feel like opening a bottle of something... however, the broadband provider (plusnet) has decided to become exactly the opposite of what it has been so far - the connection has been dead during the day, and it comes on around 9pm, then goes again mid morning... the fun never stops... 
i have been testing ubuntu applications and the system itself (in comparison to my win2k). i found the open office quite disappointing, especially the database. it doesn't seem to be nowhere near as flexible as ms access, which i use daily at work. i also find the way to do things, like installing/configuring and that terminal business, can get a little to detailed. maybe i'm used to the lightness (friendliness) of ms windows, i don't know. i intend to try kubuntu, just to see how that feels, and also suse linux. my desire to leave microsoft will take me to one of those directions. also, i apologise for pasting that whole script in the thread, that looked really bad...

---

### Post by handy on 2006-10-20
I'm glad it worked for you, & thanks for your feedback.

It is possible to run M$ Office under Wine, & probably a more friendly way is with [Crossover Office]("http://www.codeweavers.com/"), whether you can run the version you need or not is another potential problem...

Linux is not as easy to do many things in as windoze, but you learn it's ways in time.  The forum's provide sollutions to the vast majority of problems,  just that sometimes we have to wait for the solution.

All the best, I hope you find what you need to escape the clutches of M$ as soon as possible... :KS

---

### Post by michaelm66 on 2006-10-21
well, the fun still hasn't stopped for me. i tried to install xgl and compiz following instructions from a help website and i managed to brake ubuntu. obviously, i didn't know how to fix it so i installed kubuntu and played with it for a few hours. i liked the kde desktop a little more than the gnome, the open office was still a sore point for me. following my curiosity and greed, i obtained the pc linux os "big daddy", installed it and i'm still using it with a big smile. it is just fantastic... i think this is the one. it will be permanently installed on the pc downstairs. there is one thing that i must see in action - the cube (cubic) desktop in ubuntu, so i'll try to play with it on the other pc. i believe that microsoft is on the way out for me already... it's a shame i can't use linux at work... 
thanks for the crossover office tip. once i establish linux at home, i'll investigate the expansion into that area.

---

### Post by handy on 2006-10-21
@**Michaelm66**: It would seem that installing **Compiz/XGL** is a really easy way to break Ubuntu. The technology is too new to be stable, the word is that Edgy will incorporate those 2 bad boys, & will use beta nVidia drivers (?) & a later version of X than Dapper. So it would seem that reliability is on it's way for the Ubuntu 3D desktop. :)

I had a look at **Compiz/XGL**, in so doing made my normally very well behaved machine a horror!  Fortunately I was able to remove the offenders & regain the stability I need... :D 

I'm not very familiar with the Edgy situation, but I'm currently downloading a torrent of the current release, so I'll surely know a whole lot more over the next couple of days. :-k  

As far as reliability & ease of installation, the hardware that you use plays such a big role with Linux.

Happy to hear that you found a Linux distro' to love... :KS

---

### Post by michaelm66 on 2006-10-29
i am back again with new results, and this time it's huge. i installed SLED10 from the LINUX format magazine DVD on my own PC for a test run. it is big, it is wonderful, it's precise, and it almost feels like WIN2K, which has been  my original baby. i changed my video card yesterday as well, and ever since i've been flipping cubes on the screen. the desktop effects are amazing. i am very impressed by the system's thoroughness  and attention to detail (maybe slightly too much). i also installed the PC Linux OS (big daddy) in the office and i'll be using it on a daily basis. the big daddy will go on my laptop as well. one things still doesn't work for me terribly well, the open office database. but i'm willing to live with it for the sake of other goodies. i feel that ubuntu is not straight forward enough for me, and the excellent functionality of kde desktop, especially konqueror, is what i'm looking for from a system. i would definitely recommend trying out SLED 10. i guess VISTA feels as important to me as Britney Spear's new single...

---

