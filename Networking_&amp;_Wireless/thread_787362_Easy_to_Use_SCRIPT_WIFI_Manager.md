---
title: "Easy to Use SCRIPT WIFI Manager"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by taipoh on 2008-05-08
If network manager is getting on your nerves...  DISABLE THE BEAST! Use this script.

Features:
1.  Supports WEP and non-WEP
2.  Only connects when you tell it to (via an easy command)
3.  Can set random hostnames and random mac addresses

To install:
```

1.  open up a terminal
2.  copy and paste the below line:
sudo gedit /root/wifi.sh
3.  copy and paste the code (starting with #!/bin/bash below)
4.  modify the code to include your networks at the top
5.  To use the rand_mac and/or rand_hostname features, scroll down in gedit and uncomment them (IMPORTANT: Also uncomment seed_rand)
6.  Save, and return to the terminal.
7.  Copy and paste the below line:
sudo chmod +x /root/wifi.sh

```
example usage:
sudo /root/wifi.sh another


```

#!/bin/bash

#you need to edit the network list below

#nickname=( essid encryption_type encryption_key )
example=( "My ExAmPlE" wep s:forumnetworking )
another=( "Another wep example" wep 1908AC0988 )
linksys=( linksys off )

#you also need to set this to your device
device=wlan0



############################################################
#            ONLY CODE IS BELOW THIS LINE!!!!!!            #
###########################################################


if [ -z "$1" ]; then
	echo "usage: $0 network_nick_name"
	exit
fi

if [ -z "${!1}" ]; then
	echo "ERROR, no network nick name of $1 is defined"
	exit
fi

seed_rand ()
{
	RANDOM=$(( `date +%s` % 32766 ))
}

rand () #$1 === min, $2 === max
{
	echo $(( $RANDOM % ($2-$1+1) + $1 ))
}

gen_char () #$1 === max
{
	if [ -z "$1" ]; then
		max=35
	else
		max=$1
	fi

	alphas=( 0 1 2 3 4 5 6 7 8 9 A B C D E F G H I J K L M N O P Q R S T U V W X Y Z )
	echo ${alphas[`rand 0 $max`]}
}

setup_1450 ()
{
	rmmod ssb 2>/dev/null
	rmmod ndiswrapper 2>/dev/null
	modprobe ndiswrapper
}

drop_conn ()
{
	ifconfig $device down
	dhclient -r $device
}

rand_hostname ()
{
	length=`rand 5 20`
	hn=''
	for ((i=0;i<length;i+=1)); do
		hn=$hn`gen_char`
	done
	hostname $hn
}

rand_mac ()
{
	if [ -z "$1" ]; then
		mac="00:0D:93"
	else
		mac=$1
	fi

	for ((i=0;i<3;i+=1)); do
		mac=$mac:`gen_char 15``gen_char 15`
	done
	ifconfig $device hw ether $mac
	ifconfig $device up
}

new_conn ()
{
	#nickname=( essid encryption_type encryption_key )
	essid=${1}[0]
	enc_type=${1}[1]

	if [ "${!enc_type}" = wep ]; then
		enc_key=${1}[2]
		iwconfig $device key "${!enc_key}"
		iwconfig $device essid "${!essid}"

	elif [ "${!enc_type}" = off ]; then
		iwconfig $device key off
		iwconfig $device essid "${!essid}"

	else
		echo "Encryption Type ${!enc_type} not yet configured"
	fi

	iwconfig $device key open
	iwconfig $device mode Managed
	dhclient $device
}

#setup_1450
drop_conn
#seed_rand
#rand_hostname
#rand_mac
new_conn $1

echo mac: $mac
echo hostname: `hostname`

```

---

