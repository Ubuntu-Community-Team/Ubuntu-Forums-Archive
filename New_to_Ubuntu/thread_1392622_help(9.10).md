---
title: "help(9.10)"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by en_mohamed on 2010-01-28
welcome dears
i have upgraded to 9.10 after restart i discoverd that internet did not respond 
i noticed that network sign is (X) then i done new connection but not responding also
i noticed also the interface card is on
please if any one know this problem help me thanks advance

---

### Post by MelDJ on 2010-01-28
what kind of connection?

---

### Post by Kalamata on 2010-01-28
Hi en_mohamed,
 
A similar issue happend to me when upgrading from 9.04 to 9.10. By my surprise the wifi and the Ethernet stop working after upgrading, but my biggest surprise was to find out that the Sierra Wireless card that I had battle for months to get it to work with 9.04 was now working like a champ. 
 
The way that I resolved wifi and eth0 issue was clean install of 9.10. My wifi and eth0 are now working, BUT the wireless card connects and I am able to browse by IP address but not by URL. Some where, some how the DNS is not working while using the wireless card.
 
This is what is on the avahi-daemon file:
 
#!/bin/sh
#
# If we have an unicast .local domain, we immediately disable avahi to avoid
# conflicts with the multicast IP4LL .local domain
if [ -x /usr/lib/avahi/avahi-daemon-check-dns.sh ]; then
exec /usr/lib/avahi/avahi-daemon-check-dns.sh
fi
 
and,
 
This is what is on the avahi-daemon-check-dns file:
 
#!/bin/sh
#
# If we have an unicast .local domain, we immediately disable avahi to avoid
# conflicts with the multicast IP4LL .local domain
PATH=/bin:/usr/bin:/sbin:/usr/sbin
RUNDIR="/var/run/avahi-daemon/"
DISABLE_TAG="$RUNDIR/disabled-for-unicast-local"
NS_CACHE="$RUNDIR/checked_nameservers"
AVAHI_DAEMON_DETECT_LOCAL=1
test -f /etc/default/avahi-daemon && . /etc/default/avahi-daemon
if [ "$AVAHI_DAEMON_DETECT_LOCAL" != "1" ]; then
exit 0
fi
ensure_rundir() {
if [ ! -d ${RUNDIR} ] ; then 
mkdir -m 0755 -p ${RUNDIR}
chown avahi:avahi ${RUNDIR}
fi 
}
dns_reachable() {
# If there are no nameserver entries in resolv.conf there is no dns reachable
$(grep -q nameserver /etc/resolv.conf) || return 1;
# If there is no local nameserver and no we have no global ip addresses
# then we can't reach any nameservers
if ! $(egrep -q "nameserver 127.0.0.1|::1" /etc/resolv.conf); then 
# Get addresses of all running interfaces
ADDRS=$(LC_ALL=C ifconfig | grep ' addr:')
# Filter out all local addresses
ADDRS=$(echo "${ADDRS}" | egrep -v ':127|Scope:Host|Scope:Link')
if [ -z "${ADDRS}" ] ; then
return 1;
fi
fi
return 0
}
dns_has_local() { 
# Some magic to do tests 
if [ -n "${FAKE_HOST_RETURN}" ] ; then
if [ "${FAKE_HOST_RETURN}" = "true" ]; then
return 0;
else
return 1;
fi
fi
OUT=`LC_ALL=C host -t soa local. 2>&1`
if [ $? -eq 0 ] ; then
if echo "$OUT" | egrep -vq 'has no|not found'; then
return 0
fi
else 
# Checking the dns servers failed. Assuming no .local unicast dns, but
# remove the nameserver cache so we recheck the next time we're triggered
rm -f ${NS_CACHE}
fi
return 1
}
dns_needs_check() {
TMP_CACHE="${NS_CACHE}.$$"
RET=0
ensure_rundir
cat /etc/resolv.conf | grep "nameserver" | sort > ${TMP_CACHE} || return 0
if [ -e ${NS_CACHE} ]; then 
DIFFERENCE=$(diff -w ${NS_CACHE} ${TMP_CACHE})
echo "${DIFFERENCE}" | grep -q '^>'
ADDED=$?
echo "${DIFFERENCE}" | grep -q '^<'
REMOVED=$?
# Avahi was disabled and no servers were removed, no need to recheck
[ -e ${DISABLE_TAG} ] && [ ${REMOVED} -ne 0 ] && RET=1
# Avahi was enabled and no servers were added, no need to recheck
[ ! -e ${DISABLE_TAG} ] && [ ${ADDED} -ne 0 ] && RET=1
fi
mv ${TMP_CACHE} ${NS_CACHE}
return ${RET};
}
 
