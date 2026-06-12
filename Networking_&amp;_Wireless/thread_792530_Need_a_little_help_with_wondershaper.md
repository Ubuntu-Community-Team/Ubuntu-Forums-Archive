---
title: "Need a little help with wondershaper"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by w1z4rd on 2008-05-13
I was wondering if anyone could help me with this script, I need to shape down the speed on our gateway internet server with this script:

[http://lartc.org/wondershaper/](http://lartc.org/wondershaper/)

```
#!/bin/bash 

# Wonder Shaper
# please read the README before filling out these values 
#
# Set the following values to somewhat less than your actual download
# and uplink speed. In kilobits. Also set the device that is to be shaped.
DOWNLINK=800
UPLINK=220
DEV=eth0

# low priority OUTGOING traffic - you can leave this blank if you want
# low priority source netmasks
NOPRIOHOSTSRC=80

# low priority destination netmasks
NOPRIOHOSTDST=

# low priority source ports
NOPRIOPORTSRC=

# low priority destination ports
NOPRIOPORTDST=

# Now remove the following two lines :-)

echo Please read the documentation in 'README' first :-\)
exit

#########################################################

if [ "$1" = "status" ]
then
	tc -s qdisc ls dev $DEV
	tc -s class ls dev $DEV
	exit
fi


# clean existing down- and uplink qdiscs, hide errors
tc qdisc del dev $DEV root    2> /dev/null > /dev/null
tc qdisc del dev $DEV ingress 2> /dev/null > /dev/null

if [ "$1" = "stop" ] 
then 
	exit
fi

###### uplink

# install root CBQ

tc qdisc add dev $DEV root handle 1: cbq avpkt 1000 bandwidth 10mbit 

# shape everything at $UPLINK speed - this prevents huge queues in your
# DSL modem which destroy latency:
# main class

tc class add dev $DEV parent 1: classid 1:1 cbq rate ${UPLINK}kbit \
allot 1500 prio 5 bounded isolated 

# high prio class 1:10:

tc class add dev $DEV parent 1:1 classid 1:10 cbq rate ${UPLINK}kbit \
   allot 1600 prio 1 avpkt 1000

# bulk and default class 1:20 - gets slightly less traffic, 
#  and a lower priority:

tc class add dev $DEV parent 1:1 classid 1:20 cbq rate $[9*$UPLINK/10]kbit \
   allot 1600 prio 2 avpkt 1000

# 'traffic we hate'

tc class add dev $DEV parent 1:1 classid 1:30 cbq rate $[8*$UPLINK/10]kbit \
   allot 1600 prio 2 avpkt 1000

# all get Stochastic Fairness:
tc qdisc add dev $DEV parent 1:10 handle 10: sfq perturb 10
tc qdisc add dev $DEV parent 1:20 handle 20: sfq perturb 10
tc qdisc add dev $DEV parent 1:30 handle 30: sfq perturb 10

# start filters
# TOS Minimum Delay (ssh, NOT scp) in 1:10:
tc filter add dev $DEV parent 1:0 protocol ip prio 10 u32 \
      match ip tos 0x10 0xff  flowid 1:10

# ICMP (ip protocol 1) in the interactive class 1:10 so we 
# can do measurements & impress our friends:
tc filter add dev $DEV parent 1:0 protocol ip prio 11 u32 \
        match ip protocol 1 0xff flowid 1:10

# prioritize small packets (<64 bytes)

tc filter add dev $DEV parent 1: protocol ip prio 12 u32 \
   match ip protocol 6 0xff \
   match u8 0x05 0x0f at 0 \
   match u16 0x0000 0xffc0 at 2 \
   flowid 1:10


# some traffic however suffers a worse fate
for a in $NOPRIOPORTDST
do
	tc filter add dev $DEV parent 1: protocol ip prio 14 u32 \
	   match ip dport $a 0xffff flowid 1:30
done

for a in $NOPRIOPORTSRC
do
 	tc filter add dev $DEV parent 1: protocol ip prio 15 u32 \
	   match ip sport $a 0xffff flowid 1:30
done

for a in $NOPRIOHOSTSRC
do
 	tc filter add dev $DEV parent 1: protocol ip prio 16 u32 \
	   match ip src $a flowid 1:30
done

for a in $NOPRIOHOSTDST
do
 	tc filter add dev $DEV parent 1: protocol ip prio 17 u32 \
	   match ip dst $a flowid 1:30
done

# rest is 'non-interactive' ie 'bulk' and ends up in 1:20

tc filter add dev $DEV parent 1: protocol ip prio 18 u32 \
   match ip dst 0.0.0.0/0 flowid 1:20


########## downlink #############
# slow downloads down to somewhat less than the real speed  to prevent 
# queuing at our ISP. Tune to see how high you can set it.
# ISPs tend to have *huge* queues to make sure big downloads are fast
#
# attach ingress policer:

tc qdisc add dev $DEV handle ffff: ingress

# filter *everything* to it (0.0.0.0/0), drop everything that's
# coming in too fast:

tc filter add dev $DEV parent ffff: protocol ip prio 50 u32 match ip src \
   0.0.0.0/0 police rate ${DOWNLINK}kbit burst 10k drop flowid :1
```

Basically what I need to do is shape down eth0 so that is does not use more than 25KBs of speed.

We currently have a 512kbs line with 128kbs (upload), and when one of our departments downloads a large file on our one network it chokes the line. Im looking to use this script so that any downloads on the missbehaving network... will be shaped down to 25Kbs.

Im not sure what to do so I was wondering if anyone out there could assist me.

---

### Post by Jean-Marc Liotier on 2008-06-02
> Basically what I need to do is shape down eth0
> so that is does not use more than 25KBs of speed.

You have to enter your parameters in the script.

In your case you need to set the value of "UPLINK" to 25. Uplink and downlink speed are expressed in Kb/s (kilobits per second).

So in the script you should have something like :

DOWNLINK=512
UPLINK=25
DEV=eth0

---

### Post by Jean-Marc Liotier on 2008-06-02
Ooops sorry - I misread your question. What you want to shape to 25Kb/s is the download, not the upload. That is an unusual requirement but there you go : just set the DOWNLINK value to 25 too...

---

