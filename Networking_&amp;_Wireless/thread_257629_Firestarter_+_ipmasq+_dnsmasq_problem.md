---
title: "Firestarter + ipmasq+ dnsmasq problem"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by bastupungen on 2006-09-14
Hello!
I have a problem with internet sharing, NAT. I run a server with several processes on it, and more too come. Security IS an issue too me. So is also usability. I'd rather use a program with a GUI-frontend then a CLI based program. If that means that im not a true-linux-user then so be it, I don't care.

So I found Firestarter to be an exellent choice. I fire up Firestarter, pardon the pun, and run DHCP through dhcpd3. It works good at first but my brother and others reported that internet was slow at first, or didn't work at all for the first minuates of trying to get it to work. Something i've never noticed in the linux computer. So i decided to try something else.

I installed both dnsmasq(dns+dhcpserver) and ipmasq(NAT-like program) and configured them mildly to fit my needs. I then also uninstalled firestarter and dhcpd3. Things work fine now, but then i also wan't a firewall and I thought that Firestarter did that just fine, i loved the Frontend of it. What I then find is that ipmasq stops working if I start firestarter, and ipmasq also have to be restarted if i've started and closed firestarter to work.

Why is this? do i have to open a port too be able to use Firestarter with ipmasq or disable some function, no dchp or internet sharing was NOT on in firestarter. Or does anyone know why Firestarter built-in internet sharing didn't work satisfactory? I've looked into the option of using iptables... it's probobly a really nice program with lots of options. But, seriously, I did not like the frontend. Its just too much for me to handle. To much to read and figure-out to be really worth it. If there is an GUI that uses iptables under it i could try that.

/Jonatan Sandberg Forsgren

---

### Post by tbonius on 2006-09-14
I love responding to this question.  Its my favorite.. because IP firewalling and NAT'ing can be made easier than most apps out there make it to be.  I recommend just using IPtables to do your dirtywork.  All you need is IPtables rules and some IPv4 forwarding:

[http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables](http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables)

IP forwarding is enabled by simply adding the following line to /etc/sysctl.conf:

```
#Enable packet forwarding
net.ipv4.ip_forward = 1
```

**Configuring a ruleset**

The following example shell script creates a basic ruleset that allows all traffic out from an internal network and only a couple of ports inbound. This script should be created and saved in a convenient and accessible place like /usr/local/sbin. Name this script whatever you would like to call it, like maybe firewall.sh

```
#!/bin/sh
IPTABLES='/sbin/iptables'

# Set interface values
EXTIF='eth0'
INTIF='eth1'

# enable ip forwarding in the kernel
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward

# flush rules and delete chains
$IPTABLES -F
$IPTABLES -X

#Enable masquerading to allow LAN internet access
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

#Forward LAN traffic from LAN $INTIF to Internet $EXTIF
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT

#Allowing access to the SSH server"
$IPTABLES -A INPUT --protocol tcp --dport 22 -j ACCEPT

#Allowing access to the HTTP server"
$IPTABLES -A INPUT --protocol tcp --dport 80 -j ACCEPT

# block out all other Internet access on $EXTIF
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,INVALID -j DROP
$IPTABLES -A FORWARD -i $EXTIF -m state --state NEW,INVALID -j DROP

#Redirect TCP port 25 to another internal computer
$IPTABLES -A FORWARD -i $EXTIF -d 10.0.0.5 -p tcp --dport 25 -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp --dport 25 -j DNAT --to-destination 10.0.0.6:25
```


This script assumes that we are using eth0 for our external interface and eth1 for the internal interface. If you have a different setup then adjust the script accordingly and change the EXTIF and INTIF values.

