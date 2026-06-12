---
title: "can anyone help me with Deluge &amp; router port forwarding?"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by logos34 on 2008-08-28
I really need step by step assistance for bittorrent client and D-link di-604 router port settings, and Firestarter .  Down/up speeds appear normal, but iptables gui is going crazy, sucking on the cpu cycles.  Need to port forward, and I think I need to whitelist it too in firestarter, but need help--can't afford to compromise security.

The only guide on portforward.com is for di-604 and uTorrent.  But I want Deluge

anyone please help.  I hate networking

---

### Post by caljohnsmith on 2008-08-28
I can at least help you with your DI-604 router settings:
[LIST=1]
[*]First, in Deluge, go to Edit > Preferences, click the "network" tab, and make note of the port number where it says "TCP active port".
[*]I should mention at this point, in order to do port forwarding with your router, you need to set up your computer to use a static IP. You can use "ifconfig" to find your current IP LAN address, usually in the form 192.168.0.XXX, and then just set that as your static IP address in Network Manager. 
[*]Next go into your router's settings via [http://192.168.0.1](http://192.168.0.1)
[*]In your router settings, click "advanced", and where it talks about using a virtual server, click the "enabled" button, and then enter the fields with:
```
name = Deluge
private IP = the static IP you set
Protocol = tcp
Public port = Private port = the port you got from step #1.
Schedule = always
```
[/LIST]
That should be all you need to do to configure your router. About firestarter I don't know; the bottom line is you need to get firestarter to allow incoming connections to your computer on the TCP port number you found in step #1. But before you figure that out, are you aware that your router acts exactly like a firewall, and you really don't need any additional firewall software on your computer if you are behind a router? Personally I think you should simply disable firestarter since your router is your firewall.

Also, to test whether you have truly done everything necessary to open up the TCP port number from step #1, just go to [www.canyouseeme.org](www.canyouseeme.org) and type in your TCP port number. Keep in mind you need Deluge running at that time so Deluge will answer the incoming request. 

Anyway, good luck, let me know how it goes.

---

### Post by logos34 on 2008-08-28
Thanks! i think that may have done the trick.  At first I got:
> 
Error: I could not see your service on 75.63.7.134 on port (55823)
Reason: Connection timed outThen I added a rule/exception to firstarter>policy tab>inbound traffic policy>allow service port for>
> 
Allow service    Port    For
**unknown          55823 everyone**

(or instead of 'everyone' should I have chosen 'IP, host or network' ??? -- please verify, someone!)

Result:

> Success: I can see your service on 75.63.7.134 on port (55823)
Your ISP is not blocking port 55823Deluge is still up/downloading torrents, and I'm able to access the web, so I guess it's all ok.  Firestarter is back to normal 'Blue' icon ('Go'), nice not to have it lit up all the time with a mile long list of blocked hits on the random port chosen by Deluge.

Yes I'm aware of the router acting as a firewall (and a very effective one at that).  But I've never heard of disabling the default linux iptables firewall settings (firestarter is just a gui config frontend). 

I've restarted Deluge with 'random ports' unchecked, and the range set to 55823-55823, and it appears to be ok, up and downloading as usual.

Can't thank you enough.

I hope the 'anyone' firestarter setting is right or someone tells me either way.

I noticed that when I try to choose 'bittorent' in the dropdown box in firestarter it snaps to 6881-6889 default...if I put in mine it says 'unknown'. 

The router virtual server list now has this added to bottom: 
> 
Deluge    192.168.0.1**    TCP 55823/55823    alwaysAnd the router Home tab>DHCP now reads:
 
> Static DHCP Client List    
Host Name      IP Address      MAC Address
[my computer listed here]

Dynamic DHCP Client List
[other computer on the lan listed here]Hope that's it.

Hope I'm safe!

---

### Post by caljohnsmith on 2008-08-28
Glad Deluge is working for you now, logos34. :)

Something I'm confused about though, is why you have to manually open up that Deluge TCP port in your iptables with firestarter; when I open Deluge, it automatically opens the port it needs:
```
john@TECH5321:~$ [COLOR="Blue"]sudo netstat --tcp --listening --programs[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:60289                 *:*                     LISTEN      8099/python     
tcp        0      0 *:sunrpc                *:*                     LISTEN      4280/portmap    
tcp        0      0 localhost:ipp           *:*                     LISTEN      4958/cupsd      
tcp6       0      0 [::]:[COLOR="Blue"]60289[/COLOR]              [::]:*                  LISTEN      8099/python     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      7411/sshd       

```
Netstat shows my port 60289 TCP port is open, which is my Deluge's port. Also, I can go to canyouseeme.org and it shows "success" on getting a response from my computer on that port. If I do:
```
john@TECH5321:~/tmp$ [COLOR="Blue"]sudo iptables -L[/COLOR]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```
Iptables does not show any rule for my Deluge program, yet my 60289 port is indeed open. So I don't understand why you have to fiddle with your iptables, via firestarter, to get yours working. But if it works, I'm not going to argue with that. :)

---

### Post by logos34 on 2008-08-28
> Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:55823                 *:*                     LISTEN      26431/python    
tcp        0      0 *:8112                  *:*                     LISTEN      26443/python    
tcp6       0      0 [::]:55823              [::]:*                  LISTEN      26431/python


iptables says '(Policy DROP)' on input, forward and output

in Firestarter prefs set for 'Block broadcasts from external network' and to 'drop silently'

These were set up by Firestarter gui wizard.  Has worked fine for 2 + years

---

### Post by caljohnsmith on 2008-08-29
> **logos34 said:**
> iptables says '(Policy DROP)' on input, forward and output

in Firestarter prefs set for 'Block broadcasts from external network' and to 'drop silently'

These were set up by Firestarter gui wizard.  Has worked fine for 2 + years
OK, that explains it then; you've got your iptables configured to drop everything (via firestarter) by default, so that's why you have to manually open a port when you want to use a program like Deluge. :)

---

