---
title: "Kismet problem"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by fractalman on 2011-05-19
Ok i recently installed backtrack 5 on my hd, mainly just so i could have a look at it and test my own wifi networks security, i'm also using the install to learn a bit about using the shell too and to learn the terminal way of doing things.

Anyway the problem i have is this

The version of kismet on backtrack 5 needs the capture source configuring and i can't work out what the problem is.  i have tried changing the config file but had no luck with several combinations, after adding the source from the on screen prompt i get this
[http://v1.iimmgg.com/images/is8gr/227d2f7053e223a52efa2a7899d0a577.png](http://v1.iimmgg.com/images/is8gr/227d2f7053e223a52efa2a7899d0a577.png)

when i close the server down it looks like this
[http://v1.iimmgg.com/images/is8gr/abb8e30ee5464ef33b44ead60c66285a.png](http://v1.iimmgg.com/images/is8gr/abb8e30ee5464ef33b44ead60c66285a.png)

the only part of the config file that contains anything about sources reads as follows
# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2009-newcore

# Name of server (Purely for organizational purposes)
servername=Kismet_2009

# Prefix of where we log (as used in the logtemplate later)
# logprefix=/some/path/to/logs

# Do we process the contents of data frames?  If this is enabled, data
# frames will be truncated to the headers only immediately after frame type
# detection.  This will disable IP detection, etc, however it is likely
# safer (and definitely more polite) if monitoring networks you do not own.
# hidedata=true

# Do we allow plugins to be used?  This will load plugins from the system
# and user plugin directiories when set to true (See the README for the default
# plugin locations).
allowplugins=true

# See the README for full information on the new source format
# ncsource=interface:options
# for example:
# ncsource=wlan0
# ncsource=wifi0:type=madwifi
# ncsource=wlan0:name=intel,hop=false,channel=11

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example, if sources with name=prismsource and name=ciscosource are defined,
# and you only want to enable those two:
# enablesources=prismsource,ciscosource

# Control which channels we like to spend more time on.  By default, the list
# of channels is pulled from the driver automatically.  By setting preferred channels,
# if they are present in the channel list, they'll be set with a timing delay so that
# more time is spent on them.  Since 1, 6, 11 are the common default channels, it makes
# sense to spend more time monitoring them.
# For finer control, see further down in the config for the channellist= directives.
preferredchannels=1,6,11

i have LM Technologies LM-001 usb wifi adapter using the zd1211 driver and its on wlan0,  how should i edit the config file?

I know that it works with kismet because i have an 11:04 install on the same pc and i had to install kismet on that earlier, and after changing the config file for the 11:04 version it worked fine

on 11:04 it looks like this
[http://v1.iimmgg.com/images/is8gr/781e1876f0db8bbcb19951d4dc4dbec7.jpg](http://v1.iimmgg.com/images/is8gr/781e1876f0db8bbcb19951d4dc4dbec7.jpg)


the config file for the version on 11:04  is different to the one on the backtrack 5 and the source part reads as follows
# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=your_user_here

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
source=zd1211,wlan0,lm-001

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource


# Automatically destroy VAPs on multi-vap interfaces (like madwifi-ng).
# Madwifi-ng doesn't work in rfmon when non-rfmon VAPs are present, however
# this is a fairly invasive change to the system so it CAN be disabled.  Expect
# things not to work in most cases if you do disable it, however.
vapdestroy=true



you can see where i added  'source=zd1211,wlan0,lm-001'    why does this not work in my backtrack 5 install? everything is showing up on ifconfig iwconfig etc, the drivers are working because it picks up several other networks,   so if anyone knows how to configure the backtrack version of kismet, your knowledge would be gratefully appreciated 

Thanks

---

### Post by fractalman on 2011-05-20
Sorry to bump the thread, i know this might be in the wrong section.  I was wondering is it possible to remove the 2009 version of kismet from BT5 and install the 2007 version instead?  if anyone has the repo and commands it would be most appreciated.  thanks

---

