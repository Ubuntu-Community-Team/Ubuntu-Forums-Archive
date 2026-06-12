---
title: "pptp vpn Windows Server"
date: 2005-05-15
forum: Networking &amp; Wireless
---

### Post by mrh on 2005-05-15
Hi!

To use the computer system from my university (Muenster if anybody from Muenster is here) I need a VPN-connection.

I looked up this forum for pptp and vpn, but unfortunately all contributions are to complicated for me. I didnt't get it work. And I wasn't able to get the packages from "http://quozl.netrek.org/pptp/pptpconfig".

I got the pptpconfig.rpm from sourceforge.net and convertet it via alien and istalled them.

But what do I have to do now? How can I check if the installation was succesfull?  :confused: 

I would be happy if anybody could write a detailed installation-howto here. 
If i do not get vpn work, I have to switch back to windows.  :sad:

---

### Post by cwaldbieser on 2005-05-15
I managed to establish a VPN from my Ubuntu to our Window/Unix network at work using only tools I got from the repositories with apt-get.  I know I got the pptp-linux package.  I found some docs online that explained how to do this, though I don't have the link anymore.  Here is my explanation of the notes I took:

You need to create a file called /etc/ppp/peers/<PEER NAME>.  So for example, you could call it /etc/ppp/peers/school.  Put the following in that file:

```
#--------- /etc/ppp/peers/<PEER NAME> -------------
pty "pptp <IP ADDR> --nolaunchpppd"
name <LOGIN>
remotename PPTP
file /etc/ppp/options.pptp
ipparam <PEER NAME>
```

The stuff in the angle brackets needs to be filled in.  PEER NAME should match the file name.

Next you need to create or edit the file /etc/ppp/chap-secrets, and add the following entries:

```
#---------- /etc/ppp/chap-secrets -----------------
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
<LOGIN> PPTP <PASSWD> *
PPTP <LOGIN> <PASSWD> *
```

Now the command you need to issue to connect is:

```
$ sudo pon <PEER NAME>

```

This will make the connection, but your routing table still needs to be updated in order for you to do most useful stuff on your network.  Just issue something like:

```
$ sudo route add -net 10.0.0.0 netmask 255.0.0.0 dev ppp0 
```

You will neet to fill in your school's network/netmask info here instead of the 10.0.0.0/255.0.0.0 I used.

I didn't want to have to remember those commands all the time, so I threw them into a shell script in my path that I called "workvpn".  Now when I want to connect, I just type:
```

$ workvpn
```

and it prompts me for my Ubuntu password (because of the sudo calls to make the connection and change the routing table).  When I want to log off, I just issue:
```

$ sudo poff
```

Since /dev/ppp0 goes away at this point, I don't need to fool around with the routing table anymore.

It is no frills, and no GUI, but it is super-simple and it works for me.  I am sure there is probably some nice GUI that someone can point you to if you have a hard time making the configuration work.

Hope that helps!

---

### Post by mrh on 2005-05-16
First of all, many thanks for your detailed answer!!!  :grin: 

But I have still some problems.  :sad: 

File /etc/ppp/options.pptp does not exist. But there is a file ../options .
Using this, pon <name> works without promting an error.

But I still didn't understand the routing. The only information I got from my university is the name/ip of the vpn-router, but not the netmask.
And I found a description from my university for internal use: route add -host VPN-ROUTER gw VPN-GATEWAY dev eth0 
But using this route tells me that I can't reach (or something like this) the gateway.

Do you have an idea? 
	
Best regards
Marco

PS: I am using DSL and a router for network access. Maybe it's important. I forgot to mention this in my first thread.

---

### Post by cwaldbieser on 2005-05-16
Routing is the way that your computer knows where to send IP packets.  Basically, if two computers are on the same network, they can talk to each other directly.  If they are on different networks, they need to communicate over a gateway, which is just a computer with multiple network cards so it can talk to both networks.

When you establish the VPN, you are suddenly connected to a new network.  So your PC doesn't know how to talk to it directly.  By default, it is probably sending IP packets to your ethernet card, which is sending them out to the Internet where sites like [www.google.com](www.google.com) or [www.yahoo.com](www.yahoo.com) live.  Say that your school network was 192.168.xxx.xxx (only the last two numbers of the quad ever changed).  You need some way to tell your PC, if the IP address starts with 192.168, I want you to send those IP packets to my school network.

That is where the routing table comes in.  You can basically tell your PC to send the packets to an address or to a device.  In your case, when you create the VPN, a new "device" is created called something like /dev/ppp0 or /dev/ppp or something similar.  Do a 

```
$ ls /dev | grep ppp
```

after you are connected, and you should probably find it.  Another way to find out is to simply do 

```
$ ifconfig
```

after you are connected.  This will show you all your active network devices (including "lo", the loopback device, and probably "eth0" your ethernet device).  You should see a device called "ppp0" here, too.  That is your VPN "device".

Now notice that there are IP addresses next to the device names.  For example, on one of the lines after my eth0 device, I see:
```

inet addr:192.168.0.2
```