Once this is done, we need to setup a startup script for IPtables. We can do this by creating and editing a file called /etc/init.d/iptables.
```

#!/bin/sh
#
#This is a ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
# under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.
IPTABLES_SAVE="/etc/default/iptables-rules"
SAVE_RESTORE_OPTIONS="-c"
SAVE_ON_STOP="yes"
checkrules() {
if [ ! -f ${IPTABLES_SAVE} ]
then
echo "Not starting iptables. First create some rules then run"
echo "\"/etc/init.d/iptables save\""
return 1
fi
}
save() {
echo "Saving iptables state"
/sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
}
start(){
checkrules || return 1
echo "Loading iptables state and starting firewall"
echo -n "Restoring iptables ruleset"
start-stop-daemon --start --quiet --exec /sbin/iptables-restore -- ${SAVE_RESTOR
E_OPTIONS} < ${IPTABLES_SAVE}
}
case "$1" in
save)
save
echo "."
;;
start)
start
echo "."
;;
stop)
if [ "${SAVE_ON_STOP}" = "yes" ]; then
save || exit 1
fi
echo -n "Stopping firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a
if [ $a == nat ]; then
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT
/sbin/iptables -t nat -P OUTPUT ACCEPT
elif [ $a == mangle ]; then
/sbin/iptables -t mangle -P PREROUTING ACCEPT
/sbin/iptables -t mangle -P INPUT ACCEPT
/sbin/iptables -t mangle -P FORWARD ACCEPT
/sbin/iptables -t mangle -P OUTPUT ACCEPT
/sbin/iptables -t mangle -P POSTROUTING ACCEPT
elif [ $a == filter ]; then
/sbin/iptables -t filter -P INPUT ACCEPT
/sbin/iptables -t filter -P FORWARD ACCEPT
/sbin/iptables -t filter -P OUTPUT ACCEPT
fi
done
start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/ip
tables
echo "."
;;
restart)
echo -n "Flushing firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a
done;
start
echo "."
;;
*)
echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
exit 1
;;
esac
exit 0
```

Once we have saved this file, simply make the file executable and enable it to start when the system boots:
```

root@host # chmod +x /etc/init.d/iptables
root@host # update-rc.d iptables default
```

We now need to start the IPTables service so that we can load this ruleset:
```

root@host # /etc/init.d/iptables start
* Loading iptables state and starting firewall...	[ ok ]
* Restoring iptables ruleset    			[ ok ]

```

Now simply run the firewall.sh script to load the ruleset and test it out. When you have verified the rules are woking and traffic is being routed correctly, you can permanently save the rules by running the following command:
```

root@host # /etc/init.d/iptables save
* Saving iptables state...  				[ ok ]
```

Again, before blindly using the ruleset demostrated here, keep in mind that this is not the most secure ruleset. In this example we are allowing all traffic passed out. Ideally, we would filter outgoing traffic as well. From here you should be up and going, so enjoy.

---

### Post by bastupungen on 2006-09-14
.... Thanks for the response!
But, i feel that I have no idea what I am just doing. And this is a bad thing because i may have to alter the server setup from time to time. And then having this script that obviously does alot of things, and me not knowing exacly what, makes me unconfortable.

The fact that I am also controlling the server through VNC or ssh makes me even more uncomfortable using some script with iptables (a program I have a hard time understanding). One bad step and I might have to travel to the server, about 25km, to restart it.

Isn't there ANY other way that I can operate an firewall? that also works with some kind of NAT-like program. Like ipmasq that i know works, ATM.

If not then i guess i have to go with this and hope for the best, but then i'm disapointed. =(

---

### Post by bastupungen on 2006-09-17
Ok, since there didn't seem to be any better, or non buggy, way to do this i tried this out. And it worked, so far. I will have to wait and see if this one also stops working after a while, i hope not. 

Also, this configuration did not load up for me at a reboot, even though i did the /etc/init.d/iptables save command. I had to make the script run at start up by linking the script to a file in /etc/init.d/whatever and then using the update-ch.d command to make it run at boot. Then all i have to do when i wan't to open a new port is edit that file and then reboot or open it with the same command i wrote in the script. I can post all the commands I did if you wan't me to.

---

### Post by antivert on 2006-10-07
>root@host # chmod +x /etc/init.d/iptables
>root@host # update-rc.d iptables default

That was a typo, it should read 'defaults', which will make it start on bootup.

---

### Post by adamonline on 2006-12-30
Hello!  I've enountered a couple problems following this tut... For the record, I'm following it based off the steps outlined on the originating website, which is linked at the top of the post that contains this turorial...

First, at the step where it says to enter **/etc/init.d/iptables start**.  I got this message:

*Not starting iptables. First create some rules then run "/etc/init.d/iptables save"*.

I solved this by creating an empty file named /etc/default/iptables-rules.



