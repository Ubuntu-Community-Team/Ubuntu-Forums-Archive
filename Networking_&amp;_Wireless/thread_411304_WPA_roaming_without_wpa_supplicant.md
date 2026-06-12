---
title: "WPA roaming without wpa_supplicant"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by arizal on 2007-04-16
Hi there. Last few days I was looking for a way to setup my wifi roaming without the wpa_supplicant and I found that I cant find nothing :)

My motivation:
So, you will ask why I wont use the supplicant if it works.
I used the wpa_supplcant in the past and it works great. Despite that, it is my opinion that this is something that should be done by the driver/hardware and not in userspace.
Since it was obvious that the ra0 driver supports WPA encryption I was not willing to pass this job to some userspace daemon.

After no luck with finding suitable solution I wrote my own ...
It is not something special but since there is no such article on the web ( as far as I know) I decided to share my expirience.

What we use here is the standard debian interface mapping in /etc/network/interfaces :
```


mapping ra0
        script /usr/local/bin/wifi.roam
        map ra0-home 00:18:39:CF:41:BB
        map ra0-work 00:00:00:00:00:00

```

We use two logical interfaces ra0-home and ra0-work
The first argument to the map line is the logical interface name, the second
is the mac address of the corresponding Access Point. I'm using the mac as a key to decide which interface to choose because it should be unique but it can be anything else that iwlist reports ( ESSID for example ).

The config for the logical interfaces follows:

```


iface ra0-work inet dhcp 
    pre-up iwconfig ra0 essid Bastunia
    pre-up iwconfig ra0 mode managed
    pre-up iwpriv ra0 set Channel=6
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set WPAPSK="somesecret"
    pre-up iwpriv ra0 set TxRate=0

iface ra0-home inet dhcp
    pre-up iwconfig ra0 essid Jupiter
    pre-up iwconfig ra0 mode managed
    pre-up iwpriv ra0 set Channel=9
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set WPAPSK="anothersecret"
    pre-up iwpriv ra0 set TxRate=0

```

Finlay you will need the  /usr/local/bin/wifi.roam bash script which decides which logical iterface to bring up.
Basically the script lists the available Access Points using the iwlist command, then searches one of the known MAC addresses listed in the mapping and if one is found returns the name of the logical interface to bring up.

The script:

```


#!/bin/bash

if=$1

ifconfig $if down
sleep 1
ifconfig $if up
sleep 1
logger -t wifi -p info if $if
while read in ; do
        name=`echo $in | awk '{ print $1; }'`
        mac=`echo $in | awk '{ print $2}'`
        logger -t wifi -p info if $in
        for macs in `iwlist ra0 scanning| grep Address: | awk '{ print $5 }'`; do
                if [ "$macs" == "$mac" ]; then 
                                logger -t wifi -p info if Match $mac
                                echo $name
                                exit 0
                fi
        done
        exit 1
done

```

The ifconfig down/up lines are there because I found that iwlist will not always list all the Access Points without down/up of the interface.

P.S. The script is not well tested so it may have flaws ( actually I wrote it 15 minutes ago and tested it only @home..).

Best Regards

---

### Post by arizal on 2007-04-17
the exit 1 should be after the second 'done'... also there may be needed several retries...
After I finish the tests I will publish the final script ;)

---

