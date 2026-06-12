---
title: "PPTP is still broken in Intrepid"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by zyrorl on 2008-10-30
Following on from the closed thread from the intrepid forums
[http://ubuntuforums.org/showthread.php?t=922362](http://ubuntuforums.org/showthread.php?t=922362)

PPTP is still broken on the latest release of intrepid.

If you save your password it'll still tell you that there are no secrets found.  

Also the fact that there's no option to enable refuse-eap (and resorting to editing it in gconf-editor) is a deal breaker.  

Users should probably stick to hardy until this bug is fixed.

---

### Post by koruptid on 2008-10-31
I am also running into issues with this, I cannot set the encryption to 128bit and don't know enough about pptp in lunux to set the gconf-editor value for it.

Any advice?

---

### Post by jfollmann on 2008-10-31
Yep, I am having trouble with PPTP in Intrepid as well.

Before I say anything else, I should probably note that I had to re-create my VPN connections after upgrading from 8.04 to 8.10 - although "networkmanager-pptp" was still installed, the individual VPN connections were not kept in Network Manager. I'm not sure if that's normal.

The first problem I ran into is that something is not working right with the keyring - I don't know exactly why, but saving the password in the keyring causes network manager to complain that "no valid VPN secrets were found." This problem was reported at least once while Intrepid was still in beta. That's easy enough to work around, just don't have it store the password.

The second problem is more vague. When I try to initiate the VPN connection through the Network Manager applet, it displays the lock animation for a second, then pops up a notification that just says "the VPN connection 'home' failed."

What should I be looking for to determine what the problem is here?

---

### Post by jfollmann on 2008-10-31
So I reinstalled networkmanager, networkmanager-gnome, and networkmanager-pptp. Then, I set the VPN connection to use point-to-point encryption, 128-bit.

After saving that setting, I initiated the VPN, and it worked. I verified I could access resources on the other end. However, after disconnecting, I now have the same problem when trying to reconnect - generic "connection failed" message.

I noticed 128-bit point-to-point encryption is now turned off again. Weird.

---

### Post by zyrorl on 2008-11-03
i upgraded it to the latest version in the network-manager PPA and it looks like the keyring issues are finally fixed.

Add this to your software sources (system->administration->software sources->third-party software tab):

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

---

### Post by superbonus on 2008-11-03
I did what zyrorl has suggested and I can confirm that I can now connect to my work vpn without any problems - just as I always could with Hardy.

No shortcuts or tricks needed.

---

### Post by 1902 on 2008-11-03
Works for me too :) 
pptp works, don't ask me how coz it still disabling MPPE, security and statful encryption, but it works !! :-k

But thanks :) after all it did the job

I hope we see NM update soon

---

### Post by waspinator on 2008-11-15
I still get Connection to _____ Failed. I know its not the password or server because it works fine from windows. Any idea's?

---

### Post by gabba on 2008-11-15
[The fixed .deb has been on ppa for almost two weeks]("https://bugs.launchpad.net/ubuntu/intrepid/+source/network-manager/+bug/284212/comments/20"), and it has not even made its way into intrepid-proposed. Seems like nobody in the staff cares.

But! As we all know from [http://www.ubuntu.com/products/whatisubuntu/desktopedition:](http://www.ubuntu.com/products/whatisubuntu/desktopedition:)
> 
** Ubuntu 'Just Works'**

We've done all the hard work for you. Once Ubuntu is installed, all the basics are in place so that your system will be *immediately usable*.

Yeah, right.

---

### Post by zyrorl on 2008-11-15
> **waspinator said:**
> I still get Connection to _____ Failed. I know its not the password or server because it works fine from windows. Any idea's?

I'm not sure if you've added the network-manager ppa that I recommended above but if you hvae it may be due to your settings.

Below I have listed instructions on how I have configured my network vpn's hopefully it will also help you (also see the screenshots i've added below).

Step 1.

Right click nm-applet on your system tray, edit connections.
Click on the vpn tab and add a vpn connection (pptp)

Step 2.
Fill out your usual settings connection name, username, password.

Step 3.
Click advanced.
For your authentication options, untick everything except MSCHAPv2.
Tick Enable Point-to-Point encryption (MPPE).  Leave All Available (Default) selected.
Tick allow stateful encrption.
Click "OK" to save the connection settings and "OK" again on the vpn edit dialog.

Step 4.
Open gconf-editor (alt-f2 and type "gconf-editor").
Under /system/networking/connections you should have a list of all your network connections numbered incremently from 1.  If the vpn you created was the latest network connection created it'll be the last one, if not just search for for it (hint: the connection folder should have the id for the vpn connection name you gave in step 2).

Step 5.
Click on the vpn folder and right click, and add a new key.
Add a string named "refuse-eap" with the value of "yes".  
Click "OK" when you're done and close gconf-editor.

Step 6. 

Test your vpn connection.  It hopefully should work:)  Bon Appetit.

---

### Post by dhomas on 2008-11-16
Thank you so much, zyrorl! I've been trying to figure it out since I upgraded! This even fixed the "unknown secrets" problem I've been having with my keyring. Just a quick question, though. Once I've upgraded my nm, should I disable the ppa software source? It frightens me a little :). Any thoughts?

Thanks again!

---

### Post by Insane_Homer on 2008-11-16
superb! thanks zyrorl and everyone else that contributed to this for us.

It's a been real pain so that few weeks not having this working.

Finally I can stop dual booting every time I need to connect to work.

---

### Post by zyrorl on 2008-11-16
> **dhomas said:**
> Thank you so much, zyrorl! I've been trying to figure it out since I upgraded! This even fixed the "unknown secrets" problem I've been having with my keyring. Just a quick question, though. Once I've upgraded my nm, should I disable the ppa software source? It frightens me a little :). Any thoughts?

Thanks again!

it's up to you really... if you want bleeding edge NM then maybe you should leave it in... otherwise disable it if you're happy with what you got and you'll get your upgrades to nm from the regular ubuntu repositories

---

### Post by waspinator on 2008-11-16
Thanks zyrorl!

It finally works. I hope they make this an update soon so that we won't have to manually edit settings in the future.

I know this may be a little off topic, but has anyone else encoutered an error once you end a session in terminal server client? All I do is put in a computer name and connect. That works fine, but when I close it I get the attached error message.

Thanks again,
Waspinator

---

### Post by c-shadow on 2008-11-16
I'm still having problems...
After upgrading to PPA version and the eap trick in gconf network manager connects, but with some errors in syslog.
Everything looks OK until I try to connect to some of the servers at work with tsclient. I login to the server, get the desktop, and then the popup "Connection to _____ Failed" appears. Then tsclient freezes - and keyboard also. Nice :)
Even CTRL-ALT-F1 doesn't work. I can start terminal via icon on panel, but cannot write anything in it...I was able to switch to desktop 2 and from there killed tsclient.
I'm attaching syslog (with some info like IPs removed). 
Any ideas?

---

### Post by zyrorl on 2008-11-16
> **waspinator said:**
> Thanks zyrorl!

It finally works. I hope they make this an update soon so that we won't have to manually edit settings in the future.

I know this may be a little off topic, but has anyone else encoutered an error once you end a session in terminal server client? All I do is put in a computer name and connect. That works fine, but when I close it I get the attached error message.

Thanks again,
Waspinator

I have that problem even when i'm not on a vpn.  Its unrelated.   There's a bug in the tsclient program (not rdesktop), where it doesn't detect a session ending correctly.

---

### Post by zyrorl on 2008-11-16
> **c-shadow said:**
> I'm still having problems...
After upgrading to PPA version and the eap trick in gconf network manager connects, but with some errors in syslog.
Everything looks OK until I try to connect to some of the servers at work with tsclient. I login to the server, get the desktop, and then the popup "Connection to _____ Failed" appears. Then tsclient freezes - and keyboard also. Nice :)
Even CTRL-ALT-F1 doesn't work. I can start terminal via icon on panel, but cannot write anything in it...I was able to switch to desktop 2 and from there killed tsclient.
I'm attaching syslog (with some info like IPs removed). 
Any ideas?

Looks like your vpn doesn't seem to be getting an IP address from what i can see in the log there. Can you connect and paste the output of ifconfig /a for the ppp connection?


