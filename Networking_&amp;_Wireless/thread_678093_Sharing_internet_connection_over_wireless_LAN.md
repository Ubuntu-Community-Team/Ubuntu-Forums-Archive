---
title: "Sharing internet connection over wireless LAN"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by cheatr on 2008-01-25
I see there are posts on this topic, but none are really answered. Ok, so what i want to know, is how to i share my internet connection, my WAN and internet connection both work, and not at the same time. What do i need to configure to achieve internet connection sharing?(please note this is in ad-hoc mode as i don't have a router)

---

### Post by subzero316 on 2008-01-25
All four of these parameters Mode, Channel, ESSID and Network need to be agreed on between the two pc for it to function correctly.


In /etc/network/interfaces, include the following :
# for devices managed by hotplug. This assumes you have
# NET_AGENT_POLICY=hotplug
# in /etc/default/hotplug, which is the default.
mapping hotplug
  script echo

# [B][U]replace eth2 with whatever interface your wireless card gets called
# and obviously replace 'MY_SSID' appropriately for your wireless network[/U][/B]
iface eth2 inet dhcp
    pre-up iwconfig eth2 essid ''MY_SSID''
# if you are using WEP and need to specify an appropriate 13 char key,
# comment out the above line and uncomment the following line:
#    pre-up iwconfig eth2 essid ''MY_SSID' key s:abcdefghijklm


i hope u know 2 assing ip, eg,
Network: 10.10.10.0/24, this computer will be 10.10.10.1, Remote Computer will be 10.10.10.254 


type these cmds replace eth2 with ur wlanname usuallly **_wlan0_**

iwconfig eth2 mode Ad-Hoc
iwconfig eth2 essid "wlug-test"
iwconfig eth2 channel 6


If you did everything correctly you should now be able to get output similar to below, the important settings are ESSID, Mode and Frequency.
root@scorpian: iwconfig eth2
eth2      IEEE 802.11-DS  ESSID:"wlug-test"  Nickname:"test"
          Mode:Ad-Hoc  Frequency:2.437GHz  Cell: 00:02:2D:39:A9:31
          Bit Rate=11Mb/s   Tx-Power=15 dBm   Sensitivity:1/0
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:36/0  Signal level:-61 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:6514
          Tx excessive retries:6  Invalid misc:0   Missed beacon:0

---

### Post by subzero316 on 2008-01-26
hey,


try this it might be a esaier way though am not sure if it works......
**_Install Firestarter_** jus search in your synaptics u ll find it ..instll it 
then go to system->adminstration ull find it there set it up
ull find an option of shaing internet connection enble it..

---

### Post by cheatr on 2008-01-26
Thanks guys for your input. I will try both, think i'll start with firestarter cause i'm not really to keen on working alot. But in the long version, do i really have to assign an ip? between the two windoze installations i have on the two computers my ad-hoc network does that automatically.

Edit: Ok, so i've tried both, and i'm having trouble with them, i think my problem is with my wireless USB, as it has only one light on, dunno if it's a bad sign. Anyway when i try the terminal commands i get:
```
 Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
```

And in firestarter it says: "wlan0 is not ready"

---

### Post by subzero316 on 2008-01-27
are you able to connect to the internet from that.?:confused:
type iwconfig in teminal it will tell your essid:KS
also check if you did it after su(sudo).:KS
also try changing the channel to 2 from 6 or whatever is set.cause a friend of mine usb wifi worked like charm after changing the channel:):)

---

### Post by aslamrahman on 2008-01-27
Beginner :

Can you give me step by step to make wireless internet sharing.

i want sharing internet from ubuntu to win xp.. :confused:

like :

how to configure** /etc/network/interfaces**

---

### Post by cudjoe on 2008-01-31
Hi,

I made a small script, you can use it only if your configuration is like that :

```


    ,--'''''--.       +----------+              +---------+
  |' Internet  '|-----| Modem    |----------eth0|Computer1|
   `.._     _,,'      | Ethernet |          eth1+---------+
       `''''          +----------+
                                     eth1              eth1
                                +----wifi-+          +-wifi----+
                                |Computer2|          |Computer3|
                                +---------+          +---------+



```

You have to put it into a file named like "wifi.sh", and change the first lines to your needs. 

Set the wifi.sh file as executable (Right clic > Properties > Permissions > Execute).

Then run it with sudo on each machine in a terminal :

On the master computer (Computer1) :
```

sudo wifi.sh share

```

