---
title: "Capping bandwidth/usage?"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by pburkind on 2008-03-24
Hello!

I am a soon-to-be-newbie Ubuntu user.  I am setting up Ubuntu on a machine for use in the common area of my house, for visitors.

My question revolves around capping downstream bandwidth or usage for the machine or for specific users.  I have a roommate who in the past has shown no willingness to restrain his internet use (watching free movies and listening to internet radio almost constantly), which is why I've removed access to my main computer from the household.

I'm hoping someone out there will be able to point me towards a package or set of instructions that will allow me to administer the amount of bandwidth available, or the total usage per unit of time (eg, x Mb/hr), etc.  I either want to force these accounts not to be able to pull data fast enough to handle streaming content (which seems unlikely, with the buffering capabilities built in to most web-based players nowadays), or (preferably) to enforce a limit of x megabytes per hour or something like that.

Let me know if you have any thoughts on handling this problem.  It is my first minor little network administration task as I move toward that career, so I am stoked to learn some behind-the-scenes things to do to make this kind of thing a reality.

Thanks in advance,
Pete

:lolflag:

---

### Post by SpaceTeddy on 2008-03-24
inbound traffic cannot be throtteled - since others send this to you, there is nothing to do about it. What you can control is the outgoing traffic. So if the internet connection of your housemate is going through an ubuntu/linux computer, you can limit the bandwidth anyone on the network gets...

basicially, what you do is use tc to create different bandwidith profiles, and then use iptables  to mark traffic to flow through specific profiles. There might be other solutions out  there, but this is the only one i ever got to work :(

as an example, here is a basic set of rules for tc. it will create two profiles, one with a streamcap of 800kbits/sec and one with 200Kbit/sec. please note that you will have to replace the ppp0 with the proper network device)

```
#delete old traffic shaping
/sbin/tc qdisc del dev ppp0 root 2> /dev/null

#create root device
/sbin/tc qdisc add dev ppp0 root handle 1: htb default 22

#create root class (this should be set to the speed of the network card)
/sbin/tc class add dev ppp0 parent 1: classid 1:1 htb rate 1024kbit ceil 1024bit burst 1024k

#create bandwidth classes (the sum of these cannot be bigger than the root class)
/sbin/tc class add dev ppp0 parent 1:1  classid 1:11 htb rate 200kbit ceil 500kbit burst 30k prio 2
/sbin/tc class add dev ppp0 parent 1:1  classid 1:12 htb rate 824kbit ceil 800kbit burst 1024k prio 1

#create fair share handles
/sbin/tc qdisc add dev ppp0 parent 1:11 handle 11: sfq perturb 10
/sbin/tc qdisc add dev ppp0 parent 1:12 handle 12: sfq perturb 10

#this sorts the pakets into the approriates classes - anything with handle 1 goes in 1:12, anything wth handle 2 goes in 1:11
/sbin/tc filter add dev ppp0 protocol ip parent 1: prio 1 handle 1 fw classid 1:12
/sbin/tc filter add dev ppp0 protocol ip parent 1: prio 2 handle 2 fw classid 1:11

```

together with this, you have to use some iptables rules to put the right connections/ips/ports into the right classes. in my example, only the webserver gets bound by the slow class (1:11), anything else goes through the fast one.

```
iptables --table mangle -A OUTPUT -j MARK --set-mark 0x1 
iptables --table mangle -A OUTPUT -p tcp -m tcp --sport 80 -j MARK --set-mark 0x2 
```

the first line will put anything in the fast class (handle 1 - so going into profile 1:12), the second rule will then overwrite only those what have a source port of 80 (so being sent from the local webserver) to handle 2 (going into class 1:11).
this will limit the bandwidth the server can use to 200kbit/sec...

i hope this is what you were looking for...

---