> Nov 16 18:35:55 Amber NetworkManager: <info>  VPN connection 'MyVPN' (IP Config Get) reply received. 
Nov 16 18:35:55 Amber NetworkManager: <info>  VPN Gateway: 
Nov 16 18:35:55 Amber NetworkManager: <info>  Tunnel Device: ppp0 
Nov 16 18:35:55 Amber NetworkManager: <info>  Internal IP4 Address: 
Nov 16 18:35:55 Amber NetworkManager: <info>  Internal IP4 Prefix: 32 
Nov 16 18:35:55 Amber NetworkManager: <info>  Internal IP4 Point-to-Point Address: 0.0.0.0 
Nov 16 18:35:55 Amber NetworkManager: <info>  Maximum Segment Size (MSS): 0 
Nov 16 18:35:55 Amber NetworkManager: <info>  Internal IP4 DNS: 
Nov 16 18:35:55 Amber NetworkManager: <info>  Internal IP4 DNS: 
Nov 16 18:35:55 Amber NetworkManager: <info>  DNS Domain: '(none)' 
Nov 16 18:35:55 Amber NetworkManager: <info>  Login Banner: 
Nov 16 18:35:55 Amber NetworkManager: <info>  ----------------------------------------- 
Nov 16 18:35:55 Amber NetworkManager: <info>  (null) 
Nov 16 18:35:55 Amber NetworkManager: <info>  -----------------------------------------


Usually when i connect to the VPN i get allocated an ip address, looks like yours is getting 0.0.0.0, which sounds like it might be an issue at the server end (or not, i'm not 100% sure).  Though usually 0.0.0.0 can be set from config in order to obtain an automatic ip address, but strangely enough the two vpn servers i connected to then I got allocated an ip address.

---

### Post by Momfer on 2008-11-16
Hi,

I got all working as well BUT does anyone know why when I connect thru VPN all my traffic is going thru the VPN? 
I prefer not to tunnel all your traffic through the company VPN while connected.

I dont see: Deselect Use Peer DNS under the PPP Options tab and 
also: Select Only use VPN connection for these addresses

This isnt workable, anybody?

---

### Post by zyrorl on 2008-11-16
> **Momfer said:**
> Hi,

I got all working as well BUT does anyone know why when I connect thru VPN all my traffic is going thru the VPN? 
I prefer not to tunnel all your traffic through the company VPN while connected.

I dont see: Deselect Use Peer DNS under the PPP Options tab and 
also: Select Only use VPN connection for these addresses

This isnt workable, anybody?

Well its off-topic for a starter.. this is a thread about bugs with the pptp vpn connectivity module in network-manager, not "i don't know how to configure my vpn so it doesn't route all the internet traffic through it" thread.

Peer-DNS has to do with requesting DNS from the pptp connection, nothing to do with network routing.  You need to configure your vpn to ignore broadcasted routes and specify your own.  Edit the vpn, click on the ipv4 settings tab, and click the routes button.  Now obviously not knowing your vpn network's settings i can't help you with setting up the routes for your vpn's network, but the screenshot I attached to this post may be able to help (they're my vpn's routes).  The important thing is that you tick the "ignore automatically obtained routes" checkbox and setup your network routes.  If you do not know how to setup your network routes, contact your network administrator.

---

### Post by c-shadow on 2008-11-17
> **zyrorl said:**
> Looks like your vpn doesn't seem to be getting an IP address from what i can see in the log there. Can you connect and paste the output of ifconfig /a for the ppp connection?

Before connecting:
```

alen@Amber:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:71:db:a2  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe71:dba2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66901842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65097057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1509377717 (1.5 GB)  TX bytes:3511000871 (3.5 GB)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1407634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1407634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:213233513 (213.2 MB)  TX bytes:213233513 (213.2 MB)

pan0      Link encap:Ethernet  HWaddr 4e:c4:1f:2d:e5:f0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.45.1  Bcast:192.168.45.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.135.1  Bcast:172.16.135.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

After connecting
```

alen@Amber:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:71:db:a2  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe71:dba2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66905044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65100372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1510103321 (1.5 GB)  TX bytes:3511693684 (3.5 GB)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1407703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1407703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:213244216 (213.2 MB)  TX bytes:213244216 (213.2 MB)

pan0      Link encap:Ethernet  HWaddr 4e:c4:1f:2d:e5:f0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.254.226  P-t-P:192.168.254.226  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:66167 (66.1 KB)  TX bytes:3081 (3.0 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.45.1  Bcast:192.168.45.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.135.1  Bcast:172.16.135.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


> 
Usually when i connect to the VPN i get allocated an ip address, looks like yours is getting 0.0.0.0, which sounds like it might be an issue at the server end (or not, i'm not 100% sure).  Though usually 0.0.0.0 can be set from config in order to obtain an automatic ip address, but strangely enough the two vpn servers i connected to then I got allocated an ip address.

Currently I connect to VPN without problems from windows host inside vmware server session, notice the vmnet interfaces in ifconfig output above. I really don't know what 'pan0' is...

---

### Post by zyrorl on 2008-11-17
> Currently I connect to VPN without problems from windows host inside vmware server session, notice the vmnet interfaces in ifconfig output above. I really don't know what 'pan0' is...

VPN looks like its connecting fine (well at least its obtaining an ip address), are you able to ping any of the servers in the vpn?

pan0 is personal area network (bluetooth networking - some devices [mobile phones,other laptops, etc] support connecting directly to a PAN).

---

### Post by c-shadow on 2008-11-17
> **zyrorl said:**
> VPN looks like its connecting fine (well at least its obtaining an ip address), are you able to ping any of the servers in the vpn?

Yes. Today i tried connecting via SSH, everything works, VPN looks stable. I thoughth it could be some problem with tsclient, tried rdesktop but it also fails:
```

Nov 17 18:45:15 Amber pptp[31823]: nm-pptp-service-31817 log[decaps_gre:pptp_gre.c:414]: buffering packet 234 (expecting 231, lost or reordered)
Nov 17 18:45:15 Amber pptp[31823]: nm-pptp-service-31817 log[decaps_gre:pptp_gre.c:414]: buffering packet 240 (expecting 239, lost or reordered)
Nov 17 18:45:15 Amber pptp[31823]: nm-pptp-service-31817 log[decaps_gre:pptp_gre.c:414]: buffering packet 246 (expecting 245, lost or reordered)
Nov 17 18:45:17 Amber pptp[31823]: nm-pptp-service-31817 warn[decaps_gre:pptp_gre.c:331]: short read (-1): Message too long
Nov 17 18:45:17 Amber pptp[31829]: nm-pptp-service-31817 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Nov 17 18:45:17 Amber pptp[31829]: nm-pptp-service-31817 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Nov 17 18:45:17 Amber pptp[31829]: nm-pptp-service-31817 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Nov 17 18:45:17 Amber pppd[31820]: Modem hangup
Nov 17 18:45:17 Amber pppd[31820]: Connect time 1.2 minutes.
Nov 17 18:45:17 Amber pppd[31820]: Sent 52490 bytes, received 110115 bytes.
Nov 17 18:45:17 Amber pppd[31820]: MPPE disabled
Nov 17 18:45:17 Amber pppd[31820]: Connection terminated.
Nov 17 18:45:17 Amber pppd[31820]: Exit.
Nov 17 18:45:17 Amber NetworkManager: <info>  VPN plugin failed: 1 
Nov 17 18:45:17 Amber NetworkManager: <info>  VPN plugin state changed: 6 
Nov 17 18:45:17 Amber NetworkManager: <info>  VPN plugin state change reason: 0 
Nov 17 18:45:17 Amber NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Nov 17 18:45:17 Amber NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Nov 17 18:45:17 Amber NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Nov 17 18:45:17 Amber avahi-daemon[5624]: Withdrawing address record for 192.168.2.100 on eth0.
Nov 17 18:45:17 Amber avahi-daemon[5624]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.100.
Nov 17 18:45:17 Amber avahi-daemon[5624]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 17 18:45:17 Amber avahi-daemon[5624]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.100.
Nov 17 18:45:17 Amber avahi-daemon[5624]: New relevant interface eth0.IPv4 for mDNS.
Nov 17 18:45:17 Amber avahi-daemon[5624]: Registering new address record for 192.168.2.100 on eth0.IPv4.
Nov 17 18:45:18 Amber NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov 17 18:45:18 Amber NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov 17 18:45:18 Amber nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Nov 17 18:45:30 Amber NetworkManager: <debug> [1226943930.272749] ensure_killed(): waiting for vpn service pid 31817 to exit 
Nov 17 18:45:30 Amber NetworkManager: <debug> [1226943930.273228] ensure_killed(): vpn service pid 31817 cleaned up 

```

> 
pan0 is personal area network (bluetooth networking - some devices [mobile phones,other laptops, etc] support connecting directly to a PAN).
Interesting, i didn't notice that interface in hardy.

---

### Post by zyrorl on 2008-11-17
> **c-shadow said:**
> Yes. Today i tried connecting via SSH, everything works, VPN looks stable. I thoughth it could be some problem with tsclient, tried rdesktop but it also fails:

Possibly, but whatever it is seems like your vpn drops because of it, can you confirm that?  Perhaps i'm not really all that sure what the error messages mean, though I hazard a guess that it possibly is MTU related (btw i do use remote desktop over my vpn regularly without any problems). Lowering the MTU might be a worthwhile exercise to see if it improves this.  

1. Configure your network connections in network-manager (right click nm applet, edit connections).
2. Depending on which you use (either wired or wireless), edit the relevant network adaptor you use to dial your vpn through.
3. Change the MTU from automatic to either 1492 or 1432 (the lower the more stable but a slight bit quicker).



> **c-shadow said:**
> Interesting, i didn't notice that interface in hardy.

Definetly was there for me:).  You only do see it if you type ifconfig -a.  Regular ifconfig without any parameters doesn't display anything.  Either that or your bluetooth device wasnt supported or need a driver installed:)

---

### Post by sgarib on 2008-11-17
Hey,

I'm too have the problem with VPN on Intrepid. I did upgrade nm-applet as sugested but it is still not working.

I have the folowing issues:
- Can't connect to VPN due to "No VPN configuration Options" (/var/log/syslog)
- nm-applet won't save user password when I'm configuring the VPN. Or it is not showing it when I re-edit the entry.
- in gconf-editor I have NO Item for the VPN conection (for the wirless and GSM I do) , they are all working with no problem.

Does anyone upgrade nm-applet but is still having problems?

This is very anoyng!.

Thanks.

---

### Post by zyrorl on 2008-11-17
> **sgarib said:**
> Hey,

I'm too have the problem with VPN on Intrepid. I did upgrade nm-applet as sugested but it is still not working.

I have the folowing issues:
- Can't connect to VPN due to "No VPN configuration Options" (/var/log/syslog)
- nm-applet won't save user password when I'm configuring the VPN. Or it is not showing it when I re-edit the entry.
- in gconf-editor I have NO Item for the VPN conection (for the wirless and GSM I do) , they are all working with no problem.

Does anyone upgrade nm-applet but is still having problems?

This is very anoyng!.

Thanks.

If you have indeed upgraded your network-manager using that PPA I suggested above, You may need to re-create your VPN, as "No VPN Configuration Options" sounds like it hasn't got the settings. which sounds consistent with your issues finding it in gconf-editor.

Delete your VPN connection in nm-applet and re-add it, that may help.  It definetly works correctly for me and most people here... 

I'm not sure exactly what else to suggest, other than to downgrade to network-manager 0.6 and lose the 3G connectivity options.

---

### Post by dj620129 on 2008-11-17
> **zyrorl said:**
> I'm not sure if you've added the network-manager ppa that I recommended above but if you hvae it may be due to your settings.

Below I have listed instructions on how I have configured my network vpn's hopefully it will also help you (also see the screenshots i've added below).

Step 1.

Right click nm-applet on your system tray, edit connections.
Click on the vpn tab and add a vpn connection (pptp)

Step 2.
Fill out your usual settings connection name, username, password.

Step 3.
Click advanced.
For your authentication options, untick everything except MSCHAPv2.
Tick Enable Point-to-Point encryption (MPPE).  Leave All Available (Default) selected.
Tick allow stateful encrption.
Click "OK" to save the connection settings and "OK" again on the vpn edit dialog.

Step 4.
Open gconf-editor (alt-f2 and type "gconf-editor").
Under /system/networking/connections you should have a list of all your network connections numbered incremently from 1.  If the vpn you created was the latest network connection created it'll be the last one, if not just search for for it (hint: the connection folder should have the id for the vpn connection name you gave in step 2).

Step 5.
Click on the vpn folder and right click, and add a new key.
Add a string named "refuse-eap" with the value of "yes".  
Click "OK" when you're done and close gconf-editor.

Step 6. 

Test your vpn connection.  It hopefully should work:)  Bon Appetit.

