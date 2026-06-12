---
title: "How To WLAN autodetect"
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by super-user on 2005-11-17
Hi there,

I just came to know that there is the NetworkManager. But as I've read it does not support WPA. Now, I have a WPA encrypted WLAN at home to which I connect via wpa_supplicant. At university there is a WEP "encrypted" WLAN to which I also want to connect. I more or less had to do all this by hand but now I have written myself a little script that takes advantage of the mapping posibility in the interfaces configuration.

To do this you have to edit '/etc/network/interfaces'. At first you create virtual interfaces for each wlan you want to access. For me this meant:

```

iface wlan0-home inet dhcp
	pre-up	/usr/sbin/wpa_supplicant -Bw -D ndiswrapper -i wlan0 -c /etc/wireless/wpa_home.conf
	post-down killall -q wpa_supplicant

iface wlan0-uni inet dhcp
	pre-up /etc/init.d/wpasupplicant stop
	post-down /etc/init.d/wpasupplicant start
	wireless-essid Wireless Campus Network HUB
	wireless-key XXXXXXXXXX

```

The first entry is an entry from the examples for wpa_supplicant. Nothing special about this. The second entry is for my university wlan. Since it is standard WEP I stop the wpasupplicant service (since it is started during boot) and restart it once the interface is ifdown'ed.

The trick now is the 'mapping' section. First, see this:

```

mapping wlan0
	script /usr/local/sbin/map-scheme
	map wlan0-home essid SSID of my home WLAN
	map wlan0-uni address 00:11:22:33:44:55

```

When you now call 'ifup wlan0' the following happens: the script 'map-scheme' is called and gets 'wlan0' as command line argument. The content behind the 'map' statements are being passed to the script via <STDIN>. The script first checks if the interface to come up is wlan0. A 'iwlist wlan0 scan' is run and saved into a temporary file to see which networks are reachable. Then it checks the 'command' which can be 'essid' or 'address'. If it is 'essid' the script checks if the ssid is in the reachable networks. If so, the virtual interface (here wlan0-home) is being returned to the ifup script.

If you want to connect to a WLAN that does not transmit its ssid, you can still use the MAC address of the access point as identification. This is done with the 'address' command. Again the script checks if a router with the given MAC address is reachable and if so, it returnes the virtual interface (here wlan0-uni) to the ifup script. Since my university wlan0 has several access points, you can state  several MAC addresses as a space separated list. Here is the 'usage':

```

mappping wlan0
          script /path/to/map-scheme
          map <virtual interface> <cmd> <options>
# examples
          map wlan0 essid ssid without quotes
          map wlan0 address 00:11:22:33:44:55 66:77:88:99:AA:BB CC:DD:EE:FF:00:11

```

Now I only have to call 'ifup wlan0' and the rest is done automatically. For the ethernet interface I copied the ping-places.sh example from '/usr/share/doc/ifupdown/examples'. Since the eth0 interface is quite static I have also added the 'netscheme' example posted on a debian list. See the [posting]("http://lists.debian.org/debian-powerpc/2001/08/msg00505.html").

Now here finally comes my '/usr/local/sbin/map-scheme' script:

