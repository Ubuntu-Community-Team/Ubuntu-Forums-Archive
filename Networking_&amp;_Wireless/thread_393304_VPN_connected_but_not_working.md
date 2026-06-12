---
title: "VPN connected but not working"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by megalomaniac on 2007-03-25
Hi all,
Ok, so the one thing that's stopping me from switching permanently to Ubuntu  is that I need to connect to a Windows VPN and remote desktop into a machine at work.

I've tried in vain to get this up and running in Ubuntu by trawling through the forums, documentation and Google, but with no success. The situation at the moment is that I've installed Network Manager along with the pptp stuff and it ***seems*** to connect to the VPN ok. However, I cannot see anything on the windows network through 'Network Servers' (although I can see in the network itself) and I cannot connect to my required machine through the 'Terminal Server Client' and 'RDP' (it times out eventually), nor can I ping anything internal to the network, I just get:
```
ping: sendmsg: Operation not permitted

--- 192.168.240.51 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3009ms
*ping: sendmsg: Operation not permitted*.
```Any help would be hugely appreciated although I don't have the greatest understanding of VPN's and general networking so go easy on me :).

Cheers

---

### Post by megalomaniac on 2007-03-26
It's probably worth pointing out that this works perfectly in Windows with all the default VPN settings and Windows Remote Desktop Connection, and I'm trying this on Ubuntu 6.10

---

### Post by megalomaniac on 2007-03-27
Anyone got any ideas? Tips? Tricks? Anything?

---

### Post by megalomaniac on 2007-03-29
I'm really stuck here, can't anyone help?

Thanks

---

### Post by DrewUVM on 2007-04-01
I'm trying to do the same thing. If you find details, please post 'em.

Thanks,

Drew

---

### Post by megalomaniac on 2007-04-03
> **DrewUVM said:**
> I'm trying to do the same thing. If you find details, please post 'em.

Thanks,

Drew

Will do, don't forget to post if you get sorted too :).

Looking round the forums it seems M$ VPNs are a big sticking point for a lot of people, I wonder if it'll be better in Feisty?

---

### Post by rolando on 2007-04-08
I have used nm-applet to successfully connect to my University VPN for sometime now.  

TO set this up is very simple.

1. Make sure nm-applet is running in the gnome-panel.

2. Left click on it and select VPN Connections >

3. Click configure VPN.

