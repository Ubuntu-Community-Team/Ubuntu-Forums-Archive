---
title: "Internet problems"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by charlvj on 2005-11-26
Hi,

I just upgraded to breezy and I am having wierd internet problems.

The ubuntu update stuff works - connects to ubuntu without a problem. I can ping [www.google.com](www.google.com) and other sites without a problem - the host name is resolved correctly. However, when I try to go to the page in  firefox it starts with "Connecting to www.google.com..." and then doesn't get any further. Gaim can't conenct either, and neither can Evolution to my mail server.

I tried doing wget [www.google.com](www.google.com) in the terminal and it shows the following:
"Looking up [www.google.com](www.google.com)... 1.0.0.0"
that is definately wrong. Then I also tried dig [www.google.com](www.google.com) and there again the name is resolved correctly.

Then just when I thought it couldn't get any wierder, [www.mozilla.org](www.mozilla.org) worked!

Please help. :-)

---

### Post by charlvj on 2005-11-26
Just to avoid misunderstanding...
Although [www.mozilla.org](www.mozilla.org) worked, nothing else worked. :-)

Thanks

---

### Post by inhetep on 2005-11-26
Hi,

maybe you want to check if you can get

wget 66.249.93.104 

(66.249.93.104 is the ip  of google.com)

to work.

If yes then u might have some DNS problems and might want to check out your network interface configuration.

---

### Post by charlvj on 2005-11-26
I am sure it will work with the IP address (on windows at the moment, so will try later).
I also suspected a dns problem, but dns works perfectly for ping, dig and apt-get (and [www.mozilla.org](www.mozilla.org) in firefox!).
For ap-get I can understand the the hostnames and their ip addresses are cached somewhere, but I could ping all the websites I tried and I didn't have any resolve issues.

---

### Post by inhetep on 2005-11-26
What does your /etc/resolv.conf say? Are you connecting through a router?
If you use the the name server adress of your router like 192.168.1.1 maybe you want to replace it with the name server address' of your provider. 

Do you use dhcp if yes maybe you can try to configure your interface manually. (if possible)

I had similar problems and after switching from dhcp to manually it worked.

---

### Post by mips on 2005-11-26
**Step1**
In the firefox address/URL space type "**about:config**" , scroll down to **network.dns.disableIPV6 = false** ,double click this line to change it to **true**.
In the above do NOT type in any quotes.

**Step2**
Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**[COLOR="Red"]#[/COLOR]alias net-pf-10 ipv6**

Save and reboot your PC.

---

### Post by charlvj on 2005-11-26
Hi
Thanks, I changed the ipv6 stuff and now firefox works.
However, Gaim and evolution still behaves the same way - no connection.

Regards

---

### Post by inhetep on 2005-11-26
Mips,

could you elaborate your steps a little bit more? Thanks

---

### Post by mips on 2005-11-26
[QUOTE=charlvj]Hi
Thanks, I changed the ipv6 stuff and now firefox works.
However, Gaim and evolution still behaves the same way - no connection.

Regards[/QUOTE]

Did you follow Step2 and RESTART your pc ?

---

### Post by charlvj on 2005-11-26
[QUOTE=mips]Did you follow Step2 and RESTART your pc ?[/QUOTE]
I did, yes.

---

### Post by mips on 2005-11-26
[QUOTE=inhetep]Mips,

could you elaborate your steps a little bit more? Thanks[/QUOTE]

Step1
-Start Firefox.
-Where you would usually enter the URL/Address (ie. [www.cnn.com](www.cnn.com)) type **about:config** and hit the Enter key.
-A page with a long list of Preverence Names, Status, Type & Value columns will appear.
-Above the column headers mention in the step before this is a **Filter:** field, enter **network.dns.disableIPV6** in this field and you will only see one line now on the whole screen.
-Double Click with your mouse on **network.dns.disableIPV6** and you will see the Status field has changed to **true** from false.
-Close Firefox