```

#! /bin/bash
# script under GPL!
# written by Daniel Truemper <daniel dot truemper at gmx dot de>
#
# example for /etc/network/interfaces:
# mapping wlan0
# 	script /usr/local/sbin/mapping-scheme
#	map <virtual interface> <cmd:essid or address> <options>
#	map wlan0-uni essid Uni network
#	map wlan0-uni address 66:77:88:99:AA:BB CC:DD:FF:00:11:22
#	map wlan0-home essid Home Network
#	map wlan0-home address 00:11:22:33:44:55
#
# mapping eth0
#	script /usr/local/sbin/mapping-scheme
#	map ping <ip address to use for the ping> <ip of the machine to ping> <virtual interface if machine found>
#	map ping 192.168.222.254/24 192.168.222.1 eth0-home
#	map ping 192.168.1.254/24 192.168.1.1 eth0-uni
#

# configuration:
# name of the physical wireless interface:
wlan="wlan0"
# name of the physical ethernet interface:
eth0="eth0"

# interface to start comes as command line argument
iface="$1"

# if $1 is null, assume eth0 to come up
# this part is from /usr/share/doc/ifupdown/examples/ping-places.sh
if [ "$iface" = "" ]; then
	iface="$eth"
fi

# if we want the wireless interface to come up:
if [ "$iface" = "$wlan" ]; then

	# preparation for a daemon that will periodically scan networks
	# i.e. the file then has not to be generated here!
	[ -f /var/tmp/wlan-networks ] || `iwlist "$wlan" scan > /var/tmp/wlan-networks`

	while read mapping cmd option; do
		# if the command in the map statement is essid, then check,
		# if the ssid is one of the currently available networks
		if [ "$cmd" = "essid" ]; then
			# change the $IFS var to change the splitting character for array creation
			oldIFS=$IFS
			IFS='?'
			ssids=( $(cat /var/tmp/wlan-networks | perl -ne '/ESSID:\"(.*)\"/i && print $1."?"' ) )
			IFS="$oldIFS"

			# each found ssid shall be checked
			for element in $(seq 0 $((${#ssids[@]} - 1)))
			do 
				if [ "${ssids[$element]}" = "$option" ]; then echo "$mapping"; rm /var/tmp/wlan-networks ;exit 0; fi
			done
		fi
		# if the command in the map statement is address then check
		# if the MAC address is one of the currently available access points
		if [ "$cmd" = "address" ]; then

			# we want to allow a space separated list of MAC addresses:
			macs=( $option )

			# change the $IFS var to change the splitting character for array creation
			oldIFS=$IFS
			IFS='?'
			ssids=( $(cat /var/tmp/wlan-networks | perl -ne '/Address:\s(.*)/i && print $1."?"' ) )
			IFS="$oldIFS"
			
			# each found MAC address shall be checked
			for element in $(seq 0 $((${#ssids[@]} - 1)))
			do
				for el in $(seq 0 $((${#macs[@]} - 1 )))
				do
					if [ "${ssids[$element]}" = "${macs[$el]}" ]; then echo "$mapping"; rm /var/tmp/wlan-networks; exit 0; fi
				done
			done
		fi
	done

elif [ "$iface" = "eth0" ]; then
	which=""
	
	if [ -x /usr/bin/fping ]; then
		PING="/usr/bin/fping"
	else
		PING="/bin/ping -c 2"
	fi
	# the fping is a little bit slower. If you want to speed this up,
	# remove the comment of the following line
	#PING="/bin/ping -c2"

	while read cmd addr pingme scheme; do
		if [ "$cmd" = "ping" ]; then
			if [ "$which" ]; then continue; fi

			# temporarily set up the interface with the address and up it
			ip addr add $addr dev $iface  >/dev/null 2>&1
			ip link set $iface up         >/dev/null 2>&1

			# try to ping the host
			if $PING $pingme >/dev/null 2>&1; then
				which="$scheme"	
			fi
			ip link set $iface down       >/dev/null 2>&1
			ip addr del $addr dev $iface  >/dev/null 2>&1
			# if the host was found, use the scheme of the 'map' line
			if [ "$which" ]; then echo $which; exit 0; fi
		elif [ "$cmd" = "scheme" ]; then
			# do not use the ping but the file /etc/network/scheme
			# simply append the scheme with '-' to the interface
			[ -f /etc/network/scheme ] || exit 1
			scheme=$(cat /etc/network/scheme)
			if [ "$scheme" ]; then echo $iface-$scheme; exit 0; fi
		fi
	done
fi

exit 1

```

And the 'netscheme' script from the debian posting. Use it like 'netscheme home' and make sure that you have an "eth0-home" virtual interface!

```

#!/bin/bash
if [ $# -le 0 ]; then
	echo -n "Current scheme: "
	cat /etc/network/scheme
	exit 0
fi
echo "$1" > /etc/network/scheme

```

Would like to here some comments, if anyone is interested...

Daniel

---

### Post by manicka on 2005-11-18
I have added this how-to, to the 

Ubuntu Document Storage Facility

---

### Post by zombie.daemon on 2006-01-08
hi, thanks for the script, it seems to be exactly what i'm looking for
my only problem, is when i when ifup i get 
"Ignoring unknown interface ath0=ath0."