Now when I type **sudo /etc/init.d/iptables start** at the command line, I get:

[I]Loading iptables state and starting firewall
Restoring iptables ruleset/etc/init.d/iptables: line 29: ${SAVE_RESTOR
E_OPTIONS}: bad substitution
[/I]

Does anyone know what's wrong?  This firewall solution seems like exactly what I need to do, and it's done how i want to do it, so if someone can help me get it working I'd really appreciate it :)

EDIT: Nevermind, the script has a line break in it that I had to remove on, yup, line 29!  I'll leave this post for future folks though, just in case...

-ADAM

PS.  Antivert, you're a lifesaver!  If i didn't read your correction, I probably would have gotten stuck even worse than I am now ;)

---

### Post by handy on 2006-12-30
This How-To by Frodon makes iptables so easy to use & configure, :)  I can't recommend it highly enough:

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

Take the trouble to read it through once & you will see what I mean... :-)

---

### Post by motin on 2008-03-05
Have you come anywhere in this matter?
I am attempting the same setup, except that I'll skip ipmasq since Firestarter sets up NAT. 

Have you tried using Firestarter with Internet Connection sharing but with DHCP disabled?

On top of that, you could probably configure dnsmasq for the DHCP needs and you should have a suiting setup. 

PS I just don't understand why the replies on your post so far has been about configuring iptables without a GUI...

---

### Post by jerricboy on 2008-03-05
> **tbonius said:**
> I love responding to this question.  Its my favorite.. because IP firewalling and NAT'ing can be made easier than most apps out there make it to be.  I recommend just using IPtables to do your dirtywork.  All you need is IPtables rules and some IPv4 forwarding:

[http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables](http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables)

IP forwarding is enabled by simply adding the following line to /etc/sysctl.conf:

```
#Enable packet forwarding
net.ipv4.ip_forward = 1
```

**Configuring a ruleset**

The following example shell script creates a basic ruleset that allows all traffic out from an internal network and only a couple of ports inbound. This script should be created and saved in a convenient and accessible place like /usr/local/sbin. Name this script whatever you would like to call it, like maybe firewall.sh

```
#!/bin/sh
IPTABLES='/sbin/iptables'

# Set interface values
EXTIF='eth0'
INTIF='eth1'

# enable ip forwarding in the kernel
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward

# flush rules and delete chains
$IPTABLES -F
$IPTABLES -X

#Enable masquerading to allow LAN internet access
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

#Forward LAN traffic from LAN $INTIF to Internet $EXTIF
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT

#Allowing access to the SSH server"
$IPTABLES -A INPUT --protocol tcp --dport 22 -j ACCEPT

#Allowing access to the HTTP server"
$IPTABLES -A INPUT --protocol tcp --dport 80 -j ACCEPT

# block out all other Internet access on $EXTIF
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,INVALID -j DROP
$IPTABLES -A FORWARD -i $EXTIF -m state --state NEW,INVALID -j DROP

#Redirect TCP port 25 to another internal computer
$IPTABLES -A FORWARD -i $EXTIF -d 10.0.0.5 -p tcp --dport 25 -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp --dport 25 -j DNAT --to-destination 10.0.0.6:25
```


This script assumes that we are using eth0 for our external interface and eth1 for the internal interface. If you have a different setup then adjust the script accordingly and change the EXTIF and INTIF values.

