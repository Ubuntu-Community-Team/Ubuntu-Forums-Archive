---
title: "Kubuntu 7.04 connectivity issue"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by indigoshift on 2007-10-04
I ran a series of updates last week, and for some reason, this laptop won't see my internet connection.  Neither wired nor wireless.  Both devices seem active and perfectly fine.  They're even getting an IP address from my DHCP server.  But I can't ping anything, either in the network or out.

I'm not sure where to begin looking for the problem, either.  While I've been using Ubuntu for 2 years or so, this is my first experience with Kubuntu, and the differences have been enough to be classified as a learning experience.  Any nudges in the right direction will be greatly appreciated.  Thanks!

OS:  Kubuntu 7.04
Laptop:  Acer Aspire 5100 series
eth0:  Realtek RTL-8139/8139C/8139C+ (rev 10)
wifi0:  Atheros AR5005G

---

### Post by noob12 on 2007-10-04
Can you show us what you are getting from the DHCP?

```

ifconfig -a

route -n

cat /etc/resolv.conf

```

---

### Post by indigoshift on 2007-10-05
Okay, here we go:

ifconfig -a

```
ath0      Link encap:Ethernet  HWaddr 00:16:CF:29:A9:4A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:16:CF:29:A9:4A  
          inet addr:169.254.6.70  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:16:D4:16:53:EC  
          inet addr:10.200.0.124  Bcast:10.200.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe16:53ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13944 (13.6 KiB)  TX bytes:4790 (4.6 KiB)
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-29-A9-4A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2430 errors:0 dropped:0 overruns:0 frame:4702
          TX packets:174 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:227159 (221.8 KiB)  TX bytes:7968 (7.7 KiB)
          Interrupt:21 

```

route -n

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.200.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.200.0.1      0.0.0.0         UG    0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 ath0

```

cat /etc/resolv.conf

```
nameserver 10.200.0.2
```

---

### Post by noob12 on 2007-10-05
Your problem is that ath0 is up at the same time and there is a bogus route associated with it.
```

0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 ath0

```

Try seeing if things improve after running: ```
sudo ifconfig ath0 down
```  Disable wireless in the KnetworkManager as well if you are using that.

---

### Post by indigoshift on 2007-10-05
Argh.  No dice.

---

### Post by noob12 on 2007-10-05
Remember I'm pretty blind over here.  

Did you check that the interface is down and the bogus route gone after that? **route -n**

Can you ping local points like your router at 10.200.0.1 ?

Can you try and post the results?
```

ping -c 5 10.200.0.1

tail -10 /var/log/kern.log

```

---

### Post by indigoshift on 2007-10-05
route -n now returns:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.200.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.200.0.1      0.0.0.0         UG    0      0        0 eth0

```

Ping doesn't go through at all.  The tail of the kern.log shows:

```

Oct  5 09:26:55 aspire5100 kernel: [ 5628.292000] sda: Write Protect is off
Oct  5 09:26:55 aspire5100 kernel: [ 5628.292000] sda: Mode Sense: 23 00 00 00
Oct  5 09:26:55 aspire5100 kernel: [ 5628.292000] sda: assuming drive cache: write through
Oct  5 09:26:55 aspire5100 kernel: [ 5628.292000] SCSI device sda: 4029440 512-byte hdwr sectors (2063 MB)
Oct  5 09:26:55 aspire5100 kernel: [ 5628.296000] sda: Write Protect is off
Oct  5 09:26:55 aspire5100 kernel: [ 5628.296000] sda: Mode Sense: 23 00 00 00
Oct  5 09:26:55 aspire5100 kernel: [ 5628.296000] sda: assuming drive cache: write through
Oct  5 09:26:55 aspire5100 kernel: [ 5628.296000]  sda: sda1
Oct  5 09:26:55 aspire5100 kernel: [ 5628.296000] sd 1:0:0:0: Attached scsi removable disk sda
Oct  5 09:26:55 aspire5100 kernel: [ 5628.296000] sd 1:0:0:0: Attached scsi generic sg0 type 0

```