Step2
-On the Gnome Panel at the top of the screen select:
-Applications->Accessories->Terminal
-When the terminal has opened type this **sudo gedit /etc/modprobe.d/aliases** and hit the Enter key.
-You will now be prompted for your password, type your password and hit Enter.
-Press Ctrl+F keys to search and a little search window will open.
-In **The Search for:** field type **alias net-pf-10**
-It will now higlight the line that reads **alias net-pf-10 ipv6**
-You can close the search window now.
-Add a **#** character to the beginning of that line so it now reads **#alias net-pf-10 ipv6**
-On the gedit menu select File->Save or press Ctrl+S to do the same.
-Close gedit now.
-Shut your PC down and the restart it.

---

### Post by mips on 2005-11-26
[QUOTE=charlvj]I did, yes.[/QUOTE]

Ok, weird one this. 
What brand & model router are you using ?
Who is your ISP ? **Please provide a link to their site.**

Are you running any firewall, either on Ubuntu or your router ?

Lets see your **/etc/network/interfaces** file
Lets see your **/etc/resolv.conf** file
Lets see output of **ifconfig -a** command
Lets see output of **sudo mii-diag** command
Lets see output of **sudo mii-tool** command
Lets see output of **route -n** command

I have seen this problem before but can't remember where, yet!

---

### Post by charlvj on 2005-11-26
[QUOTE=mips]Ok, weird one this. 
What brand & model router are you using ?
Who is your ISP ? **Please provide a link to their site.**
[/QUOTE]
Using an ActionTec DSL Gateway (standard distribution with UKOnline broadband)
ISP is ukonline ([www.ukonline.co.uk](www.ukonline.co.uk))

[QUOTE=mips]
Are you running any firewall, either on Ubuntu or your router ?
[/QUOTE]
The router has a firewall. I tried setting the firewall down to the bare minimum, still didn't work.
Unless breezy installs a firewall as part of the main installation, I am not running one on this computer.  (Oh how I miss the service command!)

[QUOTE=mips]
Lets see your **/etc/network/interfaces** file
Lets see your **/etc/resolv.conf** file
Lets see output of **ifconfig -a** command
Lets see output of **sudo mii-diag** command
Lets see output of **sudo mii-tool** command
Lets see output of **route -n** command

I have seen this problem before but can't remember where, yet![/QUOTE]
eth1 is my wireless interface - disabled because I haven't worked out how to set up WPA encryption yet...)

**/etc/network/interfaces**
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp


**/etc/resolv.conf** 
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 212.135.1.36


**ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:06:5B:BC:89:60
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:febc:8960/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7853807 (7.4 MiB)  TX bytes:1758462 (1.6 MiB)
          Interrupt:11 Base address:0xec80

