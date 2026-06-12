---
title: "[SOLVED] intel Pro WLAN 3945"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by michelux on 2008-03-22
Hi guys,

I just performed an upgrade to Unbuntu Hardy and now I cant get my wireless connection working.
I can see my network, but when I try to connect to it I notice that my wirelesscard won't start.
I tried to install the latest jockey driver as is recommanded on the upgrade webpage of ubuntu, but also doesn't solve my problem.

The result of ip addr sh is the following:
4: wlan0_rename: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:19:d2:4e:2f:78 brd ff:ff:ff:ff:ff:ff

Does anybody have an idea on how to solve this?

---

### Post by Eiríkr on 2008-03-22
One good place to start would be topost the results of each of the following:
```
ifconfig
iwconfig
cat /etc/network/interfaces
```

And also let us know *exactly* what happens, and post what you see on screen in the terminal, when you restart your network like so:
```
sudo /etc/init.d/networking restart
```

Cheers,

Eiríkr

---

### Post by michelux on 2008-03-22
Hi Eiríkr,

Here are the results of the commands you asked me to post.

**ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:18:8b:aa:e9:1b  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:feaa:e91b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1050954 (1.0 MB)  TX bytes:289180 (282.4 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:d2:4e:2f:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158400 (154.6 KB)  TX bytes:158400 (154.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-4E-2F-78-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**cat /etc/network/interfaces**:
auto lo
iface lo inet loopback


The result of **/etc/init.d/networking restart**:
 * Reconfiguring network interfaces...                                   [ OK ]

As for your question as what happens when I try to get the wirelesscard to work...nothing happens:cry:

When I try to make a connection on my wirelesscard, I get this message in **/var/log/messages**:
Mar 22 23:52:31 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason

I'm not sure if this is any help though....

Greetz,
Michelux

---

### Post by Eiríkr on 2008-03-22
Thanks Michelux.  I'm a bit confused where the "wlan0" in your first post comes from, since it's not showing up in the command results you just posted.  

Anyway, it appears that your wireless interface is "eth1", and that you likely have a wired interface which is what's showing up as "eth0".  

Gutsy (and probably Hardy too?) has an application called Network Manager that is the default manager of network interfaces.  Unfortunately, from numerous posts I've read here on the boards, it is a piece of crap in a number of important ways -- one of which is that it only allows one active interface at a time.  I suspect that it Network Manager brings up eth0, and then since it can only handle one active interface, it never even tries to bring up eth1.  If you don't need your wired and wireless connections up at the same time, try disabling the eth0 wired connection in the Network Manager applet that looks like a small network icon on your toolbar, and see if that allows you to bring up your wireless instead.  

If you need both up at the same time, I think you need to get rid of Network Manager.  One recent thread (among many) that recommends replacing Network Manager with WICD is [thread=731899]this one[/thread].  Note that the package is unfortunately not on the Ubuntu repositories, and so must be downloaded from Sourceforge (link provided in the thread linked to above).  I haven't tried it myself, and cannot given my current circumstances, but it comes highly recommended.  

Hope that helps,

Eiríkr

---

### Post by michelux on 2008-03-22
Hi Eiríkr,

When I was using Gutsy I was using WICD, but after I installing Hardy and I running into networkproblems I got rid of it and installed the "native" Ubuntu Network Manager as I thought wicd might be the cause of my problems.

anyway, I have unplugged my networkcable and rebooted my laptop, but I didn get connection on my wireless.

I will uninstall network Manager and install WICD and get back with the result of this action.

Michelux

---

### Post by michelux on 2008-03-22
IT WORKS !!!!!!!!!!!!!!!!!!!!

Thank you very much Eiríkr

After installing wicd I had to change the configuration so it would know eth1 and NOT wlan0, as it used to be. But that was the only thing i had to do.

Maybe as a tip for others:
wicd doesn't display a connectivity icon in the notification area by default.
This can easily be done by creating a startup program, where the command you need to give is /opt/wicd/tray.py

---

### Post by Eiríkr on 2008-03-22
Brilliant, glad to read things are working!  :D  If that does it for you, then please also remember to mark this thread as SOLVED in the Thread Tools dropdown towards the top of the page.

Cheers,

Eiríkr

---

### Post by lakesurfer on 2008-04-27
I'm having the same problem with a 3935 abg on a Dell Latitude D620. With wired networking disabled in Network Manager, I am able to connect via the WLAN (WPA1/2), but the Manager keeps defaulting to having wired networking on and you have to go through the whole palaver whenever you fire up the PC. 

Tried installing WICD, but Network Manager won't properly uninstall and then conflicts with WICD.

I am using the release version of Hardy, downloaded as an upgrade from Gutsy yesterday.

---