enable_avahi () {
# no unicast .local conflict, so remove the tag and start avahi again
if [ -e ${DISABLE_TAG} ]; then
rm -f ${DISABLE_TAG}
start avahi-daemon || :
fi
}
disable_avahi () {
[ -e ${DISABLE_TAG} ] && return
stop avahi-daemon || :
if [ -x /usr/bin/logger ]; then
logger -p daemon.warning -t avahi <<EOF
Avahi detected that your currently configured local DNS server serves
a domain .local. This is inherently incompatible with Avahi and thus
Avahi disabled itself. If you want to use Avahi in this network, please
contact your administrator and convince him to use a different DNS domain,
since .local should be used exclusively for Zeroconf technology.
For more information, see [http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)
EOF
fi
ensure_rundir
touch ${DISABLE_TAG}
}
if ! dns_reachable ; then
# No unicast dns server reachable, so enable avahi
enable_avahi
# And blow away the dns cache, so we force a recheck when the interface comes
# up again
rm -f ${NS_CACHE}
exit 0
fi
# Check if the dns needs checking..
dns_needs_check || exit 0
if dns_has_local ; then
# .local from dns server, disabling avahi
disable_avahi
else
# no .local from dns server, enabling avahi
enable_avahi
fi
exit 0
 
 
I can't confirm that re-installing 9.10 will address your issue but it did for me. I any one has any idea of how to address my DNS issue while using my wireless card I will appreciate any assistance.
 
Kalamata...

---

### Post by en_mohamed on 2010-01-28
> **Kalamata said:**
> Hi en_mohamed,
 
A similar issue happend to me when upgrading from 9.04 to 9.10. By my surprise the wifi and the Ethernet stop working after upgrading, but my biggest surprise was to find out that the Sierra Wireless card that I had battle for months to get it to work with 9.04 was now working like a champ. 
 
The way that I resolved wifi and eth0 issue was clean install of 9.10. My wifi and eth0 are now working, BUT the wireless card connects and I am able to browse by IP address but not by URL. Some where, some how the DNS is not working while using the wireless card.
 
This is what is on the avahi-daemon file:
 
#!/bin/sh
#
# If we have an unicast .local domain, we immediately disable avahi to avoid
# conflicts with the multicast IP4LL .local domain
if [ -x /usr/lib/avahi/avahi-daemon-check-dns.sh ]; then
exec /usr/lib/avahi/avahi-daemon-check-dns.sh
fi
 
and,
 
This is what is on the avahi-daemon-check-dns file:
 
