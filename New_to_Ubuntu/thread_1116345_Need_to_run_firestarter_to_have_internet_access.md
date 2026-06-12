---
title: "Need to run firestarter to have internet access"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by ugriffin on 2009-04-04
I run Kubuntu 8.10, fully updated.

My problem lies in the fact that since I installed guarddog, iptools blocked ALL internet access. In the end, I ended up removing iptools out of spite (and the ubuntu-standard package), and I was surprised when my Kubuntu installtion kept on running. So, today, I installed iptools and ubuntu-standard back again, and installed firestarter fearing iptools would mess my system again.

So, my current problem lies in the fact that I now need to run firestarter to have internet.

1) Can I save my firestarter settings to iptools to save me the bother of starting firestarter for internet?

2) Can I remove iptools and ubuntu-standard? Is it safe?

3) Gimme any solution that might work, please!



Thanks in advance.

---

### Post by ibuclaw on 2009-04-04
To reset your iptables, use the **-F** flush option
```
sudo iptables -F
```

Personally, I'd just use **ufw** to setup my firewall. Presuming that your needs are very basic.

You just need to run three commands.
```
sudo ufw disable
```
```
sudo ufw default deny
```
```
sudo ufw enable
```

And now, by default, all remote inbound connections to your PC are blocked.
Although, this **won't block any service you request yourself**, so you can still browse the internet, fetch mail, talk online via Instant Messenger and other choirs without interference.

Regards
Iain

---

### Post by hyper_ch on 2009-04-05
Personally I think you don't need a firewall. So I'd get rid of all that added rules by issuing the command the previous poster gave to flush iptables and then get rid of all thsoe added firewall tools.

---

### Post by ugriffin on 2009-04-05
Sounds like the kind of commands I needed to have a working firewall and internet connection. Will reboot in a moment and see if it works.


:guitar:


EDIT: Nah, still need to run firestarter for my precious internet to work. Any more nifty command lines in for me?

---

### Post by ibuclaw on 2009-04-05
OK, can you post the output of this:
```
sudo iptables -L
```
So I (and others) can see how your firewall is setup, and to clarify that everything is dandy, just incase there is another application trying to control your firewall.

Regards
Iain

---

### Post by ugriffin on 2009-04-05
> 
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  ubuntu.local         192.168.1.255       
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST                                                       
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED                                                                          
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable                                                                       
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem                                                                             
nicfilt    all  --  anywhere             anywhere                               
srcfilt    all  --  anywhere             anywhere                               

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED                                                                          
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable                                                                       
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem                                                                             
srcfilt    all  --  anywhere             anywhere                               

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED                                                                          
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable                                                                       
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem                                                                             
s1         all  --  anywhere             anywhere                               

Chain f0to1 (3 references)
target     prot opt source               destination         
logdrop    all  --  anywhere             anywhere            

Chain f1to0 (1 references)
target     prot opt source               destination         
logdrop    all  --  anywhere             anywhere            

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10                                                                        
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED '                                       

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED '                            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED                                                                          

Chain logdrop (4 references)
target     prot opt source               destination         
logdrop2   all  --  anywhere             anywhere            limit: avg 1/sec burst 10                                                                          
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED '                                       
DROP       all  --  anywhere             anywhere                               

Chain logdrop2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `DROPPED '                            
DROP       all  --  anywhere             anywhere                               

Chain logreject (0 references)
target     prot opt source               destination         
logreject2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10                                                                         
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED '                                       
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset                                                                              
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable
DROP       all  --  anywhere             anywhere

Chain logreject2 (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `REJECTED '
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable
DROP       all  --  anywhere             anywhere

Chain nicfilt (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
logdrop    all  --  anywhere             anywhere

Chain s0 (1 references)
target     prot opt source               destination
f0to1      all  --  anywhere             localhost
f0to1      all  --  anywhere             ubuntu.local
f0to1      all  --  anywhere             192.168.1.255
logdrop    all  --  anywhere             anywhere

Chain s1 (1 references)
target     prot opt source               destination
f1to0      all  --  anywhere             anywhere

Chain srcfilt (2 references)
target     prot opt source               destination
s0         all  --  anywhere             anywhere



So, yeah.

---

### Post by ibuclaw on 2009-04-06
hmm... shot in the dark, but try this:
```
sudo aptitude purge firestarter ufw
```

Then
```

sudo iptables -F
sudo iptables -N INPUT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD DROP
sudo iptables -P INPUT ACCEPT

```

If you really are concerned and want a rudimentary protection:
```

sudo iptables -P INPUT DROP
sudo iptables -A INPUT -p tcp --tcp-flags SYN,ACK,RST SYN -j ACCEPT
sudo iptables -A INPUT -p icmp -j DROP
sudo iptables -A INPUT -m state --state NEW,INVALID -j DROP
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

```

If you follow the above, your firewall should now look like this (nice and clean):
> 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN 
DROP       icmp --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            state INVALID,NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


Now, time to save your config for future reference:
```
sudo iptables-save | sudo tee /etc/iptables.rules
```
That should get your network connection running just fine, and if it ever goes wrong at all again, to fix it will be:
```
sudo iptables-restore < /etc/iptables.rules
```

iptables is one of the most advanced firewalls out ever, period, and "dumbed-down" interfaces to it can easily break it.

If you are interested in Linux Iptables, bodhi.zazen has a brilliant tutorial: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Regards
Iain

---

### Post by ugriffin on 2009-04-07
Did it all. Iptables was configured just as you said it should. I saved the configuration file.....


When I rebooted, iptables was back to the huge jumble of problems it originally outputted, so I reinstalled ufw in order to disable my firewall and post this.


On a side note, firestarter failed to start, according to the Kubuntu start-up process, so maybe it's user related? Or what's wrong?


EDIT: Firestarter's gone from my comp, but before it went, on that bootup process, I decided to see how Kubuntu was booting up, and it reported Firestarter had failed to start. There's a clue there, but I can't think of anything other than user access privileges.

---

### Post by ibuclaw on 2009-04-07
> **ugriffin said:**
> Did it all. Iptables was configured just as you said it should. I saved the configuration file.....


When I rebooted, iptables was back to the huge jumble of problems it originally outputted, so I reinstalled ufw in order to disable my firewall and post this.


On a side note, firestarter failed to start, according to the Kubuntu start-up process, so maybe it's user related? Or what's wrong?


EDIT: Firestarter's gone from my comp, but before it went, on that bootup process, I decided to see how Kubuntu was booting up, and it reported Firestarter had failed to start. There's a clue there, but I can't think of anything other than user access privileges.

hmm... there must be another firewall interface installed that is messing about with it.

So does it work with the configuration I put up on the previous post; so you can connect and do all your internet activities without restriction?

If so, until you learn just what other package is trying to set its own configuration on your firewall you can always do this:
```
sudo gedit /etc/rc.local
```
And before the **exit 0** line:
```
/sbin/iptables-restore < /etc/iptables.rules
```
Ensure you save the file, and that should make the iptables configuration stick and keep stuck.

Regards
Iain

---

### Post by ugriffin on 2009-04-07
I discovered the solution. Apparently, guarddog wasn't removed properly by Adept.

My code:

```

sudo aptitude purge guarddog iptables
sudo aptitude install iptables ubuntu-standard

```


Worked beautifully. Thanks a lot man. I happen to 3D Model with blender, make some basic tunes with modplug tracker, and program in Game Maker (GML). Should you need help in any of those topics, feel free to PM me. 

Thanks a lot again. You saved my sanity.

---