I followed this step by step, and vpn is working nicely.... I just would like to add that I had to reboot...

---

### Post by c-shadow on 2008-11-18
> **zyrorl said:**
> Possibly, but whatever it is seems like your vpn drops because of it, can you confirm that?  Perhaps i'm not really all that sure what the error messages mean, though I hazard a guess that it possibly is MTU related (btw i do use remote desktop over my vpn regularly without any problems). Lowering the MTU might be a worthwhile exercise to see if it improves this.  

1. Configure your network connections in network-manager (right click nm applet, edit connections).
2. Depending on which you use (either wired or wireless), edit the relevant network adaptor you use to dial your vpn through.
3. Change the MTU from automatic to either 1492 or 1432 (the lower the more stable but a slight bit quicker).

You were right about MTU. This thread helped me solve the problem.
[http://ubuntuforums.org/showthread.php?t=979001](http://ubuntuforums.org/showthread.php?t=979001)
Still, RDP connection is a kind of sluggish. Packets are still dropping... I think I could try a rollback to 0.6 version od NM. Any advice about that, do I just edit the repo list and point it to hardy?

> 
Definetly was there for me:).  You only do see it if you type ifconfig -a.  Regular ifconfig without any parameters doesn't display anything.  Either that or your bluetooth device wasnt supported or need a driver installed:)

I don't know...
I just recently upgraded to hardy, automunting USB devices broke soon after some updates so switched to intrepid - clean install for the first time since 6.06 :) BT device was supported, used it a lot in 7.10, but then somehow lost the "browse device" function for my nokia E65, all the way to 8.04. Clean intrepid install fixed that - works like a charm now. All kind of stuff got broken along the way 6.06-->8.04 I was just lazy to try to fix them...BTW, i always had NM disabled until 8.04 - until then didn't need VPN :-)

---

### Post by zyrorl on 2008-11-18
> **c-shadow said:**
> You were right about MTU. This thread helped me solve the problem.
[http://ubuntuforums.org/showthread.php?t=979001](http://ubuntuforums.org/showthread.php?t=979001)
Still, RDP connection is a kind of sluggish. Packets are still dropping... I think I could try a rollback to 0.6 version od NM. Any advice about that, do I just edit the repo list and point it to hardy?

I'm glad it's fixed your vpn issues.  It sounded like an MTU problem from the logs.

I wouldn't overly recommend that as a method to rollback to an older version of NM, i think there are guides on how to downgrade nm safely somewhere in this forum.

---

### Post by Momfer on 2008-11-18
> **zyrorl said:**
> The important thing is that you tick the "ignore automatically obtained routes" checkbox and setup your network routes.  If you do not know how to setup your network routes, contact your network administrator.


Thank you so very much, did fixed it ;-)

---

### Post by zyrorl on 2008-11-18
> **Momfer said:**
> Thank you so very much, did fixed it ;-)

good to know;) good luck

---