#!/bin/sh
#
# If we have an unicast .local domain, we immediately disable avahi to avoid
# conflicts with the multicast IP4LL .local domain
PATH=/bin:/usr/bin:/sbin:/usr/sbin
RUNDIR="/var/run/avahi-daemon/"
DISABLE_TAG="$RUNDIR/disabled-for-unicast-local"
NS_CACHE="$RUNDIR/checked_nameservers"
AVAHI_DAEMON_DETECT_LOCAL=1
test -f /etc/default/avahi-daemon && . /etc/default/avahi-daemon
if [ "$AVAHI_DAEMON_DETECT_LOCAL" != "1" ]; then
exit 0
fi
ensure_rundir() {
if [ ! -d ${RUNDIR} ] ; then 
mkdir -m 0755 -p ${RUNDIR}
chown avahi:avahi ${RUNDIR}
fi 
}
dns_reachable() {
# If there are no nameserver entries in resolv.conf there is no dns reachable
$(grep -q nameserver /etc/resolv.conf) || return 1;
# If there is no local nameserver and no we have no global ip addresses
# then we can't reach any nameservers
if ! $(egrep -q "nameserver 127.0.0.1|::1" /etc/resolv.conf); then 
# Get addresses of all running interfaces
ADDRS=$(LC_ALL=C ifconfig | grep ' addr:')
# Filter out all local addresses
ADDRS=$(echo "${ADDRS}" | egrep -v ':127|Scope:Host|Scope:Link')
if [ -z "${ADDRS}" ] ; then
return 1;
fi
fi
return 0
}
dns_has_local() { 
# Some magic to do tests 
if [ -n "${FAKE_HOST_RETURN}" ] ; then
if [ "${FAKE_HOST_RETURN}" = "true" ]; then
return 0;
else
return 1;
fi
fi
OUT=`LC_ALL=C host -t soa local. 2>&1`
if [ $? -eq 0 ] ; then
if echo "$OUT" | egrep -vq 'has no|not found'; then
return 0
fi
else 
# Checking the dns servers failed. Assuming no .local unicast dns, but
# remove the nameserver cache so we recheck the next time we're triggered
rm -f ${NS_CACHE}
fi
return 1
}
dns_needs_check() {
TMP_CACHE="${NS_CACHE}.$$"
RET=0
ensure_rundir
cat /etc/resolv.conf | grep "nameserver" | sort > ${TMP_CACHE} || return 0
if [ -e ${NS_CACHE} ]; then 
DIFFERENCE=$(diff -w ${NS_CACHE} ${TMP_CACHE})
echo "${DIFFERENCE}" | grep -q '^>'
ADDED=$?
echo "${DIFFERENCE}" | grep -q '^<'
REMOVED=$?
# Avahi was disabled and no servers were removed, no need to recheck
[ -e ${DISABLE_TAG} ] && [ ${REMOVED} -ne 0 ] && RET=1
# Avahi was enabled and no servers were added, no need to recheck
[ ! -e ${DISABLE_TAG} ] && [ ${ADDED} -ne 0 ] && RET=1
fi
mv ${TMP_CACHE} ${NS_CACHE}
return ${RET};
}
 
enable_avahi () {
# no unicast .local conflict, so remove the tag and start avahi again
if [ -e ${DISABLE_TAG} ]; then
rm -f ${DISABLE_TAG}
start avahi-daemon || :
fi
}
disable_avahi () {
[ -e ${DISABLE_TAG} ] && return
stop avahi-daemon || :
if [ -x /usr/bin/logger ]; then
logger -p daemon.warning -t avahi <<EOF
Avahi detected that your currently configured local DNS server serves
a domain .local. This is inherently incompatible with Avahi and thus
Avahi disabled itself. If you want to use Avahi in this network, please
contact your administrator and convince him to use a different DNS domain,
since .local should be used exclusively for Zeroconf technology.
For more information, see [http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)
EOF
fi
ensure_rundir
touch ${DISABLE_TAG}
}
if ! dns_reachable ; then
# No unicast dns server reachable, so enable avahi
enable_avahi
# And blow away the dns cache, so we force a recheck when the interface comes
# up again
rm -f ${NS_CACHE}
exit 0
fi
# Check if the dns needs checking..
dns_needs_check || exit 0
if dns_has_local ; then
# .local from dns server, disabling avahi
disable_avahi
else
# no .local from dns server, enabling avahi
enable_avahi
fi
exit 0
 
 
I can't confirm that re-installing 9.10 will address your issue but it did for me. I any one has any idea of how to address my DNS issue while using my wireless card I will appreciate any assistance.
 
