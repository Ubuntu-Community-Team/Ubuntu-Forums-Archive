---
title: "[SOLVED] Limiting upload speed for non-local connections"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by spr- on 2008-10-13
**The solution can be found [here]("http://ubuntuforums.org/showthread.php?t=946624&page=2#post5962422")**

Hi,

I'm looking for a way to limit the upload speed on my Ubuntu machine, so that my upload link doesn't get saturated. However, I don't want to limit traffic within my LAN, so I can FTP/Samba locally with full speed. In a sense it's like:
```
if destinationIP not in 192.168.2.* then limit 500kbit/s
```
I've come across simple solutions like wondershaper (limits ALL traffic) and trickle (works for one program at a time). Reading about iproute2, tc, etc. just blew my mind.

I'm sure there must be a great lot of people that want this. 

Cheers, spr

**The solution can be found [here]("http://ubuntuforums.org/showthread.php?t=946624&page=2#post5962422")**

---

### Post by fwre01 on 2008-10-13
the easiest place would be to rate limit at your router, but im assuming you cant do that?

---

### Post by spr- on 2008-10-13
> **fwre01 said:**
> the easiest place would be to rate limit at your router, but im assuming you cant do that?
Nope. :(

---

### Post by iponeverything on 2008-10-13
```

tc qdisc add dev eth0 root handle 1: htb default 12
tc class add dev eth0 parent 1: classid 1:1 htb rate 100mbit ceil 100mbit
tc class add dev eth0 parent 1:1 classid 1:10 htb rate 500kbit ceil 500kbit
tc class add dev eth0 parent 1:1 classid 1:12 htb rate 50mbit ceil 100mbit
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src 0.0.0.0/0  flowid 1:10
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src  192.168.2.0/24 flowid 1:12
tc qdisc add dev eth0 parent 1:10 handle 20: sfq perturb 10
tc qdisc add dev eth0 parent 1:12 handle 30: sfq perturb 10

```

or something like that..

---

### Post by spr- on 2008-10-13
> **iponeverything said:**
> ```

tc qdisc add dev eth0 root handle 1: htb default 12
tc class add dev eth0 parent 1: classid 1:1 htb rate 100mbit ceil 100mbit
tc class add dev eth0 parent 1:1 classid 1:10 htb rate 500kbit ceil 500kbit
tc class add dev eth0 parent 1:1 classid 1:12 htb rate 50mbit ceil 100mbit
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src 0.0.0.0/0  flowid 1:10
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src  192.168.2.0/24 flowid 1:12
tc qdisc add dev eth0 parent 1:10 handle 20: sfq perturb 10
tc qdisc add dev eth0 parent 1:12 handle 30: sfq perturb 10

```

or something like that..

Wow, you really put some work into that. Thanks! I'll see whether that does the job.

---

### Post by spr- on 2008-10-13
Hmm, it seems to limit some LAN traffic as well. I think that is due to the fact I approach it by its host name. The router still routes it through the LAN, but it seems as if I'm coming from the outside world.
Would adding
```
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src  my.ip.here/24 flowid 1:12
```
help?

My ethernet if is indeed eth0, so that's not the problem. Thanks a lot already!

---

### Post by fwre01 on 2008-10-13
I havent read up on how tc works exactly, but it seemed to me confusing how it can classify your local subnet AFTER it classifys the 0.0.0.0/0 subnet. seems to me astho it will ignore the "tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src  192.168.2.0/24 flowid 1:12" line....perhaps not? perhaps it works through these in a specific order.

My thoughts were to use dest MAC address, therefore you could say anything with a dest MAC address of your router = rate limit at 500kbit, and ignore everything else.

---

### Post by spr- on 2008-10-13
> **fwre01 said:**
> I havent read up on how tc works exactly, but it seemed to me confusing how it can classify your local subnet AFTER it classifys the 0.0.0.0/0 subnet. seems to me astho it will ignore the "tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src  192.168.2.0/24 flowid 1:12" line....perhaps not? perhaps it works through these in a specific order.

My thoughts were to use dest MAC address, therefore you could say anything with a dest MAC address of your router = rate limit at 500kbit, and ignore everything else.
I reversed the filter order and now there's no limit when I friend of mine downloads something from my webserver. So, somehow, it matches my.ip.address or 192.168.2.* and puts no limit? I'm pretty confused. :)
But why check the MAC address of the router? It's never the destination? Not that I know that much about networking.. If what you say is right, how would I go about changing the commands?
Thanks everybody for helping me out.

If anyone else is reading this and wants to know how to remove **ALL** the rules:
```
sudo tc qdisc del root dev ethX
```

---

### Post by fwre01 on 2008-10-13
can you post the config you are now using?

just as a quick and dirty explanation...

