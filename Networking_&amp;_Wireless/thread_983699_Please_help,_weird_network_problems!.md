---
title: "Please help, weird network problems!"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Phases on 2008-11-15
Ok. I installed a new server yesterday and am having some problems. I put ubuntu server 8.04 on it, and then loaded ubuntu-desktop. 

Now. 

My www works fine (its a webserver, superstickphase.com).. I got all that restored and stuff. 

I can SSH into it fine. 

synergy is working.

But, my ftp quit working (got it to work once last night), and none of my web browsers will work, and my eggdrop bot isn't launching. 

When I try to FTP in, connection refused. 
When I try to open FF, says its already running, kill process or reboot. There is no process, reboot doesn't help.
When I try epiphany I get "Unable to connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply,the reply timeout expired, or the network connection was broken.
When I go into "network tools" and drop down to eth0 in "Network Device", i can see the address and netmast and stuff, and when I click "configure" i get an error: "the interface does not exist, check that it is correctly typed and that is correctly supported by your system"

Please help me with where to look. 

/etc/network/interfaces/ says:

# loopback
auto lo
iface lo inet loopback

# eth0
auto eth0
iface eth0 inet static
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.99
broadcast 192.168.2.255

Please help this is driving me nuts.

---

### Post by Bluebell392 on 2008-11-16
I sometimes had problems like yours and sometimes the problem is solved by checking firewall rules. Simply issue these commands at a terminal window: ```
sudo iptables -L INPUT
sudo iptables -L OUTPUT
``` This will show what rules are in effect, as well as the policy for each. If the policy for one of the rules is DROP or REJECT, then you fix it by issuing these commands:```
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
```

---

### Post by Phases on 2008-11-16
Thanks for the reply,

Chain INPUT (policy ACCEPT)
target prot opt source   destination

....


Chain OUTPUT (policy ACCEPT)
target prot opt source    destination

---

### Post by Phases on 2008-11-16
Ok. I fixed the browser problem. It appears when I copied over my home dir from the old server that was the problem. So I chown'd it back to me and now both browsers work. And my bot works, and the stuff that wasn't staying on the panel after I added them works. So :P

ftp still now working - connection refused. Everything in proftpd.conf is fine as far as I can tell, i checked it several times, and had it connect last night.

---

### Post by Phases on 2008-11-16
....and for some reason synaptic showed proftpd as uninstalled. 

It was installed.

So I marked for install and it works now! 

I think that's most everything.. except now after the reboot with the profile fix, i've lost a few of my var/log's in log manager.. the 3 different mail ones. Do they maybe have to create an entry first to show.. ? hmm..

---