Kalamata...

dear Kalamata,
thanks alot Kbut sorry i did not understand any thing i am not profisional in ubuntu
please if you have another lighter solution

---

### Post by en_mohamed on 2010-01-28
> **MelDJ said:**
> what kind of connection?

connection is ethernet

---

### Post by mikewhatever on 2010-01-28
> **en_mohamed said:**
> connection is ethernet

Can you open Applications->Accessories->Terminal and post the outputs of the following commands:

ifconfig

lshw -C network

---

### Post by en_mohamed on 2010-01-28
> **mikewhatever said:**
> Can you open Applications->Accessories->Terminal and post the outputs of the following commands:

ifconfig

lshw -C network
thanks master
i will do en shaa allahKand i will tell you dont go  far :D

---

### Post by en_mohamed on 2010-01-28
> **mikewhatever said:**
> Can you open Applications->Accessories->Terminal and post the outputs of the following commands:

ifconfig

lshw -C network

i have done what you said 
[COLOR=Red]first: ifconfig result[/COLOR]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[COLOR=Red]second :lshw -c netowrk[/COLOR]

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-e8003fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: memory:e8108000-e8109fff

---

### Post by en_mohamed on 2010-01-28
where you master [B]mikewhatever and other dears
[/B]

---

### Post by mikewhatever on 2010-01-28
> **en_mohamed said:**
> where you master [B]mikewhatever and other dears
[/B]

Looking for an answer, have patience. So far, the only thing I found was that it should work out of the box.
[http://hardware4linux.info/module/b44/](http://hardware4linux.info/module/b44/)

Edit: Can you post the output of the following (you may get no output):

lsmod | grep b44

or perhaps it will work after loading the module:

sudo modprobe b44

---

### Post by en_mohamed on 2010-01-28
> **mikewhatever said:**
> Looking for an answer, have patience. So far, the only thing I found was that it should work out of the box.
[http://hardware4linux.info/module/b44/](http://hardware4linux.info/module/b44/)

Edit: Can you post the output of the following (you may get no output):

lsmod | grep b44

or perhaps it will work after loading the module:

sudo modprobe b44
first: My tongue would like to thank.i thank you very much. God guide you to Islam
my connection is established.

second:please would you mid tell me what are the function of last two commands or tell me the problem and the explaination of the solution
second time thank you for you following -up and help

---

### Post by mikewhatever on 2010-01-28
Well, it looks like, for some reason, the kernel module (b44) needed for your ethernet card wasn't loaded. The last command I posted loads it, but we'll need to modify a file to ensure it loads automatically from now on. The file in question is /etc/modules

Run the following command **once**:

sudo echo "b44" >> /etc/modules

---

### Post by Kalamata on 2010-01-29
Hi en_mohamed,
 
I am sorry for the confusion. My solution to you was uninstall and reinstall Linux 9.10 since that address my issue on the ethernet and the wifi issue. The rest of the post was related to the issue that I have with the wireless card that it was working before reinstalling 9.10. Probably I should have posted that in a separate. Anyway I hope that you were able to address your issue, I am not a guru but if i find the solution to your issue I will make sure that you get it.

---

### Post by en_mohamed on 2010-01-29
> **Kalamata said:**
> Hi en_mohamed,
 
I am sorry for the confusion. My solution to you was uninstall and reinstall Linux 9.10 since that address my issue on the ethernet and the wifi issue. The rest of the post was related to the issue that I have with the wireless card that it was working before reinstalling 9.10. Probably I should have posted that in a separate. Anyway I hope that you were able to address your issue, I am not a guru but if i find the solution to your issue I will make sure that you get it.
daer Kalamata thanks  very much for trying to help me i have got the solution with the grace of allah then the grace of _mikewhatever_

---

