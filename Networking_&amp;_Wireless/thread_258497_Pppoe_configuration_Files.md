---
title: "Pppoe configuration Files ?"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by jadhav333 on 2006-09-16
1) I am ware that we can configure broadband access through pppoeconf.

2) what i need to find out is whether the configuration suggested by my ISP shown below are safe & reliable or whether it compromises my Pc in anyway? People with strong linux knowledge can analyse the attached content and preferably give the implication of the commands on a per line basis.

The files provided by our ISP are as follows:

/etc/ppp/firewall-masq
/etc/ppp/firewall-standalone
/etc/ppp/pppoe.conf
/etc/rc.d/init.d/adsl

also some executable files ?

/usr/sbin/adsl-connect
/usr/sbin/adsl-setup
/usr/sbin/adsl-start
/usr/sbin/adsl-status
/usr/sbin/adsl-stop
/usr/sbin/pppoe


**a) content file: /etc/ppp/firewall-masq**

#!/bin/sh
#
# firewall-masq		This script sets up firewall rules for a machine
#                       acting as a masquerading gateway
#
# Copyright (C) 2000 Roaring Penguin Software Inc.  This software may
# be distributed under the terms of the GNU General Public License, version
# 2 or any later version.
# LIC: GPL

# Interface to Internet
EXTIF=ppp+

ANY=0.0.0.0/0

ipchains -P input ACCEPT
ipchains -P output ACCEPT
ipchains -P forward DENY

ipchains -F forward
ipchains -F input
ipchains -F output

# Deny TCP and UDP packets to privileged ports
ipchains -A input -l -i $EXTIF -d $ANY 0:1023 -p udp -j DENY
ipchains -A input -l -i $EXTIF -d $ANY 0:1023 -p tcp -j DENY

# Deny TCP connection attempts
ipchains -A input -l -i $EXTIF -p tcp -y -j DENY

# Deny ICMP echo-requests
ipchains -A input -l -i $EXTIF -s $ANY echo-request -p icmp -j DENY

# Do masquerading
ipchains -A forward -j MASQ
echo 1 > /proc/sys/net/ipv4/ip_forward

**b) content file: /etc/ppp/firewall-standalone**

#!/bin/sh
#
# firewall-standalone	This script sets up firewall rules for a standalone
#                       machine
#
# Copyright (C) 2000 Roaring Penguin Software Inc.  This software may
# be distributed under the terms of the GNU General Public License, version
# 2 or any later version.
# LIC: GPL

# Interface to Internet
EXTIF=ppp+

ANY=0.0.0.0/0

ipchains -P input ACCEPT
ipchains -P output ACCEPT
ipchains -P forward DENY

ipchains -F forward
ipchains -F input
ipchains -F output

# Deny TCP and UDP packets to privileged ports
ipchains -A input -l -i $EXTIF -d $ANY 0:1023 -p udp -j DENY
ipchains -A input -l -i $EXTIF -d $ANY 0:1023 -p tcp -j DENY

# Deny TCP connection attempts
ipchains -A input -l -i $EXTIF -p tcp -y -j DENY


**c) contents of file /etc/ppp/pppoe.conf**

#***********************************************************************
#
# pppoe.conf
#
# Configuration file for rp-pppoe.  Edit as appropriate and install in
# /etc/ppp/pppoe.conf
#
# NOTE: This file is used by the adsl-start, adsl-stop, adsl-connect and
#       adsl-status shell scripts.  It is *not* used in any way by the
#       "pppoe" executable.
#
# Copyright (C) 2000 Roaring Penguin Software Inc.
#
# This file may be distributed under the terms of the GNU General
# Public License.
#
# LIC: GPL
# $Id: pppoe.conf,v 1.10 2002/04/09 17:28:38 dfs Exp $
#***********************************************************************

# When you configure a variable, DO NOT leave spaces around the "=" sign.

# Ethernet card connected to ADSL modem
ETH=eth0

# ADSL user name.  You may have to supply "@provider.com"  Sympatico
# users in Canada do need to include "@sympatico.ca"
# Sympatico uses PAP authentication.  Make sure /etc/ppp/pap-secrets
# contains the right username/password combination.
# For Magma, use [email]xxyyzz@magma.ca[/email]
USER=in2net

# Bring link up on demand?  Default is to leave link up all the time.
# If you want the link to come up on demand, set DEMAND to a number indicating
# the idle time after which the link is brought down.
DEMAND=no
#DEMAND=300

# DNS type: SERVER=obtain from server; SPECIFY=use DNS1 and DNS2;
# NOCHANGE=do not adjust.
DNSTYPE=SERVER

# Obtain DNS server addresses from the peer (recent versions of pppd only)
# In old config files, this used to be called USEPEERDNS.  Changed to
# PEERDNS for better Red Hat compatibility
PEERDNS=yes

# Make the PPPoE connection your default route.  Set to
# DEFAULTROUTE=no if you don't want this.
DEFAULTROUTE=yes