4. Stick your stuff in (same as you would in windows, i.e. dont touch anything, just type the name of the server to connect to.

5. Once you have done that Left click on the  nm-applet again, select VPN connections > and select whatever you named it.

6. Watch it connect.

7. Go check your IP address at whatsmyipaddress.com or whatever it is.

8. Do what you do on your VPN.

Footnote 1:
Mine only works for around 10 seconds, but I have recently changed ISPs and will be approaching them very soon, as to why this is happening, whilst my old ISP it worked first time every time.
Footnote 2: DO NOT USE rainlander, I had all sorts of trouble with running my JAVA stuff over the VPN because of this nice eye candy program!

---

### Post by megalomaniac on 2007-04-12
> **rolando said:**
> I have used nm-applet to successfully connect to my University VPN for sometime now.  

TO set this up is very simple.

1. Make sure nm-applet is running in the gnome-panel.

2. Left click on it and select VPN Connections >

3. Click configure VPN.

4. Stick your stuff in (same as you would in windows, i.e. dont touch anything, just type the name of the server to connect to.

5. Once you have done that Left click on the  nm-applet again, select VPN connections > and select whatever you named it.

6. Watch it connect.

7. Go check your IP address at whatsmyipaddress.com or whatever it is.

8. Do what you do on your VPN.

Footnote 1:
Mine only works for around 10 seconds, but I have recently changed ISPs and will be approaching them very soon, as to why this is happening, whilst my old ISP it worked first time every time.
Footnote 2: DO NOT USE rainlander, I had all sorts of trouble with running my JAVA stuff over the VPN because of this nice eye candy program!

Alas if it were that simple I wouldn't need to post here, unfortunately everything seems fine up to step 8. Then nothing, can't ping or connect to anything on the remote network as explained above.

Thanks anyway

---

### Post by Joeri Mul on 2007-04-15
I've had this problem too today, and i realised i modified my dns. You have to add your company's DNS ip to the dns server list. To do this, do the following:

Go to system-->administration-->network and then to the tab DNS.

At DNS-servers, click add. Then type in your company's DNS server IP-adress (not the hostname!)

Greetings from Holland ,

Joeri

---

### Post by Austin_KW on 2007-04-15
After you set it up what is the output of the following terminal commands
ifconfig -a
route

---

### Post by Azalin on 2007-04-27
The results of the commands when I am connected but can not do anything with my VPN (MS PPTP VPN):

```
alex@azalinslair:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:B2:F0:4B  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19791215 (18.8 MiB)  TX bytes:5417501 (5.1 MiB)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22523670 (21.4 MiB)  TX bytes:22523670 (21.4 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.1.56  P-t-P:192.168.1.51  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:98 (98.0 b)  TX bytes:104 (104.0 b)

alex@azalinslair:~$ 
alex@azalinslair:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.93.71.37    192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
alex@azalinslair:~$ 
alex@azalinslair:~$ 


```

Looks like the route is going wrong... or am I mistaken? If not, how do I fix this?

---

### Post by megalomaniac on 2007-04-29
output of  ifconfig -a is: 

```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe57:c302/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:379558 (370.6 KiB)  TX bytes:38093 (37.2 KiB)
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.1.240.10  P-t-P:192.168.240.7  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:88 (88.0 b)  TX bytes:94 (94.0 b)

```

Cheers for the assist

---

### Post by megalomaniac on 2007-04-29
Output of route is:

```

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
mail.cadspec.co 192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0

```


Thanks in advance

---

### Post by megalomaniac on 2007-04-30
Oh and I'm now running Feisty, with the same problems as before...if that makes any difference.

---

### Post by universepoint on 2007-10-20
I'm running 7.10 and having the same problem.  Can connect to the office via PPTP but can't ping.  Was this issue ever resolved?

---

### Post by Azalin on 2007-10-21
Well, I just installed Gutsy and can work with it out of the box... no problems anymore... I do have to tell you that I am NOT running Firestarter, that wás the problem in this whole picture. I had fixed this in Feisty by turning off Firestarter whenever I needed to use the VPN.

Oh, and I am using Network Manager... which is used by default, but some people detest Network Manager and deinstall it... for me it works..

---

### Post by phun-ky on 2007-10-21
hm, I've been trying to get a decent VPN connection ever since feisty came out, using gutsy now and I thought it would be easier, but no luck. It seems that I CAN connect to the VPN, I can open SMB shares and browse the network, but i CAN'T browse the web or use any other protocols. the same problem occurs in windows, and the solution was to check some "dns"- something checkbox in the config and it would work., but i've checked/unchecked all checkboxes in the network manager applet with no luck at all. 

does anyone have the same problem?

---

### Post by Azalin on 2007-10-21
Well, I am not sure if you are talking about a pptp vpn and if you are talking about using internet over vpn or just being able to use internet along side yourvpn... however, if you want to use internet (your existing connection that is) next to your vpn connection then make sure you go into the Router tab of the configuration of your VPN connection and make sure you press 'Only use VPN connection for these addresses" and specify the address of the server you connect to by VPN. This makes sure that only the specified address is used for VPN and anything else ([www.google.com](www.google.com) or 82.234.21.1) will not go through the vpn tunnel.
If you want to use the VPN as your main connection I think enabling Peer DNS through VPN tunnel should do the trick (same Routing tab).
I think enabling Use Peer DNS should do the trick as well, I am not quite sure...

---

### Post by Virtual_Ron on 2007-10-25
I'm so confused.     

I'm using Kubunto 7.10 Gutsy.

I'm using KVpnc to connect to my work cisco vpn.
It says I'm Successfully Connected.

But... nothing works.   I understand it will screw up my local web browsing and what not, but while connected to the vpn, thats fine.

But I cannot connect to anything on my work vpn.    

I use Krdc, and it says "Connection attempt to host failed"
If I try rdesktop, is says "No Route to host".

the remote vpn is 66.195.66.65
my local ip is:  192.168.2.1
my gateway is: 192.168.2.34   (vpn router)

I have just about every port I can think of forwarded.


This is my route & ipconfig output:

===============================

[PHP]ronb@vulcan:~$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.195.66.65    192.168.2.34    255.255.255.255 UGH   0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0[/PHP]

===============================

[PHP]ronb@vulcan:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:18:F3:10:69:67
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe10:6967/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:175370 (171.2 KB)  TX bytes:432126 (421.9 KB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:276 (276.0 b)  TX bytes:276 (276.0 b)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:192.168.2.219  P-t-P:192.168.2.219  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1390  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:802 (802.0 b)[/PHP]


Any ideas what I'm doing wrong?   Is the route screwed up in some way?
I don't understand where the tun0 entry got the address of 192.168.2.219 either...

---

### Post by Virtual_Ron on 2007-10-27
any ideas?

---

### Post by hcgoh on 2007-11-09
if you have firewall enable, disable it first, maybe it is the firewall policy block the packet.

---

### Post by BagOBones on 2007-11-09
Running Gutsy here and I can't even see an option to add a VPN even after installing the VPN packages.

Much like everyone else I would like to connect to my company VPN.

---

### Post by zveroboy on 2007-11-20
I have VPN (PPTP) working on Gutsy, so I am just sharing my setup.  I didn't do anything particularly fancy to make it work, since I am pretty new to Ubuntu and linux altogether.  Nevertheless, I have it working on three seperate pc: two desktops running Ubuntu 7.10, Xubuntu 7.10, and a labptop running Ubuntu 7.10, using wireless.  So, hopefuly, it may help some people here.

First of all I've installed the following packages:
network-manager
network-manager-gnome
network-manager-pptp

Note: I tried connecting with Kvpnc to no avail, so I stuck with network manager.
After installing the package a reboot would be good, or at least log off and log back in.

After rebooting/relogging in I noticed an icon on the top bar that looks like two black computer monitors one behind another.  I am not 100% sure if that icon was there before or not.  Anyhow, left click on the icon and you should see a menu consisting of you network and connections, VPN Connections and manual configuration.  If you don't see that I found several threads on this forum that troubleshoot this issue.  So, assuming you see the menu, choose VPN Connections->Configure VPN.
VPN Connections dialog should come up.  Click Add, and follow the wizard.
Here are some important settings that I found on one of the threads here.  Note, I couldn't connect to VPN using the default settings provided in the wizard, so here are my settings by tab:
Connection Tab:
Make sure to select a correct Type, i.e. Windows VPN (PPTP)

Authentication Tab:
Check Refuse EAP.
Everything else unchecked

Compression & Encryption Tab:
Leave all the compression options unchecked
Check all the encryption options, i.e. Require MPPE encryption, Require 128 bit MPPE Encryption, Enable Stateful MPPE

PPP Options Tab:
I think I left everything at default here, but here is a quick run down:
Custom PPP options: <blank>
IP Options: Check Use Peer DNS, Exclusive device access (UUCP-style lock), Debug Output
Packet aprams: MTU 1416  MRU 1416
Delays and Timeouts:
connect-delay (greyed out), lcp-echo-failure: 10, lcp-echo-interval: 10

Routing:
Check Peer DNS through tunnel
Second option Only use VPN connection for these addresses is optional - I am not entirely sure how to use this option.

Now hit 'Forward' button and 'Apply.

You should you see the new named connection in the VPN Connections Dialog.  Close the dialog and left click on that network manager icon again.  Select VPN Connection->NameofYourConnection. 

Hopefuly, you are able to connect.  I am assuming you will be prompted for user name and password.  For the user name I just put my user name w/out the domain i.e. *username* and not *username@domain.com*. If you are successful there are two way to tell (as far as I know): 1. there will be golden lock in the bottom right corner of the nm icon. 2. on a terminal run```
 ifconfig -a
``` and you should see ppp0 adapter entry with an ip addresse assigned.  Something like this:

```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.2.6  P-t-P:192.168.2.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:114 (114.0 b)  TX bytes:126 (126.0 b)

```

At this point hopefuly you can reach my work network's resources albeit by ip address only.  At least that's how it was for me.  Now, to get the name resolution working, i.e. to be able to reach various internal websites by name I had to open up Network Settings dialog (*Administrator->Network*), select DNS tab, and add my works windows network domain in the **search domains** box.  As far as **DNS Servers** the correct entries were already there.  You can save the settings as new *location*.  Now, I have to bring up Network Settings dialog and select saved location every time I connect to VPN, since I haven't figured out how to get it selected automatically on VPN connecton establishement..  There is probably some file I can modify.  Anybody?

By the way if you are using a wireless adapter to connect to your network here is a link to thread that helped me set it up.
[http://ubuntuforums.org/showthread.php?t=601671](http://ubuntuforums.org/showthread.php?t=601671)

All of my setups are using DHCP to get an ip address, so I haven't messed with using a static ip.  

I hope this helps.  Post your comments.  and good luck.

---

### Post by BagOBones on 2007-11-20
> **zveroboy said:**
> 
All of my setups are using DHCP to get an ip address, so I haven't messed with using a static ip.  

I hope this helps.  Post your comments.  and good luck.


Doesn't work with Static IP, that was the WHOLE point. Yes, everything appears and is easy in DHCP mode but this does not help me with the particular network location of the device in question.

---

### Post by zveroboy on 2007-11-21
Bones,

This thread is called "VPN connected but not working"
Perhaps my post will help some people who've posted on this thread.

You post says:

> **BagOBones said:**
> Running Gutsy here and I can't even see an option to add a VPN even after installing the VPN packages.

Much like everyone else I would like to connect to my company VPN.

Since I lost my crystal ball and therefore an ability to read peoples minds, I didn't know you were using static ip. :roll: However, I've searched for your posts on other threads, and I saw what you are talking about.  However, as you yourself have pointed out it is a bug or at least a shortcoming of NM.  By the way on the community documentation site
[https://help.ubuntu.com/community/VPNClient?highlight=%28network-manager%29#head-59ce4fd1b224aaa5f4666c573a62957a2b6491b5](https://help.ubuntu.com/community/VPNClient?highlight=%28network-manager%29#head-59ce4fd1b224aaa5f4666c573a62957a2b6491b5)

it says:
> important.png NetworkManager only allows VPN connections if it is currently managing a connection. If your network interface is manually configured (in the Network Administration Tool under System/Administration) or in /etc/network/interfaces), it is not managed by NetworkManager. If the option for VPN connections is greyed out, NetworkManager is not managing a connection.

Also, I have switched to static ip on my machine, and while VPN options are still available, when I try to connect nothing happens.  I am not sure where to look for error logs.  Hopefully, this issue is resolved in version 0.7 of Network Manager.  

Perhaps, a workaround presents itself in the meantime.

Good luck.

---

### Post by BagOBones on 2007-11-21
Sorry zveroboy, I had this thread confused with another and was having a particularly bad day when I posted my reply.

---

### Post by J1m on 2007-11-22
Hi Guys,

I was having this problem - could get connected to the vpn server with network-manager-pptp - dns correct - all routing seems correct - firestarter installed and turned off - but could not ping the the VPN server or anything on the remote network - even though i was connected and all the network settings seemed right.

Well now it's working.  All I did was mess around with the settings in VPN-Connections -> Configure-VPN in the network manager applet.

My VPN server at work is a tinyservers.com vmware image for a PPTP server running on BSD.

Anyway - eventually - playing with the settings got rid of the error described above.  This is my network-manager-pptp configuration - strange as it may seem.

I choose windows VPN (PPTP) as the connection type

In authentication - I tick refuse EAP and Refuse MSCHAP and leave the others clear

In compression & encryption - I tick Allow BSD Compression and Enable Stateful MPPE. I leave all the other boxes on that tab UNTICKED including Require MPPE Encryption and Require 128 bit MPPE encryption

In PPP options I tick Use Peer DNS and Exclusive Device Access

In routing I tick peer DNS through tunnel,

That worked for me.  Hope it helps you guys out - just persevere with the settings tweaking and I reckon you can get there.

Cheers


J1m

---

### Post by electralake on 2007-11-25
Had this same issue, don't have a 'correct' solution yet but ... if you open firestarter and stop the fire wall you should see through your tunnel. Hope it helps!

---

### Post by Tmanisaur on 2007-12-01
I'm experiencing the very same problem.  I CAN create a VPN tunnel but CANNOT browse the remote network or any open shares.

I have tried using NetworkManager but no luck ever.  Not even a hint of success.
Now using KVpnc (pptp).

The setup:  
Ubuntu Gutsy on my laptop - SnapGear SG565 on the remote end.
Using KVpnc to create the tunnel.  I can easily validate the tunnel is working by opening the web interface of the SnapGear VPN endpoint on the remote side.  Okay, the tunnel is up.
But, I cannot browse or even see the remote Windows file shares, which live on a Windows 2003 Server box.

Using a WinXP64 machine on this end, I can verify that the credentials work because it can easily browse the remote share.

Route:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.1     *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

So, the remote gateway is in the Routing table (192,168,0,1).

I am just ONE step away from fully migrating to linux; this is the only stumbling block.

Could anyone who has this kind of setup working please share your config?

Many, many, many thanks!

T.

-------------------------------------------------------------------------------
My edit - I managed to solve this in a very VERY simply way:

Edited KVpnc>configure>profile>networks>routes (select "Keep deault routes" to enable surfing on your native IP while being able to browse your remote network)>use additional network routes

-- and added this route:  

192.168.0.0 (your remote base network range)  192.168.0.1 (your remote gateway device)  ppp0 (your vpn device [find it with 'ifconfig'])   

Accept all changes, quit VPnc, restart, connect, explore your mojo...happy days....

* Please post - these forums really do help.  I've been on linux for 3 days now *

---

### Post by Mujaheiden on 2008-01-25
Hey

Im using the network-manager-pptp and it works okay for me (can connect to samba shares, didn't try it yet for imap). But now I want to "Only use VPN connection for these addresses" namely servers @ 10.0.0.4 and 10.0.0.12. Then I can always turn the conneciton on, and still browse the web.

For eases' sake, I just thought to add all 10.0.0.x addresses use the vpn and the rest not. But if I type 10.0.0.0/255 I can't push the apply button. Somehow, I can only go as far as 10.0.0.0/36, so I assume that the 0/36 is not an IP range? But then I don't know what the slash means. Ports? No can't be.

Also, I can't "apply " just putting servers there like 10.0.0.4 10.0.0.10, because also then "apply" is not enabled. So what does the slash mean, and what should I do to achieve these multpiple IP-addresses in the "Only use VPN connection for these addresses"-config line?

And then one more question, for if this gets resolved; Can I auto-connect to the VPN at boot, before mounting samba shares?

---

### Post by Azalin on 2008-01-25
I have this in my "use only for these addresses" box:
192.168.1.0/24

the fact that the IP addess ends with a 0 means: the network wher addresses begin with 192.168.1
The 24 means : use the range 192.168.1.1 to 192.168.1.254 therefore you should not use 255 since that means something completely different ... something impossible and that is why the apply button is then grayed.

When you use network manager, the network manager in default installation won't run until you logon for the first time... I have been told, but other people reading this and know better feel free to correct me here ... so samba shares will be connected on first... 
There is however a way to let the vpn client run a script on connect so that the samba shares related to your vpn are mounted.

> Scripts in /etc/ppp/ip-up.d and /etc/ppp/ip-down.d are run on connection and disconnection, which gives you a chance to do routing using route or just log the state of things. Really, if you get as far as a script in /etc/ppp/ip-up.d actually triggering, you're probably basically there in any case so stop crying now. You might also be interested in /etc/resolv.conf where your current DNS is specified, and the commands ifconfig and netstat.
Check this site: [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

Hope this helps a bit.

---

### Post by Austin_KW on 2008-01-25
The slash notations is the number of bits that define the subnet mask.

The dot notation is 8 bits per dot

so 192.168.1.0/24 is 192.168.1.0 mask 255.255.255.0 where 255 is binary (111111111)
i.e. All IPs 192.168.1.x are in the subnet and x changes for each different address. 

Thus using this /24 you can have a 192.168.1.x subnet a  192.168.2.x subnet and so on.  Used to be called a class C network

The 10. address is in the old class A networks, 10.0.0.0/8 (mask 255.0.0.0)
You are allowed to divide your 10. network into further subnets. Hence you can use values greater than 8.
If it is a single private network it is probable /8. ie any 10.x.y.z  address is on the same subnet

The / notation just gives flexability to divide up networks beyond the old class structure.

---

### Post by Mujaheiden on 2008-01-26
Right.... class C, masks, subsets, the old class structure... thats actually more then i want to know... I now tried 10.0.0.0/8 and i couldnt find google, also not with peer-dns-through-tunnel turned off.
I hate to admit my ignorance here, but cant you just tell me what I should enter?

---

