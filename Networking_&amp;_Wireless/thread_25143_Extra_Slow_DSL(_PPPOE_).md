---
title: "Extra Slow DSL( PPPOE )"
date: 2005-04-09
forum: Networking &amp; Wireless
---

### Post by Jefis on 2005-04-09
I have DLS internet, connecting via eth0 from ppp0.
I have configured it from provided CD, compiled pppoe.
It works, and connect, but works very slow, averange download speed is 10kb/s
and it shoud about 30kb/s.

------------------------------------------------------------------------------------------------------
Start scipt (/usr/local/bin/start-pppoe ) looks like:
#!/bin/bash

# (c) 2000 Efficient Networks, Inc.
# Copyright (c) 1999,2000 by Network TeleSystems, Inc.
# All rights reserved.
# Internet [http://www.nts.com](http://www.nts.com)
#
# Please direct all support-related calls to your licensed Internet Service 
# Provider.  NTS does not provide direct support.  NTS works through Internet
# Service Providers that have licensed our software.

unset USERID
unset ACNAME
unset SERVICENAME
unset ETHERNET
unset LINKNAME
unset SYNC
unset PERSIST

#----- Beginning of User Changeable Area ----------------------------------

# Note, when making changes be sure NOT to insert white space (blanks)
# around the "=" symbol.  
# For example:  USERID= "RoadRunner"           
# This will not work.  It should be written as:  USERID="RoadRunner"

# Replace YourUserID with that of the userid supplied by your ISP.
# You will also need to add the user-id and password to the 
# /etc/ppp/chap-secrets and/or /etc/ppp/pap-secrets file.
USERID="myuser@secret.lt"

# If you need to connect to a specific service name then uncomment the line 
# below.  Replace YourServiceName with the service name specified by your ISP.
# SERVICENAME="YourServiceName"

# If you need to access a specific Access Concentrator then uncomment the
# line below.  Replace YourAccessConcentratorName with the name specified by 
# your ISP. 
# ACNAME="YourAccessConcentratorName"

# Not all systems can support the sync option.  Uncomment the next line if 
# yours can.  See the README, section **IMPROVE PERFORMANCE**, for more 
# information on when you can and cannot use this option.
SYNC=sync

# If you want your PPPoE connection to automatically reconnect if the 
# connection should break, uncomment the next line.
PERSIST=persist

# If the Ethernet NIC that you will be using is not at eth0 you will need
# to supply that information below by replacing eth0 with that of your
# network card.  ifconfig command will show a list of network interfaces.
INTERFACE="eth0"

# Programs w/path.  If your system has these programs in different locations
# update the paths as appropriate.
PPPD=/usr/sbin/pppd
PPPOED=/usr/local/bin/pppoed
IFCONFIG=/sbin/ifconfig

#----- End User Changeable Area ------------------------------------------------

if [ "$USERID" = "YourUserID" ]; then
    echo 'Are you sure your correct login user ID is "YourUserID".'
fi

$IFCONFIG $INTERFACE 0.0.0.0 up -arp

if [ -n "$1" ]; then
    SERVICENAME="$1"
fi

if [ -n "$SERVICENAME" ]; then
	SERVICENAME="-S $SERVICENAME"
fi
if [ -n "$ACNAME" ]; then
	ACNAME="-A $ACNAME"
fi
if [ -n "$INTERFACE" ]; then
	INTERFACE="-I $INTERFACE"
fi
if [ -n "$USERID" ]; then
	USERID="name $USERID"
fi
if [ -n "$PERSIST" ]; then
	PERSIST="persist"
fi
if [ -n "$SYNC" ]; then
	SYNC="sync"
fi


$PPPD \
    pty "$PPPOED $INTERFACE $SERVICENAME $ACNAME" \
    $USERID \
    file /etc/ppp/options.pppoe \
    defaultroute \
    $SYNC \
    $PERSIST
---------------------------------------------------------------------------------------------
All other files (/etc/resolv.conf , /etc/ppp/chap-secrets , /etc/ppp/pap-secrets )
are configured correctly


----------------------------------------------------------------------------------------------
One more thing , from readme file
----------------------------------------------------------------------------------------------

7) IMPROVE PERFORMANCE - SYNC OPTION

Using the **sync** option can reduce pppoed's CPU utilization to about 1/4.  