### Post by t.rulands on 2008-11-20
Maybe someone here can help me, i tried everything in this thread, but nothing works :(

When i try to connect, nm just tells me that the connection failed. I'm on 64bit intrepid if that matters and i can connect to the vpn-server fine from the same pc when i boot into xp.

I tried re-installing the  pptp plugin, tried all kinds of combinations of options in the "Advanced" vpn-settings in nm, added the "refuse-eap" string etc....nothing seems to help.

Here's my /var/log/syslog: 

> Nov 20 09:25:00 lap NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Nov 20 09:25:00 lap NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 8009 
Nov 20 09:25:00 lap NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Nov 20 09:25:00 lap NetworkManager: <info>  VPN plugin state changed: 1 
Nov 20 09:25:00 lap NetworkManager: <info>  VPN plugin state changed: 3 
Nov 20 09:25:00 lap NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received. 
Nov 20 09:25:00 lap pppd[8014]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Nov 20 09:25:00 lap pppd[8014]: pppd 2.4.4 started by root, uid 0
Nov 20 09:25:00 lap pppd[8014]: Using interface ppp0
Nov 20 09:25:00 lap pppd[8014]: Connect: ppp0 <--> /dev/pts/0
Nov 20 09:25:00 lap pptp[8024]: nm-pptp-service-8009 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Nov 20 09:25:00 lap pptp[8041]: nm-pptp-service-8009 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Nov 20 09:25:00 lap pptp[8041]: nm-pptp-service-8009 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov 20 09:25:00 lap pptp[8041]: nm-pptp-service-8009 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov 20 09:25:01 lap pptp[8041]: nm-pptp-service-8009 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Nov 20 09:25:01 lap pptp[8041]: nm-pptp-service-8009 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov 20 09:25:01 lap pptp[8041]: nm-pptp-service-8009 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 10008). 
Nov 20 09:25:02 lap pppd[8014]: MS-CHAP authentication failed: Good luck!
Nov 20 09:25:02 lap pppd[8014]: CHAP authentication failed
Nov 20 09:25:02 lap pppd[8014]: Connection terminated.
Nov 20 09:25:02 lap NetworkManager: <info>  VPN plugin failed: 1 
Nov 20 09:25:02 lap pptp[8041]: nm-pptp-service-8009 log[ctrlp_disp:pptp_ctrl.c:929]: Call disconnect notification received (call id 10008)
Nov 20 09:25:02 lap pptp[8024]: nm-pptp-service-8009 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Nov 20 09:25:02 lap pptp[8024]: nm-pptp-service-8009 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Nov 20 09:25:02 lap NetworkManager: <info>  VPN plugin failed: 1 
Nov 20 09:25:02 lap pptp[8041]: nm-pptp-service-8009 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Nov 20 09:25:02 lap pptp[8041]: nm-pptp-service-8009 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Nov 20 09:25:02 lap pptp[8041]: nm-pptp-service-8009 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Nov 20 09:25:02 lap pppd[8014]: Exit.
Nov 20 09:25:02 lap NetworkManager: <info>  VPN plugin state changed: 6 
Nov 20 09:25:02 lap NetworkManager: <info>  VPN plugin state change reason: 0 
Nov 20 09:25:02 lap NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Nov 20 09:25:02 lap NetworkManager: <info>  Policy set 'Auto fritzbox' (wlan0) as default for routing and DNS. 
Nov 20 09:25:14 lap NetworkManager: <debug> [1227169514.380618] ensure_killed(): waiting for vpn service pid 8009 to exit 
Nov 20 09:25:14 lap NetworkManager: <debug> [1227169514.381160] ensure_killed(): vpn service pid 8009 cleaned up 

Every hint or suggestion would be greatly appreciated :-D

---

### Post by zyrorl on 2008-11-20
> **t.rulands said:**
> Maybe someone here can help me, i tried everything in this thread, but nothing works :(

When i try to connect, nm just tells me that the connection failed. I'm on 64bit intrepid if that matters and i can connect to the vpn-server fine from the same pc when i boot into xp.

I tried re-installing the  pptp plugin, tried all kinds of combinations of options in the "Advanced" vpn-settings in nm, added the "refuse-eap" string etc....nothing seems to help.

Here's my /var/log/syslog: 



Every hint or suggestion would be greatly appreciated :-D

can you attach screenshots of your configuration screens or something?  Did you try the same settings as the one i suggested earlier on this post: [http://ubuntuforums.org/showpost.php?p=6187094&postcount=10](http://ubuntuforums.org/showpost.php?p=6187094&postcount=10)

---

### Post by t.rulands on 2008-11-20
These are my settings from the time i posted the log in my first post:
[IMG]http://rulands.org/images/vpn.png[/IMG]

I tried all kinds of different settings tho and the result seems to stay the same (as far as i can tell).

---

### Post by zyrorl on 2008-11-20
FYI this is what my connection logs as 

```

Nov 20 20:18:50 portabeast NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Nov 20 20:18:50 portabeast NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 9056 
Nov 20 20:18:50 portabeast NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Nov 20 20:18:50 portabeast NetworkManager: <info>  VPN plugin state changed: 3 
Nov 20 20:18:50 portabeast NetworkManager: <info>  VPN connection 'XXXXXXXXXXX' (Connect) reply received. 
Nov 20 20:18:51 portabeast pppd[9060]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Nov 20 20:18:51 portabeast kernel: [ 8757.403450] PPP generic driver version 2.4.2
Nov 20 20:18:51 portabeast kernel: [ 8757.524439] NET: Registered protocol family 10
Nov 20 20:18:51 portabeast kernel: [ 8757.526597] lo: Disabled Privacy Extensions
Nov 20 20:18:51 portabeast pppd[9060]: pppd 2.4.4 started by root, uid 0
Nov 20 20:18:51 portabeast pptp[9078]: nm-pptp-service-9056 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Nov 20 20:18:51 portabeast pppd[9060]: Using interface ppp0
Nov 20 20:18:51 portabeast pppd[9060]: Connect: ppp0 <--> /dev/pts/1
Nov 20 20:18:51 portabeast pptp[9093]: nm-pptp-service-9056 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Nov 20 20:18:51 portabeast pptp[9093]: nm-pptp-service-9056 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov 20 20:18:51 portabeast pptp[9093]: nm-pptp-service-9056 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov 20 20:18:52 portabeast pptp[9093]: nm-pptp-service-9056 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Nov 20 20:18:52 portabeast pptp[9093]: nm-pptp-service-9056 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov 20 20:18:52 portabeast pptp[9093]: nm-pptp-service-9056 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 4469). 
Nov 20 20:18:52 portabeast pptp[9093]: nm-pptp-service-9056 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Nov 20 20:18:52 portabeast pptp[9093]: nm-pptp-service-9056 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Nov 20 20:18:52 portabeast pptp[9093]: nm-pptp-service-9056 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Nov 20 20:18:52 portabeast pppd[9060]: CHAP authentication succeeded
Nov 20 20:18:53 portabeast kernel: [ 8759.241683] PPP MPPE Compression module registered
Nov 20 20:18:53 portabeast pppd[9060]: MPPE 128-bit stateless compression enabled
Nov 20 20:18:54 portabeast pppd[9060]: Cannot determine ethernet address for proxy ARP
Nov 20 20:18:54 portabeast pppd[9060]: local  IP address 192.168.150.15
Nov 20 20:18:54 portabeast pppd[9060]: remote IP address 192.168.150.16
Nov 20 20:18:54 portabeast pppd[9060]: primary   DNS address 192.168.150.1
Nov 20 20:18:54 portabeast pppd[9060]: secondary DNS address 192.168.150.254
Nov 20 20:18:54 portabeast NetworkManager: <info>  VPN connection 'XXXXXXXX' (IP Config Get) reply received. 
Nov 20 20:18:54 portabeast NetworkManager: <info>  VPN Gateway: 192.168.150.16 
Nov 20 20:18:54 portabeast NetworkManager: <info>  Tunnel Device: ppp0 
Nov 20 20:18:54 portabeast NetworkManager: <info>  Internal IP4 Address: 192.168.150.15 
Nov 20 20:18:54 portabeast NetworkManager: <info>  Internal IP4 Prefix: 32 
Nov 20 20:18:54 portabeast NetworkManager: <info>  Internal IP4 Point-to-Point Address: 0.0.0.0 
Nov 20 20:18:54 portabeast NetworkManager: <info>  Maximum Segment Size (MSS): 0 
Nov 20 20:18:54 portabeast NetworkManager: <info>  Internal IP4 DNS: 192.168.150.1 
Nov 20 20:18:54 portabeast NetworkManager: <info>  Internal IP4 DNS: 192.168.150.254 
Nov 20 20:18:54 portabeast NetworkManager: <info>  DNS Domain: '(none)' 
Nov 20 20:18:54 portabeast NetworkManager: <info>  Login Banner: 
Nov 20 20:18:54 portabeast NetworkManager: <info>  ----------------------------------------- 
Nov 20 20:18:54 portabeast NetworkManager: <info>  (null) 
Nov 20 20:18:54 portabeast NetworkManager: <info>  ----------------------------------------- 
Nov 20 20:18:54 portabeast postfix/master[6346]: reload configuration /etc/postfix
Nov 20 20:18:55 portabeast NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf 
Nov 20 20:18:55 portabeast NetworkManager: <info>  VPN connection 'XXXXXX' (IP Config Get) complete. 
Nov 20 20:18:55 portabeast NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf 
Nov 20 20:18:55 portabeast NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov 20 20:18:55 portabeast NetworkManager: <info>  VPN plugin state changed: 4 

```

Looks like your logging problems could be due to an invalid username/password?

Have you definetly 100% checked refuse-eap is set to yes for the connection profile? Because i can't authenticate without setting refuse-eap set and the system tells me I have incorrect username/password.

---

### Post by t.rulands on 2008-11-20
> **zyrorl said:**
> 

Looks like your logging problems could be due to an invalid username/password?

Have you definitely 100% checked refuse-eap is set to yes for the connection profile? Because i can't authenticate without setting refuse-eap set and the system tells me I have incorrect username/password.

I'm 100% sure that username/password are correct. I checked it several times and even re-entered it a couple of times to make sure...and it works under XP with the same name/pass...

and here's a screenshot from gconf-editor:
[IMG]http://rulands.org/images/Screenshot-Configuration Editor - vpn.png[/IMG]

Just to make sure that i'm not missing something obvious: i enter the username "as is", e.g. if my username would be "john.doe.vpn" (without the quotes) i enter exactly that into the username box, right? The same goes for the gateway...i just enter "whatever.dyndns.org", right? At least that's what i have to enter in XP :oops:

---

### Post by zyrorl on 2008-11-20
> **t.rulands said:**
> I'm 100% sure that username/password are correct. I checked it several times and even re-entered it a couple of times to make sure...and it works under XP with the same name/pass...

and here's a screenshot from gconf-editor:
[IMG]http://rulands.org/images/Screenshot-Configuration Editor - vpn.png[/IMG]

Just to make sure that i'm not missing something obvious: i enter the username "as is", e.g. if my username would be "john.doe.vpn" (without the quotes) i enter exactly that into the username box, right? The same goes for the gateway...i just enter "whatever.dyndns.org", right? At least that's what i have to enter in XP :oops:

sounds about right.... not really sure what else it could be... maybe someone else here might have a bit more insight into it?

Can you tell us what kind of a server you're vpn'ing to (if you know)?

---

### Post by t.rulands on 2008-11-20
> **zyrorl said:**
> sounds about right.... not really sure what else it could be... maybe someone else here might have a bit more insight into it?

Can you tell us what kind of a server you're vpn'ing to (if you know)?

It's a vpn-router/dsl-modem at work that is connected to a Windows 2000 or 2003 server (I'm not 100% sure which one it is) that is used as a WTS. But what is "behind" that router doesn't really matter i guess (?), because i cant even get a connection to the router... 

The connection details in XP tell me the following:
MS CHAP v2
MPPE 128
no compression
PPP mutlilink framing off

Its pretty unlikely that it's a problem with the router tho because connecting to it from XP works 100% and it also works fine from a co-workers XP machine.:confused:

Edit: it's a Draytek router (looking at the pictures on Draytek's site its probably a Vigor2820n)