That is my PC's addess on my local network.  You ppp0 device also has an address.  This is your computer's address on the VPN.  So you have 2 IP addresses at this point.  This address can give you a clue as to what your school's network is.  If your address is 192.168.10.50, then the network would probably be 192.168.10.0, and the network would be 255.255.255.0.  You could do something like:

```
$ sudo route add -net 192.168.10.0 netmask 255.255.255.0 dev ppp0
```

This tells your computer, if an IP address starts with 192.168.10, then you have to send the packets to the ppp0 device.  Otherwise, try and match something else in the routing table.

Usually, the last line in the routing table is a default route, which says, if all else fails, try sending the packets here (in my case, "here" is to the eth0 device).

If you are still having trouble, connect to the VPN, then post the output of your ifconfig command back here, as well as the output of your route command.

---

### Post by mrh on 2005-05-17
oh, there is no ppp0 showing up  :confused: 

--- route  -------------------------------------------------------------------------------------------------
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.100   0.0.0.0         UG    0      0        0 eth0


---  ifconfig after pon -------------------------------------------------------------------------------------------------

eth0      Protokoll:Ethernet  Hardware Adresse 00:01:80:3C:FB:5F
          inet Adresse:192.168.0.77  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::201:80ff:fe3c:fb5f/64 Gültigkeitsbereich:Verbindung

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:18869 (18.4 KiB)  TX bytes:4379 (4.2 KiB)
          Interrupt:22 Basisadresse:0x8000

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:17466 (17.0 KiB)  TX bytes:17466 (17.0 KiB)

---

### Post by Raider on 2005-05-18
**cwaldbieser** 
One questiong before I am try to configure my vpn  ;-) 
How to edit config files throught the shell? :) At "Window Manager" I have no permissions.  O:)

---

### Post by cwaldbieser on 2005-05-18
Well, you need to have root permissions to edit those config files.  So you can just use sudo with your favorite editor at the console.  For example:

```
$ sudo vi rootfile
$ sudo nano rootfile
$ sudo gedit rootfile
$ sudo kedit rootfile
```

The only problem I have ever had using this method was with the editor, kate, under KDE.  I believe it is a known KDE bug, and work-arounds exist for it.

---

### Post by cwaldbieser on 2005-05-18
mrh,

I am not 100% sure why your ppp0 device is not showing up, but if you can't see it with ifconfig, then you are not connected.  I looked over the problem you said you were having with the options.pptp file being missing.  Try creating the file.  This is what mine looks like:

```
--- /etc/ppp/options.pptp ----
lock noauth nobsdcomp nodeflate
```

Make sure you change your peers file to point back to it instead of the normal options file!  I believe the normal options file has options for a normal ppp (dial up) connection.

Let me know how that works out.

---

### Post by slyride on 2005-05-19
Hello,
I have gone through the above steps and am stuck at the same place.  I issue the pon <my peer> minus the <> and it does not give any errors.  However when I use ifconfig, it does not show up a ppp0 connection.  TIA

---

### Post by cwaldbieser on 2005-05-19
Hmm,

Well, I am not sure what is wrong...  There is probably something slightly different that you guys need to set an option for.  One thing I did notice is that my ppp0 connection doesn't always show up right away-- sometimes I have to wait 5-10 seconds.

Here is a link to the pptp-linux home page with some general instructions, and links to a PHP GUI front end:

[http://pptpclient.sourceforge.net/#tryit](http://pptpclient.sourceforge.net/#tryit)

And this link from the same site trys to explain how to configure the connection similar to how I did it, though they are a little more comprehensive about what the various options mean:

[http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand)

If you get stuck on a particular point, let me know, and I will try to help if I can.  For now, I can only give you encouragement, and let you know that once you finally do hit on the right configuration, it is dead easy to connect from then on.

---

### Post by mrh on 2005-05-20
I already had the idea of creating my own /etc/ppp/options.pptp . But this wasn't successfull.

Maybe I try a a new clean installation next days.

Thanks so far for your detailed help! If I'am successfull I will report this here in the forum.

Bye
Marco

---

### Post by jdmazz on 2005-05-27
I had the same problems you seem to be experiencing. I have a linksys router, and fixed it by allowing PPTP VPN passthrough in the admin control panel for it. After that I just fiddled with the settings until it worked right.

---

### Post by Prefader on 2005-06-17
I'm having, basically, the same problem.  I have no /dev/ppp0, it's never created, and it doesn't appear in "ifconfig" after I do a 
```
sudo pon Steak
``` 

Very frustrating, as, to date, this is the *only* thing I can't get Ubuntu to do that I really want done.

Here's what I get from "pon Steak debug dump logfd 2 nodetach" :

```
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
name <NAME>           # (from /etc/ppp/peers/Steak)
remotename PPTP         # (from /etc/ppp/peers/Steak)
                # (from /etc/ppp/options.pptp)
pty pptp xx.xxx.xxx.xx --nolaunchpppd           # (from /etc/ppp/peers/Steak)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam Steak           # (from /etc/ppp/peers/Steak)
proxyarp                # (from /etc/ppp/options)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
noipx           # (from /etc/ppp/options)
using channel 11
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9a58484b> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
```

I also noticed that there is no /dev/pts/1.  No idea if that matters yet.

As always, any help is greatly appreciated.

---