On the others (Don't forget to put a different MY_IP on each one)
```

sudo wifi.sh join

```

Here it is :
```

#!/bin/bash
#Author: Mathieu Leplatre (leplatre AT gmail)
#

MY_IP="10.0.0.2"            #Put a different one on each machine
MASTER_IP="10.0.0.3"        #Machine with Internet access
INTERNET_GW="192.168.1.1"   #Your ethernet modem IP
KEY="mypass"            #Your Wifi Key
ESSID="mywifi"              #Your Wifi name


CHANNEL="6"
INTERNET_IP="74.125.47.99" #Google's IP
INTERNET_URL="www.google.com"
ETH_WIFI="eth1"
ETH_LAN="eth0"

function status_wifi {
    ping -I $ETH_WIFI -c 1 -W 10 $MASTER_IP &>/dev/null
    if [ $? -eq 0 ]; then
        echo "Wireless Ad-hoc OK."
    else
        echo "Wireless Ad-hoc failed."
        iwconfig $ETH_WIFI
        ifconfig $ETH_WIFI
    fi
}

function status_internet {
    ping -c 1 -W 10 $INTERNET_IP &>/dev/null
    if [ $? -eq 0 ]; then
        echo "Internet access OK."
    else
        echo "Internet access failed."
    fi

    ping -c 1 -W 10 $INTERNET_URL &>/dev/null
    if [ $? -eq 0 ]; then
        echo "DNS resolving OK."
    else
        echo "DNS resolving failed."
    fi
}

function setup_wifi {
    #Create Ad-Hoc Cell
    echo "Setup Ad-Hoc..."
    iwconfig $ETH_WIFI channel $CHANNEL essid "$ESSID" mode Ad-Hoc key s:$KEY
    echo "Setup static IP address..."
    ifconfig $ETH_WIFI $MY_IP netmask 255.255.255.0
}

function join_share {
    if [ `route -n|grep -c $INTERNET_GW` -eq 1 ]; then
        echo "Remove existing default route..."
        route del -net 0.0.0.0 gw $INTERNET_GW
    fi
    echo "Setup default route..."
    route add default gw $MASTER_IP
}

function share_to_wireless {
    #/etc/sysctl
    #net.ipv4.ip_forward = 1
    #net.ipv4.conf.default.forwarding=1 
    #net.ipv4.conf.all.forwarding=1

    echo "Setup forward and NAT..."
    iptables -A FORWARD -j ACCEPT
    iptables -t nat -A POSTROUTING -o $ETH_LAN -j MASQUERADE
    echo 1 > /proc/sys/net/ipv4/ip_forward 
}

function reset_wifi {
    # Reset Wifi mode
    iwconfig $ETH_WIFI channel $CHANNEL mode Managed
    # Reset routes
    #if [ `route -n|grep -c $INTERNET_GW` -eq 1 ]; then
    #    echo "Remove existing default route..."
    #    route del -net 0.0.0.0 gw $INTERNET_GW
    #fi

    route del -net 0.0.0.0 gw $MASTER_IP
    route add default gw $INTERNET_GW
}

function reset_share {
    # Set the default policy
    iptables -P INPUT ACCEPT
    iptables -P FORWARD ACCEPT
    iptables -P OUTPUT ACCEPT

    # Set the default policy for the NAT table
    iptables -t nat -P PREROUTING ACCEPT
    iptables -t nat -P POSTROUTING ACCEPT
    iptables -t nat -P OUTPUT ACCEPT

    # Delete all rules
    iptables -F
    iptables -t nat -F

    # Delete all chains
    iptables -X
    iptables -t nat -X
}

case "$1" in
    "share" )
    setup_wifi
    share_to_wireless
    /etc/init.d/networking restart
    ;;

    "join" )
    setup_wifi
    join_share
    ;;

    "status" )
    status_wifi
    status_internet
    MY_IP_ETH0=`ifconfig $ETH_LAN|grep "inet addr:"|sed -e's/^.*r://' -e 's/ .*$//'`
    MY_IP_ETH1=`ifconfig $ETH_WIFI|grep "inet addr:"|sed -e's/^.*r://' -e 's/ .*$//'`
    echo "IP Wifi:$MY_IP_ETH1 LAN:$MY_IP_ETH0"    
    ;;

    "reset" )
    reset_share
    reset_wifi
    ;;

    * )
    echo "$0 [share|join|reset]"
    echo "Run as root"
    exit 1;
esac

```

---

### Post by subzero316 on 2008-02-07
try wicd it has an adhoc function in the network menu...:KS:KS:KS

---

