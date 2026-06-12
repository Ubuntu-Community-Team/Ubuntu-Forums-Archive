---
title: "some questions about using tc"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Phate99 on 2008-09-09
Hi, 

I'm in need of some help for a few (hopefully) simple questions about the usage of tc, specifically for limiting bandwidth usage.

I'm fairly new to linux, but have managed to put together a basic file server running ubuntu, using mdadm, and samba to share the files.  Now what I want to is limit the network speed to certain IP addresses on my network.  Why?  Well, my main computer, and the server are connected to a 100Mbit switch, which connects to the rest of the network on a 10Mbit link.  The internet connection is also on this 10Mbit link.  So, when the file server is being used, the 10Mbits is saturated, and I get a poor internet connection.  So if I could limit connection speed to ~9Mbit for the rest of the network, and not limit the speed to my main computer, I'll have no problems.

I've done some reading, and came up with the idea that tc will do this for me.  I've even come up with a script, and have a vague understanding of what the various options in it do.  (basically I modified the script I found here: [http://osdir.com/ml/linux.network.routing/2001-06/msg00075.html](http://osdir.com/ml/linux.network.routing/2001-06/msg00075.html) )  I was hoping someone who knows more about this will tell me if it's even close to what I want.

Here's the script:
```
## ROOT Class
tc qdisc add dev eth0 root handle 12: cbq bandwidth 100Mbit avpkt 1400

tc class add dev eth0 parent 12: classid 12:1 cbq bandwidth 100Mbit \
   rate 100Mbit allot 1514 weight 10Mbit maxburst 20 avpkt 1400

## FLOWs
# 129.128.198.198 (unbounded)
tc class add dev eth0 parent 12:1 classid 12:11 cbq bandwidth 100Mbit \
   rate 100Mbit allot 1514 weight 10Mbit maxburst 20 avpkt 1400

# other (bounded)
tc class add dev eth0 parent 12:1 classid 12:12 cbq bandwidth 100Mbit \
   rate 9Mbit allot 1514 weight 900Kbit maxburst 20 avpkt 1400 bounded

# unbounded class for local traffic
#tc class add dev eth0 parent 12:1 classid 12:300 cbq bandwidth 10Mbit \
#   rate 3Mbit allot 1514 weight 300Kbit prio 3 maxburst 20 avpkt 1400

## QDISCs
tc qdisc add dev eth0 parent 12:11 sfq quantum 1514b perturb 15
tc qdisc add dev eth0 parent 12:12 sfq quantum 1514b perturb 15

## FILTERs
# unbounded class
tc filter add dev eth0 parent 12:0 protocol ip u32 \
   match ip src 123.123.123.198 flowid 12:11

# bounded classes
tc filter add dev eth0 parent 12:0 protocol ip u32 \
   match ip dst 123.123.123.0/197 flowid 12:12
tc filter add dev eth0 parent 12:0 protocol ip u32 \
   match ip dst 123.123.123.199/255 flowid 12:12

```

Is this even close?

Now, assuming it is (and here's the dumb question) what do I do with this script??  Nowhere have I found instructions on what exactly you do with it.  Does it just run through the terminal, or go in some folder somewhere?

Other question, if I do something to completely mess things up, how can I reset the interface to the default basic fifo setting?

Thanks for any help! :)

---

### Post by Phate99 on 2008-09-09
Ok, so I figured out how to reset things:
```
tc qdisc del dev eth0 root
```

And figured out that you can use a bash script to input the commands (which I'm not sure how to do), but that means that the commands can just be put into the terminal (I think...). So I gave it a shot.

Each command inputs with no errors, and if I try the same command twice RTNETLINK says the file already exists, which is good I think..  There was a file transfter (or transfers) going when I input everything, so I could see if anything happened.  There was no change in bandwidth usage :( 

So one of 4 things I guess:
1. Changes only apply to new connections.  Seems unlikely...
2. Each connection is limited to 9Mbps, so more than one still saturates the line.  Shouldn't be the case, as the filter should filter all packets to the limited class, which is limited to 9Mbits total?
3. This script actually shapes incoming connection speed.. This is what the original script was supposed to do, and I wasn't sure what needed to be changed to make it limit outgoing...
4. It's just plain wrong :(

Or something else...

Thoughts?

---

### Post by Phate99 on 2008-09-10
Ok, I figured it out.  My filters were wrong.  Apparently the slashes don't let you specify an IP range.  I'm not sure how to specify a range, so I just created filters for 100-255 excluding 198.  Placing a sudo in front of every command, and removing the comments gets you a script that you can run through terminal.

Just for future reference :-P

---