eth1      Link encap:Ethernet  HWaddr 00:02:2D:24:FF:5F
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2754048 (2.6 MiB)  TX bytes:2754048 (2.6 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


**sudo mii-diag**
Using the default interface 'eth0'.
Basic registers of MII PHY #24:  3000 782d 0041 6800 05e1 41e1 0007 2801.
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised 41e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   End of basic transceiver information.


**sudo mii-tool**
eth0: negotiated 100baseTx-FD, link ok
SIOCGMIIPHY on 'eth1' failed: Operation not supported


**route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by mips on 2005-11-26
Change your **/etc/resolv.conf** to:
```
#search domain.actdsltmp
#nameserver 192.168.0.1
nameserver 212.135.1.36
nameserver 195.40.1.36
```

and see what happens.

If it does not help change to a static IP configuration and see if that helps.

Please feed back.

---

### Post by charlvj on 2005-11-26
Evolution seems to be working now! Gaim is still having problems though.

This is only after taking down eth0 and bringing it back up again. maybe I missed something that will show after a reboot... till later.

Going out now, so will give more feedback tomorrow or so.
Thanks for the help!

---

### Post by charlvj on 2005-11-26
Hi, I tried with the nameserver change, still doesn't work. I also played around with static and dinamic IPs and it still doesn't work.

---

### Post by mips on 2005-11-27
Ok, I'm baffled as everything 'looks' fine.

Is it only Gaim giving you problems ?

---

### Post by towsonu2003 on 2005-11-27
you seem like very experienced (i.e. much more than me) so maybe 'offtopic' but worth mentioning: any existing firewall configuration (although evolution works)?? gaim will use ports that usual stuff won't...

---

### Post by mips on 2005-11-27
As far as I know Ubuntu does not have a firewall installed/configured by default. Firestarter is the most common one and can be found under Applications->System tools when installed. Can you disable your routers firewall completely and see what happens.

Maybe check to see if there is any IP Tables stuff configured... Long shot.

I know that certain applications like P2P filesharing stuff requires port forwarding on some routers to work but i have not heard of this being required for Gaim.

Are the Gaim setting correct ?

---

### Post by mips on 2005-11-27
Do you possibly have any proxies configured anywhere like Network Settings or Gaim settings etc

---

### Post by inhetep on 2005-11-27
Mips,

thanks for the reply, but what I meant was, what is the backgrond behind your changes. For instance u turn  IPv6 off? Why? Is this related to the fact that IPv6 doesn't look for a nameserver if it is autoconfigure things. If I am mistaken, I am sorry. Thanks for your thoughts on it.

---

### Post by mips on 2005-11-27
IPv6 is not commonly used except on ISP backbones and experimental environments. There are know problems with IPv6 and some consumer broadband devices, they just dont gel together. Why ? I do not know.

As for the DNS server issues Linux 'seems' to handle DNS differently than windows clients. DNS via a broadband router never seems to give problems on windows but with Linux this is not always the case therefore we add the DNS servers to the Linux config instead. Again I dont know why this is but I would like to know the cause/reason behind both these issues.

The above problems dont always occur but once you have eliminated the obvious you start looking at the black magic / voodo type stuff ;)

---

### Post by charlvj on 2005-11-27
Hi,

Thanks for all the attempts :-)

Yesterday it looked like synaptic also had problems with downloading a new package. Now that works. Gaim is still the problem though and it looks like it is just Gaim. (any other programs I can try?)

I checked my settings in Gaim - they all look fine. Also, I have two separate accounts set up in Gaim and none of them work. I don't have any proxy's configured for Gaim and I certainly didn't configure any for the computer itself. I don't know where to check this though...

I will quickly try disabling the router firewall...

---

### Post by charlvj on 2005-11-27
Mm, It looks like I can't diable the firewall on the router. It is set to its lowest setting though.

I think I'll try reinstalling Gaim. That is the only thing I can think of doing at the moment. If Gaim is going to be the only problem I might take it up in their forums.

Bye

---

### Post by charlvj on 2005-11-28
Ok, a few more things...

I tried to ping the server that Gaim uses for Yahoo, and the ping worked. After I pinged the server, suddenly Gaim could connect to Yahoo! WIerd.
So, I thought I'll ping the other server as well (a jabber server), and it didn't want to ping - resolved to 1.0.0.0

I also found that it is not just Gaim. Synaptic works _most_ of the time, however every now and then it gets stuck when downloading a new package, and I have to cancel the whole thing and start over, then it works. I wonder if this is related.

---

### Post by mips on 2005-11-28
I'm ](*,) here...

Show me your **/etc/modprobe.d/aliases** file please.
Are you still using a static IP ?

