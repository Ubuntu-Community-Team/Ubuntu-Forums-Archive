---
title: "Kismet not working"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-04
Hi when I run kismet (as root) i get the following output

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.

---

### Post by fractalman on 2011-06-04
Hi,  

Which version of kismet are you using and which o/s are you using to run, this info will make it easier to guide you to the right files to edit

you need to find out the interface you are using for wireless and then change the kismet config file and add the interface

If open a terminal and type

```
iwconfig
```

you should see your wireless interface, it will  called something like wlan0 or wifi0/ath0 depending on your driver

next open the kismet.config file and scroll down to the section on sources then add your interface to the source line, if you bear with me i'll boot backtrack 5 and find the section to post and show you.

---

### Post by kalimojo on 2011-06-04
HI sorted it, i had to edit /etc/kismet/kismet.conf and change the line none,none,addme to ipw2200,eth1,eth1

i ran 

sudo gedit /etc/kismet/kismet.conf

i found my wireless card name - ipw2200 - using nm-tool | more

---

### Post by fractalman on 2011-06-04
```
# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
[SIZE=4]source=zd1211,wlan0,lm-001[/SIZE]

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource


# Automatically destroy VAPs on multi-vap interfaces (li
```


you see the line that reads -  source=zd1211,wlan0,lm00

thats what you have to edit according to what driver, interface and device you have

source=
zd1211 = your wireless driver
wlan0   = your wireless interface
lm00    =  your wireless device

so for me i am using a zd1211 driver on the wlan0 interface with a lm001 wireless usb wifi adapter

this is actually from the 2007 kismet, if you are using the later version the config file will show 'ncsource' instead of 'source', just edit accordingly

if your using ubuntu/linux it should be at  /etc/kismet/kismet.conf
if you're using backtrack 5 it should be at  /usr/local/etc/*kismet*.*conf*

---

