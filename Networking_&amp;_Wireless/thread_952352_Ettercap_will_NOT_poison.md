---
title: "Ettercap will NOT poison"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by starwiz on 2008-10-19
Okay, well.  I just installed ubuntu again :P
So, I install all of my updates, and then xchat.
Once I install ettercap, I do the ip forward thing.

Well... Try

I type this into the terminal

/proc/sys/net/ipv4/ip_forward

And I get....

bash: /proc/sys/net/ipv4/ip_forward: Permission denied

So, I found somewhere on the internet, to type

cat /proc/sys/net/ipv4/ip_forward

And I get.....

abyss-@abyss--laptop:~$ cat /proc/sys/net/ipv4/ip_forward
1

So far... A success.






Next, I open up ettercap
Click sniff
Then the top one
eth0 (That IS the one im using now :P)
Then, Hosts
Scan for hosts
After that.
Hosts
Host list
So I see 2 ips

192.168.1.1
And 192.168.1.103

So, I put the xxxx.1.1 in target 1 list
And xxxx.1.102 in target 2 list
then.
Mitm
arp poison
remote poison thing

At the bottom, it says started sniffing
THEN
Plugins, manage the plugins
chk_poison


And get this :(

ctivating chk_poison plugin...
chk_poison: Checking poisoning status...
chk_poison: No poisoning at all :(

---

### Post by starwiz on 2008-10-19
Bump...
Need help

---

### Post by atatistcheff on 2008-10-19
I'm not an ettercap guru - I actually came here trying to get help to make it perform an SSL mitm.  However, the arp poisoning is working fine for me.  The only thing is that ettercap will do the forwarding itself without ip_forwarding turned on in the kernel.  In fact, one post I saw said this would create duplicate forward packets as both the kernel and ettercap try to forward.  My  /proc/sys/net/ipv4/ip_forward contains 0 instead of 1.  I followed the same steps as you did.  

I have found that running the repoison_arp plug-in also keeps the poison going when the real gateway sends out its arps.  

So try turning off ip_fowarding in your kernel and see if that helps.

---

### Post by starwiz on 2008-10-19
Alright, ill try.  Thanks for the advice.

---

### Post by starwiz on 2008-10-19
:(
Nothing happened.
It actually said it needs to be forwarded.  But, from what I have read, not many people have gotten it.

---

### Post by John mech on 2012-01-03
Did someone solve this issue? I'm having the same problem

---

