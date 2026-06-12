---
title: "cable modem configuration problem"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by aborshir on 2006-12-16
Hi all and thanks in advance,

i am using ubuntu 6.10 and an external THOMSON TCM425 cable modem on a laptop.
i have downloaded and edited a dialer soplied by my isp for linux which i will add here shortly.

this is what happend:
1. installed the script which add the dialer and modifies the port requests for the isp
2. i have successfully surfed for a couple of hours.
3. aftert several hours i have noticed that every once in a while the browser stops showing new pages, to fix this at first i use the cablestop and then cablestart commands.
4. a time comes when this doesnt help and i need to restart ubuntu for access.
5. i can access the net now only via wireless or already running networks.

please help me make sense of the mess, i really do not want to get back to windows..

enclosed are the 1>full script, followed by 2>the error msg when trying to connect 

1> 
#!/bin/bash
##############################################
#     Actcom connection script for cables    #
#        Linux versions: redhat/debian       #
#  For more information call  1-800-300-123  #
#                                            #
#             [email]help@actcom.net.il[/email]             #
##############################################
# Main vars here:
wget_location="/usr/bin/wget"
pap_secrets="/etc/ppp/pap-secrets"
resolv_conf="/etc/resolv.conf"
l2tp_conf="/etc/l2tp/l2tp.conf"
l2tp_get="http://support.actcom.co.il/support/tips/cableen/l2tp/l2tp.conf.down"
cablestart="/usr/sbin/cablestart"
cablestop="/usr/sbin/cablestop"
cablestart_get="http://support.actcom.co.il/support/tips/cableen/l2tp/cablestart"
cablestop_get="http://support.actcom.co.il/support/tips/cableen/l2tp/cablestop"
# End of main vars.

# if you dont know what you're doing, dont change anything below.
echo -e "\033[30;1mStarting cables installation for linux (Actcom.co.il)\033[0m"
echo -n "Checking for privilages... "
if [ $UID != 0 ]; then
	echo -e "\033[31;1mError\033[0m"
	echo -e "\033[31;1mPlease change to root and then run this script \033[34;1m(Change to root with the command \"su -\") \033[0m"
	exit 0
else
	echo -e "\033[34;1mOkay\033[0m"
fi
echo -n "Checking for /usr/bin/wget... "
if [ -e $wget_location ]; then
	echo -e "\033[34;1mOkay\033[0m"
else 
	echo -e "\033[31;1mError\033[0m"
	echo -e "\033[31;1m"$wget_location "is required for the files download.\033[0m"
	exit 0
fi
echo -n "Looking for $pap_secrets... "
if [ -f $pap_secrets ]; then
	echo -e "\033[34;1mOkay\033[0m"
else 
	echo -e "\033[31;1mError\033[0m"
	echo -e "\033[31;1m"$pap_secrets "is required for the connection.\033[0m"
	exit 0
fi
echo -n "Looking for $resolv_conf... "
if [ -f $resolv_conf ]; then
        echo -e "\033[34;1mOkay\033[0m"
else
        echo -e "\033[31;1mError\033[0m"
        echo -e "\033[31;1m"$resolv_conf "is required for the connection - no worry, the script is creating one for you.\033[0m"
#        exit 0
fi
	
echo -ne "\033[30;1mAll seem Okay!, do you wish to continue? [y/n] (default: n): \033[0m"
read -e yn
if [ -z $yn ] ; then
	echo -e "\033[31;1mNo input, exiting.\033[0m"
	exit 0
else 
	if [ $yn = y ]; then
		echo -e "\033[34;1mStarting the installation...\033[0m"
	else 
		if [ $yn = n ]; then
			echo -e "\033[31;1mexiting...\033[0m"
			exit 0
		else
			echo -e "\033[31;1mInput unrecognized, exiting.\033[0m"
			exit 0
		fi
	fi
fi
echo -e "\033[30;1mPlease select your linux distrobution\033[0m"
echo -e "1. RedHat based (Fedora, Redhat)"
echo -e "2. Debian based (Debian)"
echo -ne "\033[30;1mYour choice: \033[0m"
read -e distrobution
if [ -z $distrobution ] ; then
        echo -e "\033[31;1mNo input, exiting.\033[0m"
        exit 0