Also have a look at this [http://www.linuxquestions.org/questions/history/244026](http://www.linuxquestions.org/questions/history/244026)

---

### Post by charlvj on 2005-11-28
[QUOTE=mips]I'm ](*,) here...
[/QUOTE]
lol! I like that smiley! (or is smiley a wrong term for that one??)

[QUOTE=mips]
Show me your **/etc/modprobe.d/aliases** file please.
Are you still using a static IP ?

Also have a look at this [http://www.linuxquestions.org/questions/history/244026](http://www.linuxquestions.org/questions/history/244026)[/QUOTE]
I will show you the aliases file as soon as I get home...

That article sounds like the same problem I am having - I only have the router and not just the modem, but I suspect it will have the same modem inside. Will try the solution also. Thanks for that one!

Bye

---

### Post by charlvj on 2005-11-28
Yes!! That did it!

In /etc/resolv.conf the router's ip address was one of the nameservers, and it seems like it shouldn't be. So, I replaced it with 127.0.0.1  (as suggested by someone in the thread you pointed me to), and now it works. Also made an extra file to copy in a script on next startup. 

Thaks for all the help!

---

### Post by pmab on 2006-01-04
I have exactly the same problem, with same isp and router. 

disabling ipv6 helped with some of the stuff but it is still intermittant.

running gaim at startup doesnt work (1.0.0.0 thingy), however running amsn works, then when i retry gaim it connects.

connecting to irc seems to work some of the time, and then it'll try to connect to 1.0.0.0 maybe 2/3 of the time (argh)

Firefox/Mozilla have never had any issues.

---

### Post by mips on 2006-01-05
Where did you disable IPv6, globally or just in firefox ?
What steps have you followed so far ?

You can also stop IPv6 from start by renaming the module
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

Change your **/etc/resolv.conf** to:
```
nameserver 127.0.0.1
nameserver 212.135.1.36
nameserver 195.40.1.36
```

Hash out all other references to nameservers in this file and only have the ones listed above. If no luck hash out the nameserver 127.0.0.1 entry and try again.

Let us know how it goes. If it does not work then:
Lets see your **/etc/network/interfaces** file
Lets see your **/etc/resolv.conf** file

---

### Post by pmab on 2006-01-06
thanks for the advice, I had another mess around with the config, and I also upgraded the adsl modem firmware, which seems to have sorted it out.

---

### Post by GTroy on 2006-02-07
I couldn't connect with gaim, ever, even after disabling ipv6 which was a ver long time ago.  so I tried installing resolv.conf, then pump which wouldn't install.
I can telnet out, except to aim's server for gaim.  I cannot edit /etc/resolv.conf and there's nothing there.

I had such peace living without gaim, no I can't use any browsers!!!

I have an actiontec gt-701 wg modem/router 

please help!!

---

### Post by GTroy on 2006-02-07
I uninstalled resolv.conf and I have no problems except for gaim. *shrug*

---

### Post by mips on 2006-02-07
1. Is that the full Actiontec Model Number ?
2. Who is your ISP, weblink please ?
3. Lets see your **/etc/network/interfaces** file
4. Lets see your **/etc/resolv.conf** file
5. Lets **/etc/modprobe.d/aliases** file
6. Lets see output of **ifconfig -a** command
7. Lets see output of **route -n** command
8. Have you tried upgrading your firmware to the latest version ?

Did you have a have a look at **[http://www.linuxquestions.org/questions/history/244026](http://www.linuxquestions.org/questions/history/244026)**

---

### Post by GTroy on 2006-02-08
thank you mips, I'll post those things this saturday. I can't now because I've got a paper due along with a test.

---

### Post by moephan on 2006-02-11
FWIW, I was having a problem where gaim (and only gaim) wouldn't connect. When I went to preferences->Network and set proxy server to No proxy it started to connect. Then after about a week it stopped connecting again. I eventually went to Accounts->show more options, and set my AIM/ICQ Options->Auth host to: 64.12.161.153. The first time I tried this, it barfed an error, so I changed it back, and it worked! The next time I logged on, it wouldn't connect again. I changed Auth host back to 64.12.161.153, and now it always works (at least it has for a couple of weeks). I have no idea why it is so flaky, but that's what I did to get it working.

---

### Post by amethyst00 on 2006-06-23
Hello !

Ubuntu BB 5.10 was completely erratic on my desktop. I suspected a compromised system. The reason was a bad  connexion to the repositories. So several packets were probably corrupted. Correct parameters of the DNS service has fixed the problem.

Let us enjoy Ubuntu !

---