when your server sends packets to your friends it will have their IP address as the destination, but it will also have your routers MAC address as the destination (i wont go into the details, but that is how it works)

If you could specify the destination mac address it would help simplify things, becasue you would no longer need to specify two subnets. (one of which is just a supernet of the other, which is confusing things further) you would only need to specify the dest mac address and the limit figure, and im assuming the rest of the traffic will get treated normally.

---

### Post by spr- on 2008-10-13
As for the tc config:
```
tc qdisc add dev eth0 root handle 1: htb default 12
tc class add dev eth0 parent 1: classid 1:1 htb rate 100mbit ceil 100mbit
tc class add dev eth0 parent 1:1 classid 1:10 htb rate 500kbit ceil 500kbit
tc class add dev eth0 parent 1:1 classid 1:12 htb rate 50mbit ceil 100mbit
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src 0.0.0.0/0  flowid 1:10
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src  192.168.2.0/24 flowid 1:12
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src  MY_IP/24 flowid 1:12
tc qdisc add dev eth0 parent 1:10 handle 20: sfq perturb 10
tc qdisc add dev eth0 parent 1:12 handle 30: sfq perturb 10
```

As for network config:
My network if is eth0. The local network is 192.168.2.*. The linux/server machine's ip is 192.168.2.100. My Windows machine is on 192.168.2.6. My external IP is MY_IP, which hostname is DYNAMIC_DNS. When I connect from my Windows machine to my server I connect to DYNAMIC_DNS, so it doesn't matter whether I connect from within the LAN or e.g. from school. The router presumably routes data through the LAN, but the server sees an external IP address, in this case, MY_IP or my friends IP. Every uplink should be limited to 500kbit/s, unless the server sees MY_IP or 192.168.2.* (because then it'll just be local, and the data won't sature my uplink).
Okay, that was a long story and I doubt whether that has many anything any clearer.

Edit: [What about an image?]("http://img101.imageshack.us/img101/8349/bandwidthlimitingcopycx9.jpg")

---

### Post by fwre01 on 2008-10-13
Just to help simplify this...

Firstly, remove the third tc filter, this is wrong, you shouldnt need to specify you public IP address anywhere.

next, if you want to limit you UPLOAD speed then you shouldnt be specifying the "ip src .... " you should be specifying the "ip dest .... " because on outbound connections the src will be 192.168.2.100 (i.e, your server) no matter what.

so it looks a bit more like this
```
tc qdisc add dev eth0 root handle 1: htb default 12
tc class add dev eth0 parent 1: classid 1:1 htb rate 100mbit ceil 100mbit
tc class add dev eth0 parent 1:1 classid 1:10 htb rate 500kbit ceil 500kbit
tc class add dev eth0 parent 1:1 classid 1:12 htb rate 50mbit ceil 100mbit
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst 0.0.0.0/0  flowid 1:10
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst  192.168.2.0/24 flowid 1:12
tc qdisc add dev eth0 parent 1:10 handle 20: sfq perturb 10
tc qdisc add dev eth0 parent 1:12 handle 30: sfq perturb 10
```

Then, run some tests from inside and outside your LAN, see how that helps. if it doesnt, post your config back, and maybe ill finally have a look at the tc man page. The tc man page seems a lot more interesting than this mock exam im doing atm thats for sure!! lol

---

### Post by spr- on 2008-10-13
Thanks a lot fwre01,

I'll have a look at this first thing in the morning. Looks like you have a point there. :)

Good night (for me at least),
spr

---

### Post by iponeverything on 2008-10-13
> **fwre01 said:**
> Just to help simplify this...

Firstly, remove the third tc filter, this is wrong, you shouldnt need to specify you public IP address anywhere.

next, if you want to limit you UPLOAD speed then you shouldnt be specifying the "ip src .... " you should be specifying the "ip dest .... " because on outbound connections the src will be 192.168.2.100 (i.e, your server) no matter what.

so it looks a bit more like this
```
tc qdisc add dev eth0 root handle 1: htb default 12
tc class add dev eth0 parent 1: classid 1:1 htb rate 100mbit ceil 100mbit
tc class add dev eth0 parent 1:1 classid 1:10 htb rate 500kbit ceil 500kbit
tc class add dev eth0 parent 1:1 classid 1:12 htb rate 50mbit ceil 100mbit
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst 0.0.0.0/0  flowid 1:10
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst  192.168.2.0/24 flowid 1:12
tc qdisc add dev eth0 parent 1:10 handle 20: sfq perturb 10
tc qdisc add dev eth0 parent 1:12 handle 30: sfq perturb 10
```

Then, run some tests from inside and outside your LAN, see how that helps. if it doesnt, post your config back, and maybe ill finally have a look at the tc man page. The tc man page seems a lot more interesting than this mock exam im doing atm thats for sure!! lol

