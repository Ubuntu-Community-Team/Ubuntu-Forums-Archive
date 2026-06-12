---
title: "wpa_supplicant reconnect script"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by MaartenNL on 2007-04-19
Hi,

I noticed wpa_supplicant loses a connection too easily and doesn't reconnect very quickly. It's better to kill wpa_supplicant and start it again. To do this automatically, I wrote a script which i thought could be useful to others here too.

I just run this in a seperate terminal and it keeps the connection alive for me.
```

#!/bin/bash
# Reconnect script. Be sure to have mutt installed, or comment that line out.
iface=ath0
driver=wext
wpaconfig=/etc/wpa_supplicant.conf
lockfile=/var/run/connstatus.pid
output=/var/log/connstatus.log
iplog=/var/log/last_ip
email=YOUR_EMAIL_ADDRESS_HERE

check_newip () {
    newip=`/sbin/ifconfig|/bin/grep "Bcast"`
    oldip=`cat $iplog`
    if [ "$newip" != "$oldip" ]; then
        echo $newip|mutt -s 'address changed' $email
        echo Address changed, time: `date` >> $output
        echo "$newip" >> $output
        if [ "`wpa_cli status|grep wpa_state`" == "wpa_state=COMPLETED" ]; then
            echo "$newip" > $iplog
        fi
    fi
}

reconnect () {
        echo Reconnecting, time: `date` >> $output 
        while [ "`wpa_cli status|grep wpa_state`" != "wpa_state=COMPLETED" ]; do
            killall wpa_supplicant; sleep 1
            wpa_supplicant -D$driver -i$iface  -c$wpaconfig &
            for i in `seq 1 10`;do
                sleep 1
                if [ "`wpa_cli status|grep wpa_state`" == "wpa_state=COMPLETED" ]; then
                        break
                fi
            done
        done
        dhclient $iface
}

if ( set -o noclobber; echo "$$" > "$lockfile") 2> /dev/null; then
   	trap 'rm -f "$lockfile"; exit $?' INT TERM EXIT
        while [ 1 ]; do
        	if [ "`wpa_cli status|grep wpa_state`" == "wpa_state=COMPLETED" ]; then
			echo -n "."
			check_newip
        	else
			reconnect
        	fi
		sleep 5
	done
   	rm -f "$lockfile"
   	trap - INT TERM EXIT
else
   	echo "Lockfile $lockfile is held by $(cat $lockfile)." 
fi 


```

---

