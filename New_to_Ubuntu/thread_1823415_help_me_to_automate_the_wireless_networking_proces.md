---
title: "help me to automate the wireless networking process........"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by jpjohnj on 2011-08-12
i plan to automate the wireless network configuration process...

so i plan to create an shell script to perform this operation.

purpose of the shell script..

[B]For UBUNTU LAPTOP
[/B]
1.manually configuring wireless settings to connect with the wireless router like encryption algorithm and essid.

2.when we choose the essid of the wireless router, it should automatically  connect to that router.

i need you help for

# program logic to perform this.
#other suggestion like how to do this in a better way.

---

### Post by Carborundum on 2011-08-12
Any particular reason you can't use network manager for this?

---

### Post by jpjohnj on 2011-08-12
i am going to test my wireless router.so i need this..........

---

### Post by jpjohnj on 2011-08-12
Program for automatic selection of SSID....


#!/bin/bash

#removing possible previous temp file
rm list.temp 2>/dev/null

#scans for wifi connections & isolates wifi AP name
# thanks to jonjgc for the array solution
#thanks to ghostdog74 for the AWK suggestion

eval list=( $(sudo iwlist scan 2>/dev/null | awk -F":" '/ESSID/{print $2}') )

#sets prompt
PS3="Choose wifi connection: "

#tests for number of wifi connections, exits if none
if [ -z "${list[0]}" ]; then
	clear
	echo "No available wifi connection"
	exit 1
fi

#menu of wifi connections
select item in "${list[@]}"; do

#sets essid as value for WIFI variable and displays information about the AP
	wifi=$(echo $item)
        sudo iwlist scan 2>/dev/null | sed -n "/$wifi/, +9p" > list.temp
	echo "$(cat list.temp | sed 's/^[ \t]*//')"

#sets channel as value for CHANNEL variable
	channel=$(grep Channel: list.temp | sed 's/.*Channel://g')

#test for mode, if mode = master, sets MODE variable to managed
	mode=$(grep Mode list.temp | sed 's/.*Mode://g')
	if [ "$mode" == "Master" ]; then
		mode="managed"
	else
		clear
		echo "Cannot connect"
		exit
	fi

#tests for encryption key
	key=$(grep key: list.temp | sed 's/.*key://g')
	if [ $key == "on" ]; then
		echo -n "Enter encryption key: "
		read key
	fi

#checks encryption algorithm
	IE=$(grep IE list.temp | sed 's/^ .*IE: \(...\).*/\1/')

#writes to /etc/network/interfaces file for WPA encryption: essid, key, protocols, etc.
	if [ "$IE" == "WPA" ]; then
		sudo cp /etc/network/interfaces /etc/network/interfaces.bakup
		sudo sed -i 's/iface wlan0 inet manual/iface wlan0 inet dhcp/' /etc/network/interfaces
		sudo sed -i -e "/dhcp/a\wpa-passphrase $key" \
	-e "/dhcp/a\wpa-driver wext" \
	-e "/dhcp/a\wpa-key-mgmt WPA-PSK" \
	-e "/dhcp/a\wpa-proto WPA" \
	-e "/dhcp/a\wpa-ssid \"$wifi\"" /etc/network/interfaces
	sudo /etc/init.d/networking restart
	sudo cp /etc/network/interfaces.bakup /etc/network/interfaces
	sudo rm /etc/network/interfaces.bakup
	exit

	else

#sets the wireless configuration for non WPA: essid, channel, mode, key, etc
		sudo iwconfig wlan0 essid \""$wifi"\" channel $channel mode $mode key $key
		echo "------------------------------------------------"
		echo "Connecting to: $wifi at channel: $channel, mode: $mode"
		echo "------------------------------------------------"

#connects to wifi connection
		sudo dhclient
		exit
	fi
done



[COLOR="DarkRed"]I got this error bellow::::::::::::::
[/COLOR]









[FONT="Courier New"][I]ESSID:"CR_SHYDB"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001508376d80
Extra: Last beacon: 224ms ago
IE: Unknown: 000843525F5348594442
IE: Unknown: 010882848B968C129824
IE: Unknown: 030102
./1.sh: line 45: [: ==: unary operator expected
Error for wireless request "Set Frequency" (8B04) :
    invalid argument "mode".
------------------------------------------------
Connecting to: CR_SHYDB at channel: , mode: managed
[/I][/FONT]

---

