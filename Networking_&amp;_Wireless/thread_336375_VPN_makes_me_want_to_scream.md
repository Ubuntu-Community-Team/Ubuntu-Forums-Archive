---
title: "VPN makes me want to scream"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by BrendanM on 2007-01-11
Ok, so I'm trying to get a PPTP VPN connection to a windows-based campus network going, and I've been at it for quite some time now. I am running Xubuntu Edgy on a Dell Latitude c610. From what I've been able to gather, the Edgy release broke pptpconfig: 
[http://ubuntuforums.org/showthread.php?t=292128](http://ubuntuforums.org/showthread.php?t=292128)
[http://kubuntuforums.net/forums/index.php?topic=10620](http://kubuntuforums.net/forums/index.php?topic=10620)
[http://ubuntuforums.org/showthread.php?t=267888](http://ubuntuforums.org/showthread.php?t=267888)

So after much hassling with workarounds, I've abandoned pptpconfig in favor of Network Manager and damn the GNOME dependencies.

I configured the VPN settings as suggested here: [http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php](http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php)
(check "Refuse EAP", uncheck "Authenticate Peer")

When I go to connect the VPN tunnel, I briefly get a little VPN lock icon and an animated swoosh. The tooltip says it's connecting, but then the icon disappears. From the console I get the following:

```
/bin/sh: /usr/bin/esd: not found
write_all write failure:: Broken pipe
/bin/sh: /usr/bin/esd: not found
** Message: <information>       Activating VPN connection 'PomonaVPN'.

libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (nm-applet:4747): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (nm-applet:4747): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (nm-applet:4747): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

```

and if I do tail /var/log/messages I get:

```
Jan 11 19:28:24 Hobo-jim kernel: [17179838.044000] PPP generic driver version 2.4.2
Jan 11 19:28:24 Hobo-jim pppd[4624]: pppd 2.4.4 started by root, uid 0
Jan 11 19:28:24 Hobo-jim pppd[4624]: Using interface ppp0
Jan 11 19:28:24 Hobo-jim pppd[4624]: Connect: ppp0 <--> /dev/pts/0
Jan 11 19:28:25 Hobo-jim pppd[4624]: nm-pppd-plugin: CHAP check hook.
Jan 11 19:28:35 Hobo-jim pppd[4624]: Terminating on signal 15
Jan 11 19:28:35 Hobo-jim pppd[4624]: Child process /usr/sbin/pptp 134.173.72.2 --nolaunchpppd (pid 4625) terminated with signal 15
Jan 11 19:28:35 Hobo-jim pppd[4624]: Modem hangup
Jan 11 19:28:35 Hobo-jim pppd[4624]: Connection terminated.
Jan 11 19:28:35 Hobo-jim pppd[4624]: Exit.

```

Does anyone have any idea what's going on? As far as I could find out, /usr/bin/esd has something to do with the sound system? Why should that matter for VPN? What's a CHAP check hook? I looked up signal 15 and it's "peer not responding to echo request" but I'm not sure what that means either. I'm able to ping the VPN server I'm trying to connect to, so it doesn't seem like I'm boxed out by a firewall or anything like that.

Can somebody please help me out here? I'm getting quite frustrated. ](*,)

---

### Post by BrendanM on 2007-01-12
Anyone? Even if you just have some suggestions of where to start.

---

### Post by jklappenbach on 2007-01-18
I haven't been able to get the network manager plugin to work for me, so I've opted to go the direct route (without utilities or GUI clients) and establish pptp vpn through the command line.  I posted about this before under another category, but since I've been seeing so many complaints, I figure a repost would be a good idea.  

First, install pptpconfig, and use it to to setup the tunnel descriptor.  Once you've set up the vpn configuration, create a shell script like the following:

```
#!/bin/sh 
#connect to work 
sudo pon [name of your pptpconfigured tunnel] 
#wait for connection 
sleep 10 
#add routes 
route add -net [remote network ip] netmask [netmask] dev ppp0

```

In my case, my company's internal network addresses are all on the virtual ip range of 10.*.*.*. Therefore, I set up my remote network ip as 10.0.0.0 and the netmask as 255.0.0.0.

Next, I checked /etc/resolv.conf after executing the script. I found that there was no "search" entry. Some may not need this, but I needed to alter /etc/resolv.conf to include the line:

search [remote domain name]

During the execution of pon (IIRC), /etc/resolv.conf will be modified to include the ip addresses for dns to use for name resolution on the tunnel.  In my case, these lines alone weren't enough to enable proper DNS name resolution for protocols. Until I realized this, I had to type everything in as IP addresses, not names. Adding the "search" line in resolv.conf ended up doing the trick.

To stop the vpn connection, I enhanced the script to execute "poff" based on an argument to shut down the connection.

It's not fancy, it's not GUI, but I find that a command line approach is the easiest.

Hope this helps.

---