Here is my network/interfaces:

auto lo ath0 eth0
#allow-hotplug ath0

iface lo inet loopback

mapping hotplug
	map eth0
	map ath0

mapping ath0
	script /usr/local/sbin/map-scheme
	map ath0-home address mac address
	map ath0-work essid ESSID

iface ath0-home inet dhcp
	post-up echo "HOME SETUP"

iface ath0-work inet dhcp
	post-up echo "WORK SETUP"

iface eth0 inet dhcp

any ideas?

---

### Post by super-user on 2006-01-08
[QUOTE=zombie.daemon]
"Ignoring unknown interface ath0=ath0."
[/QUOTE]
This error appears when the script returns not a valid logical interface. I.e. the script cannot determine the right interface to use.

[QUOTE=zombie.daemon]
mapping ath0
	script /usr/local/sbin/map-scheme
	map ath0-home address mac address
	map ath0-work essid ESSID
[/QUOTE]
Is this the EXACT part of your network/interfaces file? If so you have to change the "mac address" and "ESSID" part into something real. It was just an example. I assume that your ath0 is your wlan interface, i.e. you would only use the ssid part. E.g. your home wlan is "HOME WLAN" and your work wlan is "WORK WLAN". The interfaces file should then look like:

```

mapping ath0
	script /usr/local/sbin/map-scheme
	map ath0-home essid HOME WLAN
	map ath0-work essid WORK WLAN

```

hth
daniel

---

### Post by zombie.daemon on 2006-01-08
yes they were just placeholders

mapping ath0
script /usr/local/sbin/map-scheme
map ath0-home address XX:XX:XX:XX:XX:XX (mac address of home router)
map ath0-work essid WHATEVER (SSID of work router)

---

### Post by super-user on 2006-01-09
1st: Did you change the configuration in the map-scheme script? You have to set the variables:
```

# configuration:
# name of the physical wireless interface:
wlan="wlan0"
# name of the physical ethernet interface:
eth0="eth0"

```
at the beginning of the script. For you: >>wlan="ath0"<<

2nd: do you have the wireless tools installed? Try to scan for yourself: "iwlist ath0 scan". What restults are coming?

-daniel

---

### Post by zombie.daemon on 2006-01-09
yes, i changed wlan0 to ath0.
iwlist ath0 scan prints out a list of APs
thanks
zombie

---

### Post by super-user on 2006-01-09
Hm, strange.

I assume that you have perl installed so this cannot be the error source. If you take a look at the script, you see that I use regexp to get the info from the iwlist output. In line 50 you see something like:
```

ssids=( $(cat /var/tmp/wlan-networks | perl -ne '/ESSID:\"(.*)\"/i && print $1."?"' ) )

```
Maybe your scanning output has a different naming for my ESSID part?! The same in line 69 for the Address part?

-daniel

---

### Post by zombie.daemon on 2006-01-09
no, it pulls that just fine, i think it has something to do with the mapping in network/interface and it not liking ath0
zombie

---

### Post by super-user on 2006-01-09
Could you remove ath0 from the hotplug mapping section? This is the only difference left to my setup...

---

### Post by zombie.daemon on 2006-01-09
yeah, i already tried that.
i'm currently re-installing right now (tried to modify some rc1 code, know i didn't need to, but that's half the fun with linux).
i think i'm going to take your script and use it as a template (if that's cool) and try to write my own script.
thanks for your help
zombie

---

### Post by super-user on 2006-01-09
> 
i think i'm going to take your script and use it as a template (if that's cool) and try to write my own script.

Yeah, defenetly! Maybe you could post it here as well so we have different versions and eventually create a *really* good one :-)

-daniel

---

### Post by ktran99 on 2006-01-14
I don't know BASH so I am wondering if your syntax is correct. There is a couple of 'elif' in your script, shouldn't they be 'elsif'.

---

### Post by super-user on 2006-01-14
[QUOTE=ktran99]I don't know BASH so I am wondering if your syntax is correct. There is a couple of 'elif' in your script, shouldn't they be 'elsif'.[/QUOTE]
No, this defenetly works on my laptop and the Advanced Bash Scripting guide has the same notation

-Daniel

---