I just woke up.. Thanks fwre01 I did mix up src and dst. I really didn't expect it work out of the box ;) -- I spend few days a couple of months ago with head in tc.

The third queue should remain its the default queue.

delete the queues:
```
tc qdisc del dev eth0 root


```print your queues:
```
tc filter show dev eth0

```
To see what is going with the queues:
```
tc -s -d qdisc show dev eth0
tc -s -d class show dev eth0
```

---

### Post by iponeverything on 2008-10-14
> 
Firstly, remove the third tc filter, this is wrong, you shouldnt need to specify you public IP address anywhere.


The third rule is optional -- not "wrong" -- It is quite handy for watching packet flow rates.

---

### Post by spr- on 2008-10-14
Alright! I got it working. I'm sorry to say that the script won't work without the filter with my public IP.
Thanks to iponeverything and fwre01!

Oh, and don't look at the comments and echoes, just makes it look like it's doing something.

```
#!/bin/sh
# Traffic shaping script
# ---------------------------------------------------------------------
# Limits upload speed to the outside world to 560kbit/s, leaving speeds
# within the LAN unaffected
# Only include the filter with the public IP if you access the machine
# through the LAN with its public IP
# ---------------------------------------------------------------------
# Thanks to iponeverything and fwre01
# ---------------------------------------------------------------------

# Starting with a clean slate
echo Removing any previously set rules...
        sudo tc qdisc del root dev eth0

echo Setting root qdisc...
        sudo tc qdisc add dev eth0 root handle 1: htb default 12

echo Setting bandwidth classes...
        sudo tc class add dev eth0 parent 1: classid 1:1 htb rate 100mbit ceil 100mbit
        sudo tc class add dev eth0 parent 1:1 classid 1:10 htb rate 560kbit ceil 560kbit
        sudo tc class add dev eth0 parent 1:1 classid 1:12 htb rate 50mbit ceil 100mbit

# Only include the filter with the public IP if you access the machine through the LAN with its public IP
echo Creating filters...
        sudo tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst YOUR.PUBLIC.IP.HERE/24 flowid 1:12
        sudo tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst 192.168.2.0/24 flowid 1:12
        sudo tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst 0.0.0.0/0  flowid 1:10

echo Finishing...
        sudo tc qdisc add dev eth0 parent 1:10 handle 20: sfq perturb 10
        sudo tc qdisc add dev eth0 parent 1:12 handle 30: sfq perturb 10
```

---

### Post by spr- on 2008-10-14
Oh, and do I call this script only once or at every boot?

---

### Post by fwre01 on 2008-10-14
Well done, Im glad you solved it. (and marked it as solved)

iponeverything, you may be right about the public.ip filter, could you explain how this works? i cant see a situation where the server will ever address packets with a destination of public.ip? the server will never see that address anywhere. also, why does it has a /24 mask? (that may just be a typo)

---

### Post by iponeverything on 2008-10-14
This is the basics as I understand it -- My main block in trying to learn this was thinking in pools and queues rather than streams.

```
                      _____ 1:10
                     /
            1: -----1:1
                     \_____
                            1:12

```
Create the root:  
```

tc qdisc add dev eth0 root handle 1: htb default 12

```

Define the Queues --
First the pool:
```

tc class add dev eth0 parent 1: classid 1:1 htb rate 100mbit ceil 100mbit

```

Then the Queues:
```

tc class add dev eth0 parent 1:1 classid 1:10 htb rate 560kbit ceil 560kbit
tc class add dev eth0 parent 1:1 classid 1:12 htb rate 50mbit ceil 100mbit

```

Put the packets into the correct Queue:
```

tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst 192.168.2.0/24 flowid 1:12
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst 0.0.0.0/0  flowid 1:10

```


Define my Queue algorithms:
```

tc qdisc add dev eth0 parent 1:10 handle 20: sfq perturb 10
tc qdisc add dev eth0 parent 1:12 handle 30: sfq perturb 10

```

---

### Post by iponeverything on 2008-10-14
> **spr- said:**
> Oh, and do I call this script only once or at every boot?

Yes call it once at boot time is all that you need.

I would just call it from /etc/rc.local -- but there are a lot of folks out there that will give there scripts more regal places to be invoked from.

Don't quite understand the thinking, it seems to imply *NIX politically correctness.. and any one that spent some time on some of the commercial flavors will realize that there is no such thing ;)

BTW -- If you are calling it from rc.local,  you will not need the "sudo"'s -- it will be ran as root.

---

### Post by AlexanderDGreat on 2010-09-17
Obviously this only works if you **DO NOT** have a Squid Server, File Server, Web Server, and other apps in your server, right?

---

### Post by iponeverything on 2011-01-07
it should work just fine, the arbitration is taking place a lower level.

---