---

### Post by zyrorl on 2008-11-20
> **t.rulands said:**
> It's a vpn-router/dsl-modem at work that is connected to a Windows 2000 or 2003 server (I'm not 100% sure which one it is) that is used as a WTS. But what is "behind" that router doesn't really matter i guess (?), because i cant even got a connection to the router... 

The connection details in XP tell me the following:
MS CHAP v2
MPPE 128
no compression
PPP mutlilink framing off

Its pretty unlikely that it's a problem with the router tho because connecting to it from XP works 100% and it also works fine from a co-workers XP machine.:confused:

could be that the router has strange pptp implementation or something... are you 100% sure your vpn is using pptp and not l2tp ipsec?

---

### Post by t.rulands on 2008-11-20
> **zyrorl said:**
> could be that the router has strange pptp implementation or something... are you 100% sure your vpn is using pptp and not l2tp ipsec?

here's a screenshot of the XP connection properties...i dont know how else i could check if its really pptp...

[IMG]http://rulands.org/images/XP.png[/IMG]

---

### Post by RobertSwipe on 2008-11-20
Thanks for the messages here which have enabled me to get VPN connections to several MS Servers now.

Unfortunately, since applying the updated nm applications from the PPA repository, I can no longer create or edit Cisco connections - nothing happens when I create one, the screen never comes up.

Does anyone have any suggestions?

Thanks!

---

### Post by t.rulands on 2008-11-21
I still cant get my vpn connection to work. I tried several hours now and i get the same result no matter what i do.

Is there an alternative to using nm and the pptp plugin? Maybe some other program will work...

---

### Post by gabor111 on 2008-11-22
Hello,

I had many of the problems described above. I did all, and now I can connect to my office, my office server tells that I'm connected, but I can't do anything; no ping, no ssh, no http, no samba... nothing... but my connection is on.
Can anyone help me, please?
Thx in advance

Here is my log:
```
Nov 22 08:38:06 sve13eee NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Nov 22 08:38:06 sve13eee NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5946 
Nov 22 08:38:06 sve13eee NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Nov 22 08:38:06 sve13eee NetworkManager: <info>  VPN plugin state changed: 1 
Nov 22 08:38:07 sve13eee NetworkManager: <info>  VPN plugin state changed: 3 
Nov 22 08:38:07 sve13eee NetworkManager: <info>  VPN connection 'Iroda' (Connect) reply received. 
Nov 22 08:38:07 sve13eee pppd[5950]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Nov 22 08:38:07 sve13eee kernel: [ 1524.285806] PPP generic driver version 2.4.2
Nov 22 08:38:07 sve13eee pppd[5950]: pppd 2.4.4 started by root, uid 0
Nov 22 08:38:07 sve13eee pptp[5964]: nm-pptp-service-5946 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Nov 22 08:38:07 sve13eee pptp[5970]: nm-pptp-service-5946 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Nov 22 08:38:07 sve13eee pppd[5950]: Using interface ppp0
Nov 22 08:38:07 sve13eee pppd[5950]: Connect: ppp0 <--> /dev/pts/0
Nov 22 08:38:07 sve13eee pptp[5970]: nm-pptp-service-5946 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov 22 08:38:07 sve13eee pptp[5970]: nm-pptp-service-5946 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov 22 08:38:08 sve13eee pptp[5970]: nm-pptp-service-5946 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Nov 22 08:38:08 sve13eee pptp[5970]: nm-pptp-service-5946 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov 22 08:38:08 sve13eee pptp[5970]: nm-pptp-service-5946 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 2176). 
Nov 22 08:38:11 sve13eee pppd[5950]: CHAP authentication succeeded
Nov 22 08:38:11 sve13eee kernel: [ 1528.846491] padlock: VIA PadLock Hash Engine not detected.
Nov 22 08:38:11 sve13eee modprobe: WARNING: Error inserting padlock_sha (/lib/modules/2.6.27-8-eeepc-lean/kernel/drivers/crypto/padlock-sha.ko): No such device 
Nov 22 08:38:11 sve13eee kernel: [ 1528.850831] PPP MPPE Compression module registered
Nov 22 08:38:11 sve13eee pppd[5950]: MPPE 128-bit stateful compression enabled
Nov 22 08:38:14 sve13eee pppd[5950]: Cannot determine ethernet address for proxy ARP
Nov 22 08:38:14 sve13eee pppd[5950]: local  IP address 192.168.0.190
Nov 22 08:38:14 sve13eee pppd[5950]: remote IP address 192.168.0.201
Nov 22 08:38:14 sve13eee pppd[5950]: primary   DNS address 192.168.0.201
Nov 22 08:38:14 sve13eee pppd[5950]: secondary DNS address 192.168.0.201
Nov 22 08:38:14 sve13eee NetworkManager: <info>  VPN connection 'Iroda' (IP Config Get) reply received. 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  VPN Gateway: 192.168.0.201 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  Tunnel Device: ppp0 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  Internal IP4 Address: 192.168.0.190 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  Internal IP4 Prefix: 32 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  Internal IP4 Point-to-Point Address: 0.0.0.0 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  Maximum Segment Size (MSS): 0 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  Internal IP4 DNS: 192.168.0.201 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  Internal IP4 DNS: 192.168.0.201 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  DNS Domain: '(none)' 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  Login Banner: 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  ----------------------------------------- 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  (null) 
Nov 22 08:38:14 sve13eee NetworkManager: <info>  ----------------------------------------- 
Nov 22 08:38:15 sve13eee NetworkManager: <info>  VPN connection 'Iroda' (IP Config Get) complete. 
Nov 22 08:38:15 sve13eee NetworkManager: <info>  Policy set 'Auto SMCHOME1' (ra0) as default for routing and DNS. 
Nov 22 08:38:15 sve13eee NetworkManager: <info>  VPN plugin state changed: 4 
Nov 22 08:38:15 sve13eee nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
```