else
        if [ $distrobution = 1 ]; then
		get="http://support.actcom.co.il/support/tips/cableen/rp-l2tp-0.4-1jdl.i386.rpm"
        else
                if [ $distrobution = 2 ]; then   
			get="http://support.actcom.co.il/support/tips/cableen/rp-l2tp_0.4-2_i386.deb"
                else
                        echo -e "\033[31;1mInput unrecognized, exiting.\033[0m"
			exit 0
                fi
        fi
fi
echo -ne "\033[30;1mPlease enter your actcom username (small letters without the @cactcom! for example: tom123): \033[0m"
read username
if [ -z $username ] ; then 
	echo -e "\033[31;1mNo input, exiting.\033[0m"
	exit 0
fi
echo -ne "\033[30;1mPlease enter your actcom password (case sensetive!): \033[0m"
read password
if [ -z $password ] ; then
	echo -e "\033[31;1mNo input, exiting.\033[0m"
        exit 0
fi
################# Updating pap_secrets file and resolv.conf #################
echo "\"$username@cactcom\"  \"172.26.255.197\"  \"$password\"" > $pap_secrets
echo "nameserver 192.114.47.4" > /etc/resolv.conf
echo "nameserver 192.114.47.52" >> /etc/resolv.conf
mkdir /etc/l2tp > /dev/null 2> /dev/null
################# Creating cablestart and cablestop scripts ##################################
## cable start ##
#################
wget $cablestart_get -P /usr/sbin > /dev/null 2> /dev/null
#################
## cable  stop ##
#################
wget $cablestop_get -P /usr/sbin > /dev/null 2> /dev/null
################# End of connection scripts creation ###################################################
echo -e "\033[30;1mPlease wait while installing... \033[0m"
wget $get > /dev/null 2> /dev/null
if [ $distrobution = 1 ]; then
	rpm -Uhv rp-l2tp-0.4-1jdl.i386.rpm
else 
	dpkg -i rp-l2tp_0.4-2_i386.deb
fi
ln -s /usr/sbin/l2tpd /usr/local/sbin/l2tpd > /dev/null 2> /dev/null
ln -s /usr/sbin/l2tp-control /usr/local/sbin/l2tp-control > /dev/null 2> /dev/null

############ l2tp.conf creation ################
wget $l2tp_get -P /etc/l2tp > /dev/null 2> /dev/null 2> /dev/null
mv /etc/l2tp/l2tp.conf.down /etc/l2tp/l2tp.conf > /dev/null 2> /dev/null
echo "lac-pppd-opts \"user $username@cactcom debug persist noipdefault defaultroute usepeerdns noauth lcp-echo-interval 20 lcp-echo-failure 10\"" >> $l2tp_conf
################# END OF l2tp.conf creation ##################################################

echo -e "\033[34;1mFinished installation\033[0m"
echo -en "\033[30;1mSetting privileges... \033[0m"
chmod +x $cablestart
chmod +x $cablestop
echo -e "\033[34;1mDone\033[0m"
echo -e "\033[30;1mTo connect, run the command \033[34;1mcablestart\033[0m \033[30;1mas root.\033[0m"
echo -e "\033[30;1mTo disconnect, run the command \033[34;1mcablestop\033[0m \033[30;1mas root.\033[0m"
echo -en "\033[0m"
### END OF SCRIPT ###


2>

root@or-laptop:/home/or# cablestart
There is already a pid file /var/run/dhclient.eth0.pid with pid 4804
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:c2:df:c0:fa
Sending on   LPF/eth0/00:14:c2:df:c0:fa
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 213.57.35.2 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:c2:df:c0:fa
Sending on   LPF/eth0/00:14:c2:df:c0:fa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.241.192.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.241.192.1
bound to 172.27.153.174 -- renewal in 1501 seconds.
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported
SIOCDELRT: No such process
root@or-laptop:/home/or# 


thanks 
Or

---

### Post by x64Jimbo on 2006-12-16
How about getting a cheap router to handle talking to the cable modem for you? You shouldn't ever connect your computer directly to the internet anyway. NAT is the way to go.

---

