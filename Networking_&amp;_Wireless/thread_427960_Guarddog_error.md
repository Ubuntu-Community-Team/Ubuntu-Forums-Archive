---
title: "Guarddog error"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Nihil Videmus on 2007-04-29
When I type "gksudo guarddog" in the terminal I get this massive error
> 
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/sbin
FILTERSYS=0
if [ -e /sbin/ipchains ]; then
FILTERSYS=1
fi;
if [ -e /usr/sbin/ipchains ]; then
FILTERSYS=1
fi;
if [ -e /usr/local/sbin/ipchains ]; then
FILTERSYS=1
fi;
# Check for iptables support.
if [ -e /proc/sys/kernel/osrelease ]; then
  KERNEL_VERSION=`sed "s/^\([0-9][0-9]*\.[0-9][0-9]*\).*\$/\1/" < /proc/sys/kernel/osrelease`
  if [ $KERNEL_VERSION == "2.6" ]; then
    KERNEL_VERSION="2.4"
  fi;
  if [ $KERNEL_VERSION == "2.5" ]; then
    KERNEL_VERSION="2.4"
  fi;
  if [ $KERNEL_VERSION == "2.4" ]; then
    if [ -e /sbin/iptables ]; then
      FILTERSYS=2
    fi;
    if [ -e /usr/sbin/iptables ]; then
      FILTERSYS=2
    fi;
    if [ -e /usr/local/sbin/iptables ]; then
      FILTERSYS=2
    fi;
  fi;
fi;
if [ $FILTERSYS -eq 0 ]; then
  echo "ERROR Can't determine the firewall command! (Is ipchains or iptables installed?)"
fi;
if [ $FILTERSYS -eq 1 ]; then
echo "Using ipchains."
echo "Resetting firewall rules."
ipchains -P output ACCEPT
ipchains -P input ACCEPT
ipchains -P forward ACCEPT
ipchains -F forward
ipchains -F input
ipchains -F output
fi
if [ $FILTERSYS -eq 2 ]; then
echo "Using iptables."
echo "Resetting firewall rules."
iptables -P OUTPUT ACCEPT
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -F FORWARD
iptables -F INPUT
iptables -F OUTPUT
fi;
echo "Finished."


Is this normal? The Guarddog GUI still launches and everything seems normal in it but I have a suspicion this could be the cause of my problems with torrent file sharing; all the ports that the program[s] use have been configured in guarddog to be allowed for TCP and UDP, and the ports have been forwarded on my router for both as well, yet I still get a DHT firewalled error in Azureus as well as slow and irregular downloads in any program.

Thanks in advance for any help.

---

