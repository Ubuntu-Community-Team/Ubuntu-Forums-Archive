---
title: "Help with opening ports in iptables"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by duelle on 2007-06-22
I need to have several port ranges open for torrents and games through Wine, but I can't understand anything in iptables. I've tried installing Firestarter and configuring that to forward ports but to no avail. It's not my router as my IP is the DMZ Host and there aren't any problems in Windows.

---

### Post by Matt Yun on 2007-06-22
Try going through this tutorial here:  [http://ubuntuforums.org/showthread.php?t=57111](http://ubuntuforums.org/showthread.php?t=57111).  It seems a little complicated, but all you have to do is follow the directions.

It would help if you let us know what ports you need open.

---

### Post by duelle on 2007-06-22
I need ports 6112-6119 open (Warcraft 3) and 49200 for BitTorrent. Sorry for not saying.

Edit: I tried the script and after every question I get "[: XX: ==: unexpected operator", 'XX' being a number (line number, I'm assuming). Also, how would I configure this for the ports I want open, assuming I can get it to work?

---

### Post by Matt Yun on 2007-06-22
Here, forget that complicated script from the post above.  I've written you a simple one instead, based on a LinuxQuestions Wiki article:  [A basic firewall configuration suitable for a workstation.]("http://wiki.linuxquestions.org/wiki/A_basic_firewall_configuration_suitable_for_a_workstation")

First, open a terminal and enter: **gksudo gedit /etc/init.d/firewall**.  Copy and paste the following:


```
#!/bin/sh
# /etc/init.d/firewall
# from http://wiki.linuxquestions.org/wiki/A_basic_firewall_configuration_suitable_for_a_workstation

set -e

iptables="/sbin/iptables"
modprobe="/sbin/modprobe"

load () {

 echo "Loading kernel modules..."
 $modprobe ip_tables
 $modprobe ip_conntrack
 $modprobe iptable_filter
 $modprobe ipt_state
 $modprobe iptable_nat
 echo "Kernel modules loaded."

 echo "Loading rules..."
 $iptables -P FORWARD DROP
 $iptables -P INPUT DROP

##### PORTS #####
# comment out the ones you don't need

### ftp
#$iptables -A INPUT -p tcp -m tcp --destination-port 21 -j ACCEPT

### ssh
#$iptables -A INPUT -p tcp -m tcp --destination-port 22 -j ACCEPT

### http
#$iptables -A INPUT -p tcp -m tcp --destination-port 80 -j ACCEPT

### NetBIOS (Windows Networking, Samba)
#$iptables -A INPUT -i eth1 --protocol tcp --dport 137 -j ACCEPT
#$iptables -A INPUT -i eth1 --protocol tcp --dport 139 -j ACCEPT

### for Duelle: World of Warcraft
$iptables -A INPUT -p tcp -m tcp --destination-port 6112:6119 -j ACCEPT

### for Duelle:  Bittorrent
$iptables -A INPUT -p tcp -m tcp --destination-port 49200 -j ACCEPT


##### BLOCK OUT INTRUSION #####
$iptables -A INPUT -i eth0 -m state --state NEW,INVALID -j DROP
$iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP


###### DEFAULTS #####
 $iptables -A INPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT
 $iptables -A INPUT -s 127.0.0.1 -j ACCEPT
 echo "Rules loaded."

}

flush () {

 echo "Flushing rules..." $iptables -P FORWARD ACCEPT
 $iptables -F INPUT
 $iptables -P INPUT ACCEPT
 echo "Rules flushed."

}

case "$1" in

 start|restart)
   flush
   load
   ;;
 stop)
   flush
   ;;
 *)
   echo "usage: start|stop|restart."
   ;;

esac
exit 0


```

Save and exit gedit.  While still in the terminal, enter:  **sudo chmod 755 /etc/init.d/firewall && sudo /etc/init.d/firewall start && sudo update-rc.d firewall defaults**

"chmod 755" gives execution permissions for the script (so you can run it).  

"/etc/init.d/firewall start" actually runs the script.  If you are having problems with the firewall, then do "/etc/init.d/firewall stop".  If you make a change to the script and then want to reload it, do "/etc/init.d/firewall restart".

"update-rc.d firewall defaults" adds the firewall script to your bootup routine.  If you want to remove the script from booting, then do "update-rc.d firewall remove".

---