---

### Post by alapaty on 2008-12-02
Hi zyrorl,

Thanks a lot for your steps to fix the PPTP with NM issue in 8.10. I tried lot of other approaches from last one month to get the work PPTP VPN working with my new 8.10 installation and none of them actually worked. Your steps worked like a charm and makes my 8.10 up-gradation complete.

Regards,
Rajendra Alapaty.

---

### Post by spindizzy on 2008-12-12
No luck with any of these fixes whatsoever.
I have the latest pptp vpn and nm (at least I think I do after following these posts' instructions).
Tried all variations of password/nopassword; have refuse-eap installed; tried every possible encryption/compresssion and other options; all give VPN failed error.

Nearly two months now without VPN (thank goodness for a patient employer) and awaiting a fix via upgrades from ubuntu (is there any chance this will be soon?).

I really don't want to rebuild another distro here, nor do I wish to revert to 8.04 and put up with the copnstaqnt nagging to upgrade; most counterproductive.

Hopefully ubuntu will soon fix this essential component of their OS before too many users slip into the void.

Rant concluded.

---

### Post by jharkn on 2008-12-12
> **zyrorl said:**
> 
<snip>

Below I have listed instructions on how I have configured my network vpn's hopefully it will also help you (also see the screenshots i've added below).

<snip>


Cheers, in combination with adding the extra repo this worked a treat setting up my friend's ubuntu VPN!

:D

---