Once this is done, we need to setup a startup script for IPtables. We can do this by creating and editing a file called /etc/init.d/iptables.
```

#!/bin/sh
#
#This is a ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
# under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.
IPTABLES_SAVE="/etc/default/iptables-rules"
SAVE_RESTORE_OPTIONS="-c"
SAVE_ON_STOP="yes"
checkrules() {
if [ ! -f ${IPTABLES_SAVE} ]
then
echo "Not starting iptables. First create some rules then run"
echo "\"/etc/init.d/iptables save\""
return 1
fi
}
save() {
echo "Saving iptables state"
/sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
}
start(){
checkrules || return 1
echo "Loading iptables state and starting firewall"
echo -n "Restoring iptables ruleset"
start-stop-daemon --start --quiet --exec /sbin/iptables-restore -- ${SAVE_RESTOR
E_OPTIONS} < ${IPTABLES_SAVE}
}
case "$1" in
save)
save
echo "."
;;
start)
start
echo "."
;;
stop)
if [ "${SAVE_ON_STOP}" = "yes" ]; then
save || exit 1
fi
echo -n "Stopping firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a
if [ $a == nat ]; then
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT
/sbin/iptables -t nat -P OUTPUT ACCEPT
elif [ $a == mangle ]; then
/sbin/iptables -t mangle -P PREROUTING ACCEPT
/sbin/iptables -t mangle -P INPUT ACCEPT
/sbin/iptables -t mangle -P FORWARD ACCEPT
/sbin/iptables -t mangle -P OUTPUT ACCEPT
/sbin/iptables -t mangle -P POSTROUTING ACCEPT
elif [ $a == filter ]; then
/sbin/iptables -t filter -P INPUT ACCEPT
/sbin/iptables -t filter -P FORWARD ACCEPT
/sbin/iptables -t filter -P OUTPUT ACCEPT
fi
done
start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/ip
tables
echo "."
;;
restart)
echo -n "Flushing firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a
done;
start
echo "."
;;
*)
echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
exit 1
;;
esac
exit 0
```

Once we have saved this file, simply make the file executable and enable it to start when the system boots:
```

root@host # chmod +x /etc/init.d/iptables
root@host # update-rc.d iptables default
```

We now need to start the IPTables service so that we can load this ruleset:
```

root@host # /etc/init.d/iptables start
* Loading iptables state and starting firewall...	[ ok ]
* Restoring iptables ruleset    			[ ok ]

```

Now simply run the firewall.sh script to load the ruleset and test it out. When you have verified the rules are woking and traffic is being routed correctly, you can permanently save the rules by running the following command:
```

root@host # /etc/init.d/iptables save
* Saving iptables state...  				[ ok ]
```

Again, before blindly using the ruleset demostrated here, keep in mind that this is not the most secure ruleset. In this example we are allowing all traffic passed out. Ideally, we would filter outgoing traffic as well. From here you should be up and going, so enjoy.

can you do this with just one NIC connected to a switch?

---

### Post by jerricboy on 2008-03-06
It does work with just one nic. You just need to have the same value for both EXTIF and INTIF

> EXTIF= eth0
INTIF= eth0 

You'll need to change the /etc/network/interfaces to have two ip address assigned to it.

> iface eth0 inet static
address #you're static ip
netmask #you're netmask
gateway  #you're gateway ip
auto eth0

iface eth0:1 inet static
address 192.168.1.1
netmask 255.255.255.0
auto eth0:1


---

### Post by jerricboy on 2008-03-06
> **bastupungen said:**
> Hello!
I have a problem with internet sharing, NAT. I run a server with several processes on it, and more too come. Security IS an issue too me. So is also usability. I'd rather use a program with a GUI-frontend then a CLI based program. If that means that im not a true-linux-user then so be it, I don't care.

So I found Firestarter to be an exellent choice. I fire up Firestarter, pardon the pun, and run DHCP through dhcpd3. It works good at first but my brother and others reported that internet was slow at first, or didn't work at all for the first minuates of trying to get it to work. Something i've never noticed in the linux computer. So i decided to try something else.

I installed both dnsmasq(dns+dhcpserver) and ipmasq(NAT-like program) and configured them mildly to fit my needs. I then also uninstalled firestarter and dhcpd3. Things work fine now, but then i also wan't a firewall and I thought that Firestarter did that just fine, i loved the Frontend of it. What I then find is that ipmasq stops working if I start firestarter, and ipmasq also have to be restarted if i've started and closed firestarter to work.

Why is this? do i have to open a port too be able to use Firestarter with ipmasq or disable some function, no dchp or internet sharing was NOT on in firestarter. Or does anyone know why Firestarter built-in internet sharing didn't work satisfactory? I've looked into the option of using iptables... it's probobly a really nice program with lots of options. But, seriously, I did not like the frontend. Its just too much for me to handle. To much to read and figure-out to be really worth it. If there is an GUI that uses iptables under it i could try that.

/Jonatan Sandberg Forsgren

Firestarter wipes out all the Iptable rules every time it starts and restarts. 

Go to Edit>Preferences>Firewall then uncheck the Start/restart firewall boxes. You can then just add from the Policy.

---

