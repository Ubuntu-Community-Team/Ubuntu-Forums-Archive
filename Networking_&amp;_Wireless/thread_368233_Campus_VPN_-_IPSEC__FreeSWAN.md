---
title: "Campus VPN - IPSEC / FreeS/WAN"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by aqualad on 2007-02-23
On my campus there is very little to no linux support for the VPN, though there is an extremely outdated guide that pointed me towards FreeS/WAN and ipsec located [here]("http://helpdesk.kent.edu/flashzone/").  Hopefully the guide has enough information to allow a newer version of FreeS/WAN to be configured with IPSec.

I'm currently using kernel 2.6.17-10 and I haven't patched any kind of IPsec stuff into my kernel, though I know I might have to.  I checked and the current version of FreeS/WAN says it's compatible with my kernel, but anything older than v2.3 of FreeS/WAN isn't, so that rules out the possibility of installing the version described in the guide.

I have ipsec installed, but I don't understand how to configure the file ipsec-tools.conf files.  I followed [this]("https://help.ubuntu.com/community/IPSecHowTo") guide up to the ip-sec.conf file.

If someone could help me, I would definitely pass my gained knowledge onto someone who could update the webpage.  So by helping me you may be helping my entire campus, or at least helping me convince more people to switch to linux :]

Thanks in advance

---