### Post by zyrorl on 2008-12-12
> **spindizzy said:**
> No luck with any of these fixes whatsoever.
I have the latest pptp vpn and nm (at least I think I do after following these posts' instructions).
Tried all variations of password/nopassword; have refuse-eap installed; tried every possible encryption/compresssion and other options; all give VPN failed error.

Nearly two months now without VPN (thank goodness for a patient employer) and awaiting a fix via upgrades from ubuntu (is there any chance this will be soon?).

I really don't want to rebuild another distro here, nor do I wish to revert to 8.04 and put up with the copnstaqnt nagging to upgrade; most counterproductive.

Hopefully ubuntu will soon fix this essential component of their OS before too many users slip into the void.

Rant concluded.

Your rant is really unproductive. How do you expect us to help you without you producing us syslogs with information about your connection?

If you want our help you need to actually provide information.

What steps did you follow? Did you read my posts? Where did it fail?

If you don't know how to obtain system logs to help us, then simply run the following command in your command line:

tail -f /var/log/syslog

Then try connecting to your VPN.  Network manager will write stuff to the systemlog. Paste the output of network manager here.  Its simple.  

Provide information so we can help you, or stop whining as its not constructive at all.

---

### Post by marin.r on 2008-12-28
Hi there, haven't written anything in a very long time in the forums, yet these VPN issues are driving me crazy :)
I added the nm repo, updated, recreated my pptp connection, set refuse-eap to yes via gconf-editor and still no go.
Here is my syslog:
 
```
Dec 28 22:46:06 s37s NetworkManager: <debug> [1230497166.392651] ensure_killed(): waiting for vpn service pid 6584 to exit 
Dec 28 22:46:06 s37s NetworkManager: <debug> [1230497166.392911] ensure_killed(): vpn service pid 6584 cleaned up 
Dec 28 22:51:36 s37s NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Dec 28 22:51:36 s37s NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6606 
Dec 28 22:51:36 s37s NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Dec 28 22:51:36 s37s NetworkManager: <info>  VPN plugin state changed: 1 
Dec 28 22:51:42 s37s NetworkManager: <info>  VPN plugin state changed: 3 
Dec 28 22:51:42 s37s NetworkManager: <info>  VPN connection 'XXXX' (Connect) reply received. 
Dec 28 22:51:42 s37s pppd[6611]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Dec 28 22:51:42 s37s pppd[6611]: pppd 2.4.4 started by root, uid 0
Dec 28 22:51:42 s37s pptp[6615]: nm-pptp-service-6606 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Dec 28 22:51:42 s37s pppd[6611]: Using interface ppp0
Dec 28 22:51:42 s37s pppd[6611]: Connect: ppp0 <--> /dev/pts/1
Dec 28 22:51:42 s37s pptp[6622]: nm-pptp-service-6606 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Dec 28 22:51:42 s37s pptp[6622]: nm-pptp-service-6606 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 28 22:51:42 s37s pptp[6622]: nm-pptp-service-6606 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 28 22:51:43 s37s pptp[6622]: nm-pptp-service-6606 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Dec 28 22:51:43 s37s pptp[6622]: nm-pptp-service-6606 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 28 22:51:43 s37s pptp[6622]: nm-pptp-service-6606 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 11392). 
Dec 28 22:51:43 s37s pptp[6622]: nm-pptp-service-6606 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Dec 28 22:51:43 s37s pptp[6622]: nm-pptp-service-6606 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Dec 28 22:51:43 s37s pptp[6622]: nm-pptp-service-6606 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Dec 28 22:51:43 s37s pptp[6622]: nm-pptp-service-6606 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Dec 28 22:51:43 s37s pptp[6622]: nm-pptp-service-6606 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Dec 28 22:51:43 s37s pppd[6611]: Modem hangup
Dec 28 22:51:43 s37s pppd[6611]: Connection terminated.
Dec 28 22:51:43 s37s NetworkManager: <info>  VPN plugin failed: 1 
Dec 28 22:51:43 s37s NetworkManager: <info>  VPN plugin failed: 1 
Dec 28 22:51:43 s37s pppd[6611]: Exit.
Dec 28 22:51:43 s37s NetworkManager: <info>  VPN plugin failed: 1 
Dec 28 22:51:43 s37s NetworkManager: <info>  VPN plugin state changed: 6 
Dec 28 22:51:43 s37s NetworkManager: <info>  VPN plugin state change reason: 0 
Dec 28 22:51:43 s37s NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 

```

The server I'm trying to connect to is an ubuntu box, set up as per howtoforge article, very simple and straightforward pptpd server setup, works (tested) with default ms vpn client settings.

If someone could lend a hand here, I'd be really grateful :)

---

### Post by RainyCity on 2008-12-31
I have a Dell Mini 9 and the VPN connection is having some problems. I'm running Ubuntu 8.10, Network Manager, with a ndiswrapper wireless driver. I can connect to my work VPN nominally but after I'm connected I can't move data to X windows applications. This seems strange to me and I hope I'm missing something simple. 

Here is what I know:
[LIST]
[*]I can connect to the VPN normally using the instructions on page 1 of this thread.
[*]I can ping work servers using their DNS names.
[*]I can successfully run nslookup and find work and outside of work servers.
[*]I can use Lynx to browse the web successfully.
[*]When I use Firefox to browse to any web sites (work or non-work) the first page seems to come up correctly and any additional web page requests silently time out.
[*]SSH to a work server over the VPN never connects.
[*]RDP to a Windows server over the VPN will let me log in but hangs within seconds after the desktop is drawn
[*]RDP from within the office works like a charm as well as SSH.
[/LIST]

Any idea what is going on would be greatly appreciated. My guesses are some sort of DNS weirdness, a reverse name lookup problem, or a routing issue but I'm not good enough with VPN's to know how to test any of those.

Syslog of establishing the VPN connection, hitting [http://news.google.com](http://news.google.com) and SSH to a server in that order.

> Dec 31 14:56:27 kevin-mini9 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Dec 31 14:56:27 kevin-mini9 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6121 
Dec 31 14:56:27 kevin-mini9 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Dec 31 14:56:27 kevin-mini9 NetworkManager: <info>  VPN plugin state changed: 1 
Dec 31 14:56:28 kevin-mini9 NetworkManager: <info>  VPN plugin state changed: 3 
Dec 31 14:56:28 kevin-mini9 NetworkManager: <info>  VPN connection 'Work VPN' (Connect) reply received. 
Dec 31 14:56:28 kevin-mini9 pppd[6125]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Dec 31 14:56:28 kevin-mini9 kernel: [  317.488001] PPP generic driver version 2.4.2
Dec 31 14:56:28 kevin-mini9 pppd[6125]: pppd 2.4.4 started by root, uid 0
Dec 31 14:56:28 kevin-mini9 pptp[6136]: nm-pptp-service-6121 log[main: pptp.c:314]: The synchronous pptp option is NOT activated 
Dec 31 14:56:28 kevin-mini9 pppd[6125]: Using interface ppp0
Dec 31 14:56:28 kevin-mini9 pppd[6125]: Connect: ppp0 <--> /dev/pts/1
Dec 31 14:56:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Dec 31 14:56:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_disp: pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 31 14:56:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_disp: pptp_ctrl.c:773]: Client connection established.
Dec 31 14:56:29 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Dec 31 14:56:29 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_disp: pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 31 14:56:29 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_disp: pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 8957). 
Dec 31 14:56:29 kevin-mini9 pptp[6136]: nm-pptp-service-6121 log[decaps_gre: pptp_gre.c:405]: discarding duplicate or old packet 0 (expecting 2)
Dec 31 14:56:32 kevin-mini9 pptp[6136]: nm-pptp-service-6121 log[decaps_gre: pptp_gre.c:414]: buffering packet 3 (expecting 2, lost or reordered)
Dec 31 14:56:35 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_disp: pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 31 14:56:35 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_disp: pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Dec 31 14:56:35 kevin-mini9 pptp[6152]: nm-pptp-service-6121 warn[ctrlp_disp: pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 31 14:56:38 kevin-mini9 pppd[6125]: CHAP authentication succeeded
Dec 31 14:56:39 kevin-mini9 kernel: [  328.517239] padlock: VIA PadLock Hash Engine not detected.
Dec 31 14:56:39 kevin-mini9 modprobe: WARNING: Error inserting padlock_sha (/lib/modules/2.6.27-9-generic/kernel/drivers/crypto/padlock-sha.ko): No such device 
Dec 31 14:56:39 kevin-mini9 kernel: [  328.562229] PPP MPPE Compression module registered
Dec 31 14:56:39 kevin-mini9 pppd[6125]: MPPE 128-bit stateless compression enabled
Dec 31 14:56:42 kevin-mini9 pppd[6125]: Cannot determine ethernet address for proxy ARP
Dec 31 14:56:42 kevin-mini9 pppd[6125]: local  IP address 192.168.2.30
Dec 31 14:56:42 kevin-mini9 pppd[6125]: remote IP address 192.168.2.25
Dec 31 14:56:42 kevin-mini9 pppd[6125]: primary   DNS address 192.168.0.87
Dec 31 14:56:42 kevin-mini9 pppd[6125]: secondary DNS address 192.168.0.88
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  VPN connection 'Work VPN' (IP Config Get) reply received. 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  VPN Gateway: 192.168.2.25 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  Tunnel Device: ppp0 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  Internal IP4 Address: 192.168.2.30 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  Internal IP4 Prefix: 32 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  Internal IP4 Point-to-Point Address: 0.0.0.0 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  Maximum Segment Size (MSS): 0 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  Internal IP4 DNS: 192.168.0.87 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  Internal IP4 DNS: 192.168.0.88 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  DNS Domain: '(none)' 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  Login Banner: 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  ----------------------------------------- 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  (null) 
Dec 31 14:56:42 kevin-mini9 NetworkManager: <info>  ----------------------------------------- 
Dec 31 14:56:43 kevin-mini9 NetworkManager: <info>  VPN connection 'Work VPN' (IP Config Get) complete. 
Dec 31 14:56:43 kevin-mini9 NetworkManager: <info>  Policy set 'Work VPN' (ppp0) as default for routing and DNS. 
Dec 31 14:56:43 kevin-mini9 NetworkManager: <info>  VPN plugin state changed: 4 
Dec 31 14:56:43 kevin-mini9 nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Dec 31 14:57:24 kevin-mini9 pptp[6136]: nm-pptp-service-6121 log[decaps_gre: pptp_gre.c:414]: buffering packet 46 (expecting 45, lost or reordered)
Dec 31 14:57:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[logecho: pptp_ctrl.c:677]: Echo Request received.
Dec 31 14:57:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply' 
Dec 31 14:57:33 kevin-mini9 pptp[6136]: nm-pptp-service-6121 log[decaps_gre: pptp_gre.c:414]: buffering packet 61 (expecting 60, lost or reordered)
Dec 31 14:57:33 kevin-mini9 pptp[6136]: nm-pptp-service-6121 log[decaps_gre: pptp_gre.c:414]: buffering packet 62 (expecting 60, lost or reordered)
Dec 31 14:57:52 kevin-mini9 pptp[6136]: nm-pptp-service-6121 log[decaps_gre: pptp_gre.c:414]: buffering packet 79 (expecting 78, lost or reordered)
Dec 31 14:58:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[logecho: pptp_ctrl.c:677]: Echo Request received.
Dec 31 14:58:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply' 
Dec 31 14:59:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[logecho: pptp_ctrl.c:677]: Echo Request received.
Dec 31 14:59:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply' 
Dec 31 14:59:28 kevin-mini9 pptp[6152]: nm-pptp-service-6121 log[logecho: pptp_ctrl.c:677]: Echo Reply received.


---

### Post by RainyCity on 2009-01-02
I just tested the same VPN connection from a 8.04 Ubuntu box I have at home and SSH, RDP, and web browsing worked without problem. So this is either 8.10, or Dell Mini 9 related.

---

### Post by noothe on 2009-01-18
> **zyrorl said:**
> Below I have listed instructions on how I have configured my network vpn's hopefully it will also help you (also see the screenshots i've added below).
...
Test your vpn connection.  It hopefully should work:)  Bon Appetit.

Thx alot zyrol. You saved more than my evening!

---

### Post by Philip_White on 2009-02-23
cheers that worked brilliantly :D:D

---

### Post by jpaul6160 on 2009-03-28
I got it working with the set of instructions on the main page.  Thank you all.  I can now do everything except asp.net 3.5 development on my ubuntu system.  However, I am doing that on a virtual xp system hosted on my ubuntu laptop.

---

### Post by raheel on 2009-04-14
Thanks to this thread I was able to configure the pptp VPN connection on my Ubuntu Intrepid successfully.

All the instructions are already in the thread so I'm only going to state what I discovered beyond those:

1.  I wanted ONLY the traffic meant for the remote network to go there and all other traffic to go directly out to the internet, ignoring the VPN.  I did this by adding a static route (In Ubuntu Hardy it was much easier) in 'Configure VPN'->(Edit your connection)->IPv4 Settings->Routes...

The entry I added in there was this [Address: 192.168.1.0], [Netmask: 255.255.255.0], [Gateway: 0.0.0.0], [Metric: 0]

Address and Netmask represent the subnet of the network you are connecting to
Gateway is anything assigned for all local traffic (which would eventually route to your local router)
Metric is cost of this network (0 works fine here)

That's it.  After that all my communication meant for subnet 192.168.1.xxx went through VPN and the rest ignored the VPN

2. The second thing I wanted to do was to be able to ping the computers on the host network using netbios names (I already have netbios working on my Ubuntu Intrepid so that is not part of these steps)

In order to do this, you need to change the option 'Configure VPN'->(Edit your connection)->IPv4 Settings->Method to 'Automatic (VPN) addresses only'.

This will enable the DNS Servers settings below.  Just enter a valid DNS server inside the remote network that is netbios aware.  I listed the remote network's local domain name (mynetwork.local) in the Search Domains field but I think it might be optional.

When I connected to the remote network after making both these changes, I was able to ping any host inside the remote network I wanted, by its netbios name.