---

### Post by noob12 on 2007-10-05
Routes look right now.  No errors related to eth0 in the kernel log.  So the mystery continues.  

No answers. Only more questions.  Maybe one of these will lead to something.

What does ping say when it "doesn't go through" ?   Is there any error message?  Do any of the TX counts go up in the ifconfig output?  What about RX counts?

Are you connected to a normal router  or are you connected to another box doing internet connection sharing?  (Do you know that it normally respond to pings?)  What about 10.0.0.2, the DNS server -- is that responding to pings? (and does it normally?)

Are you running any firewall rules?  Check
```

sudo iptables -nL

```

---

### Post by indigoshift on 2007-10-08
Ping just says "unknown host".

It used to be able to pint 10.200.0.2, but it can't anymore.

It's attached to a little 4-port hub in my office here.  I thought it might've been a bad port, but it wasn't.

iptables -nL gives the following:

> Chain INPUT (policy ACCEPT)
target     prot opt source               destination
RETURN     0    --  0.0.0.0/0            0.0.0.0/0
moblock_in  0    --  0.0.0.0/0            0.0.0.0/0           state NEW

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
moblock_fw  0    --  0.0.0.0/0            0.0.0.0/0           state NEW

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
RETURN     0    --  0.0.0.0/0            0.0.0.0/0
moblock_out  0    --  0.0.0.0/0            0.0.0.0/0           state NEW

Chain moblock_fw (1 references)
target     prot opt source               destination
NFQUEUE    0    --  0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (1 references)
target     prot opt source               destination
NFQUEUE    0    --  0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (1 references)
target     prot opt source               destination
NFQUEUE    0    --  0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0
 


Which, I'll admit, doesn't make a lot of sense to me, as I've never seen this before.

---

### Post by noob12 on 2007-10-08
You shouldn't get unknown host when pinging with an ip address.  Use the ip address of the router first.

Not sure what you are doing with that firewall config.  Try putting the firewall down.  If you are using a GUI tool to manage the firewall set it to inactive.  If you are not running a GUI firewall control tool, use these commands below to set everything back to a clean slate.

```

# Get a root shell
sudo /bin/sh

# Within the root shell
# Flush all chains in all tables
for t in filter nat mangle raw; do iptables -t $t --flush; done

# Set policy to accept on all of the filter chains.  
for c in INPUT FORWARD OUTPUT; do iptables -t filter -P $c ACCEPT; done

# Remove any filter chains.
iptables -t filter -X

#Exit the root shell
exit

```

See if things improve.

---

### Post by indigoshift on 2007-10-09
Your root shell commands did the trick, man!  It's back to normal.  Thanks!

I've never messed with the firewall on this machine before.  Is it possible that an update may have modified those settings?

EDIT:  No, wait...I'll bet it was moblock.  I installed that to see how it worked, but never got around to configuring it properly.  Duh.

---

### Post by noob12 on 2007-10-09
OK.  Progress! 

Those commands I provided flushed the firewall rules out.  You don't want to have to do those each time.  Instead you want to find where the firewall rules are getting set in the first place and stop that or at least set them correctly.

Next task is to hunt that down.  

Did you install guarddog  or firestarter or another tool?

UPDATE:  missed your statement about moblock.  Never heard of that one.  If you remove it, remove it with a --purge option to get rid of configs. 
If you want a GUI, I'd suggest firestarter.  Personally I like to mess with command scripts directly, but firestarter is ok.  In all cases you have to be careful to configure the firewall properly or (hey) loss of connectivity may result.  :-)

---

### Post by indigoshift on 2007-10-09
> **noob12 said:**
> OK.  Progress!

More like Success, actually.  Problem solved.  Thanks again!

I uninstalled moblocker and it's working just fine now.  Haven't looked into firestarter; I might install it just to take it for a test drive.  I'll try not to kill my connectivity this time. :)

---

