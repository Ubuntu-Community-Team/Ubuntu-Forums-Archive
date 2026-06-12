---
title: "Kismet capture source issues **help**"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by ether3al on 2008-11-12
Hi All im having trouble getting kismet to read the capture source.

Error:

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'BCM4312' in source 'BCM4312,eth1,broadcom'


Please see config below:

  lspci | grep Broadcom\ Corporation
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g 

# Sources are defined as:
# source=BCM4312,eth1,broadcom
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=BCM4312,eth1,broadcom

Any assistance as to where I have gone wrong would be appreciate!

---

### Post by ether3al on 2008-11-12
OK i think i have got the source issue sorted, now i seem to have a compatibility issue

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (broadcom): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.

---

### Post by goranj on 2009-04-15
Ether3al,

I thank many people, including myself, would be very interested to hear how you got the source issue sorted, as we are having the same issue.

Thanks in advance,
goranj

---

### Post by ether3al on 2009-04-16
Unfortunately I have discovered that broadcom does not support rfmon so will not work with kismet.

---

### Post by goranj on 2009-04-16
Fair enough, but the point is that many people are trying this with many different wireless cards, and are getting the same "FATAL: unknown capture source type" message.

So if you can give us an insight into how you resolved THAT issue, maybe then we can get to the next step and find out if our wireless card are supported for rfmon.

Right now we can't even get to that step. So you have a chance to be our hero. :-)

Thanks again,
goranj

---

### Post by chili555 on 2009-04-16
> So you have a chance to be our hero.Do I get a cape and a tight shirt with "C" on the front?

When you install Kismet, it has no way to know whether you have a Prism or Atheros or Intel or whomever card. It is up to the user to set that information in the */etc/kismet/kismet.conf* file. For example, here is the relevant part of mine:```
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,wlan0,Intel
```So you don't have to trial-and-error guess, Kismet has given a nifty README which you can read by opening a terminal and doing:```
less /usr/share/doc/kismet/README.gz
```You will be particularly interested in Sections 9 and 12.

As we progress into the advanced subjects in Linux, we must increasingly depend on README's, which are often stored in /usr/share/doc and manual pages, which may be accessed at the terminal:```
man kismet
man kismet.conf
```

---

### Post by usopenplayer on 2010-12-13
> **chili555 said:**
> Do I get a cape and a tight shirt with "C" on the front?

When you install Kismet, it has no way to know whether you have a Prism or Atheros or Intel or whomever card. It is up to the user to set that information in the */etc/kismet/kismet.conf* file. For example, here is the relevant part of mine:```
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,wlan0,Intel
```So you don't have to trial-and-error guess, Kismet has given a nifty README which you can read by opening a terminal and doing:```
less /usr/share/doc/kismet/README.gz
```You will be particularly interested in Sections 9 and 12.

As we progress into the advanced subjects in Linux, we must increasingly depend on README's, which are often stored in /usr/share/doc and manual pages, which may be accessed at the terminal:```
man kismet
man kismet.conf
```

Why can't kismet determine what wifi card you are using? 
If the system can access the wifi just fine, then why can't kismet vicariously take control through that?
Does kismet require more fine-grained control that Ubuntu allows? And if the drivers are located on the system, why can't it detect them... I thought this is the kind of stuff that computers excel at.

---