### ONLY TOUCH THE FOLLOWING SETTINGS IF YOU'RE AN EXPERT

# How long adsl-start waits for a new PPP interface to appear before
# concluding something went wrong.  If you use 0, then adsl-start
# exits immediately with a successful status and does not wait for the
# link to come up.  Time is in seconds.
#
# WARNING WARNING WARNING:
#
# If you are using rp-pppoe on a physically-inaccessible host, set
# CONNECT_TIMEOUT to 0.  This makes SURE that the machine keeps trying
# to connect forever after adsl-start is called.  Otherwise, it will
# give out after CONNECT_TIMEOUT seconds and will not attempt to
# connect again, making it impossible to reach.
CONNECT_TIMEOUT=30

# How often in seconds adsl-start polls to check if link is up
CONNECT_POLL=2

# Specific desired AC Name
ACNAME=

# Specific desired service name
SERVICENAME=

# Character to echo at each poll.  Use PING="" if you don't want
# anything echoed
PING="."

# File where the adsl-connect script writes its process-ID.
# Three files are actually used:
#   $PIDFILE       contains PID of adsl-connect script
#   $PIDFILE.pppoe contains PID of pppoe process
#   $PIDFILE.pppd  contains PID of pppd process
CF_BASE=`basename $CONFIG`
PIDFILE="/var/run/$CF_BASE-adsl.pid"

# Do you want to use synchronous PPP?  "yes" or "no".  "yes" is much
# easier on CPU usage, but may not work for you.  It is safer to use
# "no", but you may want to experiment with "yes".  "yes" is generally
# safe on Linux machines with the n_hdlc line discipline; unsafe on others.
SYNCHRONOUS=no

# Do you want to clamp the MSS?  Here's how to decide:
# - If you have only a SINGLE computer connected to the ADSL modem, choose
#   "no".
# - If you have a computer acting as a gateway for a LAN, choose "1412".
#   The setting of 1412 is safe for either setup, but uses slightly more
#   CPU power.
CLAMPMSS=1412
#CLAMPMSS=no

# LCP echo interval and failure count.
LCP_INTERVAL=180
LCP_FAILURE=5

# PPPOE_TIMEOUT should be about 4*LCP_INTERVAL
PPPOE_TIMEOUT=720

# Firewalling: One of NONE, STANDALONE or MASQUERADE
FIREWALL=STANDALONE

# Linux kernel-mode plugin for pppd.  If you want to try the kernel-mode
# plugin, use LINUX_PLUGIN=/etc/ppp/plugins/rp-pppoe.so
LINUX_PLUGIN=

# Any extra arguments to pass to pppoe.  Normally, use a blank string
# like this:
PPPOE_EXTRA=""

# Rumour has it that "Citizen's Communications" with a 3Com
# HomeConnect ADSL Modem DualLink requires these extra options:
# PPPOE_EXTRA="-f 3c12:3c13 -S ISP"

# Any extra arguments to pass to pppd.  Normally, use a blank string
# like this:
PPPD_EXTRA=""


########## DON'T CHANGE BELOW UNLESS YOU KNOW WHAT YOU ARE DOING
# If you wish to COMPLETELY overrride the pppd invocation:
# Example:
# OVERRIDE_PPPD_COMMAND="pppd call dsl"

# If you want adsl-connect to exit when connection drops:
# RETRY_ON_FAILURE=no






# Deny ICMP echo-requests
ipchains -A input -l -i $EXTIF -s $ANY echo-request -p icmp -j DENY

[B]
d) contents of file /etc/rc.d/init.d/adsl[/B]

#!/bin/sh
#
# adsl                     This script starts or stops an ADSL connection
#
# chkconfig: 2345 99 01
# description: Connects to ADSL provider
#
# LIC: GPL
#
# Copyright (C) 2000 Roaring Penguin Software Inc.  This software may
# be distributed under the terms of the GNU General Public License, version
# 2 or any later version.

# Source function library if it exists
test -r /etc/rc.d/init.d/functions && . /etc/rc.d/init.d/functions

# From AUTOCONF
prefix=/usr
exec_prefix=${prefix}

# Paths to programs
START=${exec_prefix}/sbin/adsl-start
STOP=${exec_prefix}/sbin/adsl-stop
STATUS=${exec_prefix}/sbin/adsl-status
case "$1" in
    start)
        echo -n "Bringing up ADSL link"

	$START
	if [ $? = 0 ] ; then
		touch /var/lock/subsys/adsl
	        echo_success
	else
		echo_failure
	fi
        echo ""
        ;;

    stop)
        echo -n "Shutting down ADSL link"

	$STOP > /dev/null 2>&1
	if [ $? = 0 ] ; then
		rm -f /var/lock/subsys/adsl
	        echo_success
	else
		echo_failure
	fi
        echo ""
        ;;

    restart)
	$0 stop
	$0 start
	;;

    status)
	$STATUS
	;;

    *)
        echo "Usage: adsl {start|stop|restart|status}"
        exit 1
esac

exit 0

---