If you are running the ready build kernel from RedHat 6.1 or Mandrake 6.5,
your system is ready to use the sync option after you do two things.

   1) add the following line to the file /etc/conf.modules:
         alias tty-ldisc-13 n_hdlc

   2) Edit the /usr/local/bin/start-pppoe file.  Find the comment section 
      that talks about the **sync** option and uncomment the sync variable.

There may be other recent package releases of Linux that are ready to support
the sync option.  If you have one of them, try the above out.  If it does not 
work, then use the information below to help you through the process of 
getting the right pieces together to make it work.


To use the sync option you need:
  1) tty line discipline support for hdlc.
  2) pppd version 2.3.7 or higher
  3) Kernel module for ppp that supports sync


1) tty line discipline support for hdlc

The Hdlc tty line discipline support is in RedHat 6.x release.  It was not 
in the RedHat 5.2 release; however, it can be added.  On RedHat release 5.2,
6.0 and 6.1, you will need to add the following line to file /etc/conf.modules, 
so that n_hdlc can be loaded automatically on demand:  
  alias tty-ldisc-13 n_hdlc
  
Otherwise you would need to explicitly run the command: insmod n_hdlc

For the RedHat 5.2 release you will need to get a copy of the file n_hdlc.c
from one of the later releases. (RedHat 6.0 has it)  Copy the file to your
kernel source tree /usr/src/linux/drivers/char.  Update the Makefile.  
Locate the line with "M_OBJS :=". Append to the end of this line, n_hdlc.o.  
The line should then read as "M_OBJS := n_hdlc.o".  Rebuild the modules and 
install modules.  Refer to related how-to's and kernel release notes for 
rebuilding modules.  I've done this; it works.  However, this is getting 
messy for some, and it may be time to upgrade.


2) pppd version 2.3.7 or higher

If you do not have pppd version 2.3.7 or higher you must get one before you 
can proceed.  Edit the start-pppoe file.  Find the comment section that talks
about the sync option and uncomment the sync variable.


3) Kernel module for ppp that supports sync

The kernel or kernel module supporting ppp must have sync support in it.  
Redhat 6.0 ppp kernel module does not.  It is present in the 6.1 release.
The pppd 2.3.7 or newer archive will have an updated kernel ppp driver source
that can be installed and built.  If you must update your system, you might
just as well get the latest version.  To install follow the README and 
README.linux that comes with the archive.



You can check syslog file for messages from pppoed to see if the sync option
was accepted.  e.g. the output of "tail -25 /var/log/messages"  should 
contain a line like this:
   ... pppoed[5555]: Operating in Sync mode.
   
If it didn't work, you will see "Operating in Async mode" instead.  This 
may be due to an old ppp.o kernel driver module being used with the new pppd 
daemon.

If you see the message:
Required N_HDLC line discipline for sync option is not supported by the system.

The n_hdlc.o kernel module did not load.  Recheck syslog for error messages 
and check /etc/conf.modules for the line:
  alias tty-ldisc-13 n_hdlc
---------------------------------------------------------------------------------------------
One more:
---------------------------------------------------------------------------------------------
root@localhost:/usr/local/bin # tail -25 /var/log/messages
Apr  9 16:23:46 localhost pppd[17652]: Terminating on signal 2.
Apr  9 16:23:46 localhost pppd[17652]: Connect time 94.4 minutes.
Apr  9 16:23:46 localhost pppd[17652]: Sent 21928020 bytes, received 384118300 bytes.
Apr  9 16:23:46 localhost pppd[17652]: Connection terminated.
Apr  9 16:23:48 localhost pppd[17652]: Exit.
Apr  9 16:29:25 localhost kernel: cdrom: hdc: mrw address space DMA selected
Apr  9 16:32:03 localhost pppd[24444]: pppd 2.4.2 started by root, uid 0
Apr  9 16:32:03 localhost pppd[24444]: Using interface ppp0
Apr  9 16:32:03 localhost pppd[24444]: Connect: ppp0 <--> /dev/pts/3
Apr  9 16:32:06 localhost pppd[24444]: PAP authentication succeeded
Apr  9 16:32:07 localhost pppd[24444]: local  IP address 85.206.101.235
Apr  9 16:32:07 localhost pppd[24444]: remote IP address 213.190.60.19
Apr  9 16:45:31 localhost -- MARK --
root@localhost:/usr/local/bin #                             
------------------------------------------------------------------------------------------
Added source to my pppoe

---

### Post by soul_rebel on 2005-04-10
you get better performance with another os/distro? may it be a provider's fault?

---