### Post by koenn on 2007-02-23
FreeSWAN is dead - they stopped in 2004. The project was replaced by OpenSWAN. I think you should ask de TechSupport if they're still actually using FreeSWAN or an other IPsec implementation. 
You might suggest to them to switch to an SSL-VPN implementation (such as openVPN : [http://openvpn.net/](http://openvpn.net/) ) to accomodate Linux users. IPsec was never really succesfull because it proved hard to configure, especially for home users behind NAT routers. SSL-VPN fills that gap. 

Alternatively, i see that for Mac OS X they propose PPtP (Point to Point Tunneling Protocol) - a Microsoft proprietary VPN protocol (which has nothing to do with IPsec, so that's the 2nd reason i doubt you'd get the IPsec to work)

There's a PPtP package for ubuntu & it works quite well. I'm not sure it's in the repo's already, you should check (universe ?). Otherwise, you can get it by

1- add ```
deb http://quozl.netrek.org/pptp/pptpconfig ./  
``` to  /etc/apt/sources.list, and ```
sudo apt-get update
```

2- install package :
```
sudo apt-get install pptp-linux
sudo apt-get install pptpconfig
```

```
3- configure vpn : 
sudo pptpconfig
```

To connect to your univ's vpn, you run pptpconfig, select the connection you've configured in step 3, and click "start". It need to run as root because it will want to temporarily change some config files (eg for DNS and routing). 
You can make a launcher on the desktop or in a panel that runs the command 
"gksudo pptpconfig"

---

### Post by aqualad on 2007-02-23
Awesome suggestion btw, I've made alot of progress so far.

First I connect to the network, run
```
(sudo pptpconfig &)
```
And then it starts.  I've already put in all of the information I believe I need to (allowing for automatic DNS). It authenticates me and everything, but here's the print out:
```
Using interface ppp0
pptpconfig:monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/2
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
```

I'm connecting via Client to LAN

I'm almost there, any help now would be really appreciated

---

### Post by koenn on 2007-02-23
> Cannot determine ethernet address for proxy ARP
This is supposedly a warning that you can ignore.
Does it just hangs there or do you get something like

```
local  IP address ....
remote IP address .....
...
pptpconfig: routes added to remote networks
... 
pptpconfig: DNS changes made to /etc/resolv.conf
**pptpconfig: connected**
```

---

### Post by aqualad on 2007-02-24
As far as I know it just hangs, though once I think it did say something about local & remote ip, and something about the DNS

I'm pretty sure it just hangs though.  How long should I wait before I can cancel it?

Should I be connecting via Client to tunnel or all to tunnel?

Really appreciate the help

---

### Post by Ptero-4 on 2007-02-24
aqualad. If you dont get it trough with pptp-linux. You might try getting an old Mac with OSX and conecting it to the campus link and then you can conect your linux box to the mac. In that way you can get past the M$ only restriction and relay the network conection to your computer.

---

### Post by aqualad on 2007-02-25
I would, but I don't actually live on campus.  Good idea though :]

I'll post some more data about what it's doing when I get to school Monday and have time to try it out again.  As far as I know it just says whatever about the Proxy ARP then hangs.  Is there any way to get a verbose print out or some kind of debugging?

---

### Post by koenn on 2007-02-25
> Should I be connecting via Client to tunnel or all to tunnel?
I guess it depends on how the vpn is set up on the other site. You could  try "everything through tunnel' to start with because it's the least complex. If that works , you can try to narrow it down, eg to client-to-LAN

You could experiment with the various encryption/authentication mechanisms to see which one works. 
However, the "Cannot determine ethernet address for proxy ARP" seems to appear after succesfull authentication, and the next step would be that the vpn gateway at the other end gives you an ip address, a route,  etc. that matches the LAN you want to connect to. 
Maybe that is what is not happening. 

In the pptpconfig GUI there's a "miscellaneous" tab where you can tyrn on "debug info"

---

### Post by aqualad on 2007-02-25
Cool, I'll check that, though I'm not sure whether it will just print out more info in the terminal or if it'll make a .log file somewhere.

Here's a file that might be somewhat useful in determining what kind of encryption the school uses:

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>PPTP</key>
	<array>
		<dict>
			<key>ConnectByDefault</key>
			<true/>
			<key>EAP</key>
			<dict/>
			<key>IPSec</key>
			<dict/>
			<key>PPP</key>
			<dict>
				<key>AuthName</key>
				<string></string>
				<key>CCPEnabled</key>
				<integer>1</integer>
				<key>CCPMPPE128Enabled</key>
				<integer>1</integer>
				<key>CCPMPPE40Enabled</key>
				<integer>1</integer>
				<key>CommRemoteAddress</key>
				<string>vpn.kent.edu</string>
				<key>UserDefinedName</key>
				<string>Flashzone</string>
			</dict>
		</dict>
	</array>
</dict>
</plist>

```

---

### Post by aqualad on 2007-02-26
Okay, i'm at school and here's what's up, it does this long sequence of stuff before finally saying that it disconnected. Here's the print out:

[IMG]http://i17.tinypic.com/40bgqyd.jpg[/IMG]

More info coming soon. Also, post anything else that would help in trouble shooting.

---

### Post by koenn on 2007-02-26
What you have here is failing authentication (the green stuf that times out after which the "modem hangs up").
This worked before : you had
> CHAP authentication succeeded
What did you change ? Are you sure you've put in correct usrname and password ?

---

### Post by aqualad on 2007-02-28
Okay, I fixed the password, I must have mistyped it at some point in one of my attempts:
[IMG]http://i17.tinypic.com/2sbphyp.png[/IMG]

At this point it just hangs. I let it sit for a while and nothing happened.

A friend of mine told me that it might be something concerning mppe and not having proper support in my kernel.  He uses gentoo though and said he wasn't sure about ubuntu.

Thanks for the help

---

### Post by aqualad on 2007-02-28
```
eth1      Link encap:Ethernet  HWaddr 00:13:02:45:4C:E9  
          inet addr:131.123.183.168  Bcast:131.123.183.255  Mask:255.255.252.0
          inet6 addr: fec0::9:213:2ff:fe45:4ce9/64 Scope:Site
          inet6 addr: 2002:837b:343d:9:213:2ff:fe45:4ce9/64 Scope:Global
          inet6 addr: fe80::213:2ff:fe45:4ce9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68297 errors:0 dropped:28094 overruns:0 frame:0
          TX packets:481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2960294 (2.8 MiB)  TX bytes:33517 (32.7 KiB)
          Interrupt:185 Base address:0xa000 Memory:52000000-52000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.0.88.255  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1486  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:96 (96.0 b)  TX bytes:102 (102.0 b)


```

A little more information.

That's what my interfaces look like when pptpconfig has done everything in the post above and is just hanging.

I entered the route 10.0.0.1/22 but as far as I can tell it makes no difference (the /22 is based off of the subnet address of the eth1)

---

### Post by koenn on 2007-02-28
From what i see, i gather that you 
- pass CHAP authentication
- get MPPE enabled, 
but during the configuration of the ppp link something seems to go wrong.
```

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.0.88.255  P-t-P:10.0.0.1
```

this says the remote vpn concentrater is 10.0.0.1, and your address is 10.0.88.255
however, the pptp config debug output shows your address should be 10.0.138.255.

You're also given DNS servers by the remote vpn gateway 131.123.246.1 and 131.123.252.2
you can check if they appear in your /etc/resolv.conf.
If they're there, at least that part is working.

Other than the ip address descripancy, i can see nothing wrong. The only part your missing is pppconfig setting new routes. The fact that it doesn't do this may have to do with the "wrong" ip address. 

Are you trying this with a "Everything through tunnel" config ? I think that would be the easiest.

If you add routes, I'd try 10.0.0.0/16. The subnetmask of eth1 has no bearing on the ppp interface.

So, to summarize:
I think you're really close, 
there's something weird with the network config, 
and i don't see why that would happen.

---

### Post by George M. Harkin on 2007-03-13
This seems to be an issue with Eft.

Here is a thread describing it: [http://www.nabble.com/hangs-after-%22Cannot-determine-ethernet-address-for-proxy-ARP%22-t2726677.html]("http://www.nabble.com/hangs-after-%22Cannot-determine-ethernet-address-for-proxy-ARP%22-t2726677.html")

I'm having the same ARP issues. I can get things to work when I add the route for the VPN's subnet manually:
```
route add -net 192.168.0.0 netmask 255.255.255.0 dev ppp0
```

Guess we'll just have to wait until Fawn

---

