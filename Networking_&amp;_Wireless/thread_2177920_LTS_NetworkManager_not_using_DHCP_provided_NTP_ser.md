---
title: "LTS NetworkManager not using DHCP provided NTP servers Workaround"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by jdehaan@ on 2013-10-01
Hi All,


    finally got irritated enough to make a workaround for this long standing issue: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/267891](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/267891) and [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=627343](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=627343).


    My issue with this is obvious: it does not work as expected.


    Other sugested workarounds are to install ntpd on every system using dhcp client. Since dhcp clients are on average desktop clients (not allowed to run any network facing services) or servers in initial installation stages, someone who suggest this should have their head examined.


    Apparently, it's below NetworkManager's standing to call ntpdate with DHCP supplied ntp-servers, just hard configured ones in /etc/default/ntpdate.


    Every workaround has, ideally, to fit in CMDB managed environments, which means you can't, again ideally, change core files of packages but got to work with files you are allowed to change. In this case it is possible to do it through /etc/default/ntpdate.


    Background: NetworkManager does not call /etc/dhcp/dhclient-exit-hooks.d/ntpdate but does call /etc/network/if-up.d/ntpdate, (hard coded in /etc/NetworkManager/dispatcher.d/01ifupdown) allthough in /etc/NetworkManager/NetworkManager.conf, section [ifupdown], "managed" is set to false, which implies not using it. This file, /etc/network/if-up.d/ntpdate, does call /usr/sbin/ntpdate-debian, another Frank Sinatra solution. This script sources /etc/default/ntpdate.


    Other attempts, for instance trying to intercept the new_ntp_servers, failed on the requirement not to change core files.


    Yes, it's one long line, it is overkill written, but in my personal belief system ("All hail the cpu!") it is better to write understandable code. Be glad I didn't CamelCase it.


    It allows for still using the static ntp servers, only takes action if there is a recent (1 minute) lease file which contains a non-zero ntp-servers option.


    /etc/default/ntpdate:


# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.


# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=no


# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
# NTPSERVERS="ntp.ubuntu.com"


NTPSERVERS=$(STATICNTPSERVERS="ntp.ubuntu.com" ; LEASEFILEDIR=/var/lib/dhcp ; NUMLEASEFILES=$(find $LEASEFILEDIR ! -type d 2>/dev/null|wc -l) ; if [ $NUMLEASEFILES != 0 ] ; then MOSTRECENTLEASEFILE=$(ls -tr $LEASEFILEDIR | tail -n 1) ; if test $(find $LEASEFILEDIR/$MOSTRECENTLEASEFILE ! -mmin +1 2>/dev/null) ; then DHCPNTPSERVERS=$(grep 'option ntp-servers' $LEASEFILEDIR/$MOSTRECENTLEASEFILE|tail -n 1|awk '{printf $3"\n"}'|tr ',' ' '|tr -d ';') ; if [ ! -z "$DHCPNTPSERVERS" ] ; then echo $DHCPNTPSERVERS ; else echo $STATICNTPSERVERS ; fi ; else echo $STATICNTPSERVERS ; fi ; else echo $STATICNTPSERVERS ; fi)


# Additional options to pass to ntpdate
NTPOPTIONS=""

---

