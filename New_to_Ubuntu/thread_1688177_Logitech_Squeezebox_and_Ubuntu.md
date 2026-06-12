---
title: "Logitech Squeezebox and Ubuntu"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Fukinagashi on 2011-02-15
Hi all. I'm a newbie on Ubuntu.
I've recently bought a Logitech Squeezebox Touch.
To get acquainted I attached it to my work PC running Windows 7 and SqueezeBoxServer (SBS) SW and all worked fine.
Now I want to use it on my home PC running Ubuntu:

1. I downloaded SBS for Ubuntu and installed it.
2. I went of [http://localhost:9000](http://localhost:9000) and setup the SBS the make it see my music.
3. I attached the SB to my router.
4. On SB in advanced settings I chosen Networking -> Choose Network -> Connect to ethernet network. When connecting to the network the SB says "connected".
5. I added the UDP and TCP ports in the Ubuntu Firewall.

Still the SB and the SBS seems not to communicate.

In the SB diagnostic I read:

mysqueezebox.com 
 DNS failed 
  
 Ping 
 Can't ping 
  
 TCP port 3483 
 Can't connect 
  
 TCP port 9000 
 Can't connect 
  
 mysqueezebox.com registration 
 - 
  
 Squeezebox Server 
 192.168.232.115 
  
 Library name 
 Arcobaleno 
  
 Ping 
 Can't ping 
  
 TCP port 3483 
 Can't connect 
  
 TCP port 9000 
 Can't connect 
  
 Current player 
 Arcobaleno 
  
 Player Type 
 Local

I tried everything but I still cannot make the SB working on my home PC!
Help please!!

---

### Post by surfer on 2011-02-15
are you on a local network? did you configure your gateway in the network settings of your squeezebox?

i have been using squeezebox for several years (my first squeezebox is even from slimdevices) on ubuntu. everything works nicely!

oh, you say your squeezebox does not connect to the server? hmmm... strange. could you post your firewall settings?

---

### Post by Fukinagashi on 2011-02-15
are you on a local network?
yes

did you configure your gateway in the network settings of your squeezebox?
no (with Win 7 I did not configure anything on the SB to make it work)
how should I do on the SB? 

could you post your firewall settings?
sure. could you tell me the command line needed to get what you need?

Thanks in advance.

---

### Post by surfer on 2011-02-15
the network settings are (on the SB touch)
Settings -> Advanced -> Networking -> Choose Network -> Connect to wireless/ethernet Network -> ...

if you do this with DHCP, the server should set the gateway correctly. if you enter everything by hand, make sure you enter the ip address of your router as gateway.

as for the firewall settings:
```
$ sudo iptables -L
```

although i do not use a firewall... so i may not help there...

---

### Post by surfer on 2011-02-15
do you know the ipaddress of your SB touch? can you ping it from the server?

---

### Post by Fukinagashi on 2011-02-15
> **surfer said:**
> do you know the ipaddress of your SB touch? can you ping it from the server?

Yes. I tried to ping from the Ubuntu console but it does not work.

---

### Post by surfer on 2011-02-15
so does your SB touch get a DHCP or a static ip address? if it's a dynamic address, did you get it from your router?

could you post your server's network configuration?
```
$ ifconfig
```

and also
```
$ sudo iptables -L
```
might help.

---

### Post by Fukinagashi on 2011-02-15
> **surfer said:**
> so does your SB touch get a DHCP or a static ip address? if it's a dynamic address, did you get it from your router?

I guess it's DHCP.

could you post your server's network configuration?
```
$ ifconfig
```and also
```
$ sudo iptables -L
```might help.

I will as soon as I'm at home this evening.

Thanks again for your support!

---

### Post by Fukinagashi on 2011-02-15
And here we go:

in ifcofig.txt the output of the command line ifconfig
in iptables_before.txt the output of the command sudo iptables -L before opening ports in firewall
in iptables_after.txt the output of the command sudo iptables -L after opening ports in firewall


Here follows the SBS report (Settings -> Information)

 		 		 	 		Squeezebox Server Status
 		 		 			 	 		Version: 7.5.3 - r31792 @ Mon Jan 24 07:13:35 PST 2011
 	 		Hostname: FEYNMAN
 	 		Server IP Address: 192.168.232.115
 	 		Server HTTP Port Number: 9000
 	 		Operating system: Debian - EN - utf8 
 	 		Platform Architecture: i686-linux
 	 		Perl Version: 5.10.1 - i486-linux-gnu-thread-multi
 	 		MySQL Version: 5.1.41-3ubuntu12.9
 	 		Total Players Recognized: 0
 	  		 
 	
 	 	
     	 	 	 		 		 	 		Library Statistics
 		 		 			 		 			Total Tracks: 64
 		 			Total Albums: 4
 		 			Total Artists: 4
 		 			Total Genres: 4
 		 			Total Playing Time: 4:11:01

---

### Post by surfer on 2011-02-15
FEYNMAN? a fellow physicist?

your ifconfig says that the network interface (eth0) for the local network 192.168.232.0/24 is not up. but that is the subnet of your SB server (how is that?!) and probably your SB touch.

can you bring eth0 up?
```
sudo ifup eth0
```

---

### Post by Fukinagashi on 2011-02-15
> **surfer said:**
> FEYNMAN? a fellow physicist?

your ifconfig says that the network interface (eth0) for the local network 192.168.232.0/24 is not up. but that is the subnet of your SB server (how is that?!) and probably your SB touch.

can you bring eth0 up?
```
sudo ifup eth0
```


done.
it says:

Ignoring unknown interface eth0=eth0.

Feynman: yes the physicist!

---

### Post by Fukinagashi on 2011-02-15
At last something happened!
I tried to attach the SB directly to the PC with an ethernet cable.
On the SB I asked


Choose Network
Connect to ethernet network


It failed but allowed me to enter the IP address, the subnet mask, the gateway and DNS.
I entered the information found in my Ubuntu SBS Settings -> Information.
I attached back the SB and PC to the router and now the SB seems to see MyMusic!!!



I'm sure there still be something wrong.
For example in the diagnostics I read:


mysqueezebox.com
DNS failed


Ping
Can't ping


TCP port 3483
Can't connect


TCP port 9000
Can't connect


At the moment it is a step forward anyway!
Probably I cannot use the full potential of the SB (cannot hear radios?).
Don't know.


Anybody can explain all this stuff?

---