NOTE: If you make any change in your VPN settings, it may wipe out the 'refuse-eap' setting you added in the gconf-editor.  If your MPPE compression settings don't seem to be sticking, not to worry, check under gconf-editor to see if the values are actually there first before raising alarm.

---

### Post by matty_e on 2009-04-15
This worked for me... thank you. The "refuse eap" option should really be included in the NM Applet Gui.  

Version: Ibex 8.10

---

### Post by Keymaster on 2009-04-17
I'd just like to add that for those of us that have jobs that require a firewall to be installed on every computer, if you use Shorewall make sure to add the proper info in it for ppp0 otherwise your VPN will connect, but you can't do anything with it.  (Same goes for any other firewall as well)

---

### Post by rmartinus on 2009-04-28
zyrorl, you are a legend! You have just solved my VPN connection problem.. I'm lovin' my Ubuntu!

---

### Post by zyrorl on 2009-04-28
awesome news! great to hear! enjoy:)

---

### Post by zivley on 2009-06-10
> **zyrorl said:**
> awesome news! great to hear! enjoy:)

Well, now that you've solved everyone's problems with PPTP in Intrepid, would you care for giving a little help with Jaunty? I tried many of the here and some other places proposed solutions and nothing seems to solve my problems, I'm still unable to make a darn pptp connection!

---

### Post by AboveTheLogic on 2009-06-14
I'm getting a "The VPN connection failed because of invalid VPN secrets" no matter what I try.

Here is my log:

```
~$ tail -f /var/log/syslog
Jun 14 13:33:03 e520 NetworkManager: <info>  VPN plugin state changed: 3 
Jun 14 13:33:03 e520 NetworkManager: <info>  VPN connection '[SNIPPED]' (Connect) reply received.                                                                         
Jun 14 13:33:03 e520 pppd[6991]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so is for pppd version 2.4.4, this is 2.4.5                                                 
Jun 14 13:33:03 e520 NetworkManager: <info>  VPN plugin failed: 0                     
Jun 14 13:33:03 e520 NetworkManager: <info>  VPN plugin state changed: 6              
Jun 14 13:33:03 e520 NetworkManager: <info>  VPN plugin state change reason: 10       
Jun 14 13:33:03 e520 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.                                
Jun 14 13:33:03 e520 NetworkManager: <info>  Policy set 'Auto 2WIRE815' (wlan0) as default for routing and DNS.                                                             
Jun 14 13:33:16 e520 NetworkManager: <debug> [1245011596.004694] ensure_killed(): waiting for vpn service pid 6988 to exit
Jun 14 13:33:16 e520 NetworkManager: <debug> [1245011596.004908] ensure_killed(): vpnservice pid 6988 cleaned up
Jun 14 13:37:44 e520 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jun 14 13:37:44 e520 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 7048
Jun 14 13:37:44 e520 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jun 14 13:37:47 e520 NetworkManager: <info>  VPN plugin state changed: 3
Jun 14 13:37:47 e520 NetworkManager: <info>  VPN connection '[SNIPPED]' (Connect) reply received.
Jun 14 13:37:47 e520 pppd[7051]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so isfor pppd version 2.4.4, this is 2.4.5
Jun 14 13:37:47 e520 NetworkManager: <info>  VPN plugin failed: 0
Jun 14 13:37:47 e520 NetworkManager: <info>  VPN plugin state changed: 6
Jun 14 13:37:47 e520 NetworkManager: <info>  VPN plugin state change reason: 10
Jun 14 13:37:47 e520 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jun 14 13:37:47 e520 NetworkManager: <info>  Policy set 'Auto [SNIPPED]' (wlan0) as default for routing and DNS.
^C

```

Screenshots showing my settings are attached. The XP screenshot is from an XP install on virtualbox which is running on the same machine the rest of the info came from. The server I'm trying to connect to is a Windows 2003 Server box w/ RRAS.

I'm wondering if this is the problem:
```
Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so isfor pppd version 2.4.4, this is 2.4.5
```

...but I've searched around and am not finding much info there.

If anyone has any ideas they are appreciated. Thanks!

---

### Post by AboveTheLogic on 2009-06-14
nevermind, I decided to go back to the default KDE network manager instead of the gnome network manager

KVPNC with the kde network manager seems to be working fine for me.

---

### Post by PGScooter on 2009-06-20
AboveTheLogic-

what settings did you use for KVpnc? Obviously it will change for each person, but I thought I would give yours a try.

---

### Post by AboveTheLogic on 2009-06-20
Get DNS from peer
Require MPPE
Allow MPPE Stateful Mode
Authorization Method: MSCHAPv2

everything else unchecked

if you need to figure out your settings, you can do it from a windows machine that can connect... once connected open properties and I think the status tab, it will list the settings you need. You can even do that through virtualbox (nonfree, not OSE) if you need to

---

### Post by ordinaryuser on 2009-12-07
Hey Guys...I'm having problems as well...I hope I've detailed enough....thanks for reading, I know its long...

Let it be known I am operating the following:

OS: Ubuntu 9.10 - Karmic Koala GNOME Version: 2.28.1
USB Wifi Adapter ( TrendNet TEW-229ub)
Network Manager
ndiswrapper w/"windows wireless drivers" to use windows driver for wireless adapter
OpenVPN & PPTP installed into Network Manager
Linksys Wifi Router has VPN>PPTP, L2TP, and the other one...All Enabled.

I have verified my VPN configuration (username/password, host, etc) is correct.

Then this happened:
[IMG]http://imgur.com/cCUD5.png[/IMG]

So then I followed this advice:

>                                                    i upgraded it to the latest version in the network-manager PPA and it looks like the keyring issues are finally fixed.

Add this to your software sources (system->administration->software sources->third-party software tab):

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
After I did that I got this error:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 248DD1EEBC8EBFE8
SOOO then I followed new advice same source:
> Step 1.

Right click nm-applet on your system tray, edit connections.
Click on the vpn tab and add a vpn connection (pptp)

Step 2.
Fill out your usual settings connection name, username, password.

Step 3.
Click advanced.
For your authentication options, untick everything except MSCHAPv2.
Tick Enable Point-to-Point encryption (MPPE).  Leave All Available (Default) selected.
Tick allow stateful encrption.
Click "OK" to save the connection settings and "OK" again on the vpn edit dialog.

Step 4.
Open gconf-editor (alt-f2 and type "gconf-editor").
Under /system/networking/connections you should have a list of all your network connections numbered incremently from 1. If the vpn you created was the latest network connection created it'll be the last one, if not just search for for it (hint: the connection folder should have the id for the vpn connection name you gave in step 2).

Step 5.
Click on the vpn folder and right click, and add a new key.
Add a string named "refuse-eap" with the value of "yes".  
Click "OK" when you're done and close gconf-editor.

Step 6. 

Test your vpn connection.
But at Step 4 I didn't have those folders....

[IMG]http://imgur.com/Hwoza.png[/IMG]

I can't seem to get it working. Anyone have any advice?

---

### Post by netmoon on 2011-08-13
> **zyrorl said:**
> I'm not sure if you've added the network-manager ppa that I recommended above but if you hvae it may be due to your settings.

Below I have listed instructions on how I have configured my network vpn's hopefully it will also help you (also see the screenshots i've added below).

Step 1.

Right click nm-applet on your system tray, edit connections.
Click on the vpn tab and add a vpn connection (pptp)

Step 2.
Fill out your usual settings connection name, username, password.

Step 3.
Click advanced.
For your authentication options, untick everything except MSCHAPv2.
Tick Enable Point-to-Point encryption (MPPE).  Leave All Available (Default) selected.
Tick allow stateful encrption.
Click "OK" to save the connection settings and "OK" again on the vpn edit dialog.

Step 4.
Open gconf-editor (alt-f2 and type "gconf-editor").
Under /system/networking/connections you should have a list of all your network connections numbered incremently from 1.  If the vpn you created was the latest network connection created it'll be the last one, if not just search for for it (hint: the connection folder should have the id for the vpn connection name you gave in step 2).

Step 5.
Click on the vpn folder and right click, and add a new key.
Add a string named "refuse-eap" with the value of "yes".  
Click "OK" when you're done and close gconf-editor.

Step 6. 

Test your vpn connection.  It hopefully should work:)  Bon Appetit.

followed this step bu step guide but nothing happened, and my vpn connection still failed !
anybody can help ? :(

---

