---
title: "network-gnome-pptp won't work..."
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by gharz on 2007-04-20
hi, guys.

since 6.10, i am not able to connect through pptp (i was using pptpconfig)... i was expecting feisty would fix this issue... unfortunately, it did not.

i've installed network-manager network-manager-gnome and network-manager-pptp.

i run nm-applet... and everything seemed fine because i was able to create a vpn profile and the profile is selectable... but when i check the connection (sudo tail -f /var/log/syslog) it showed the following...

sudo tail -f /var/log/syslog
Apr 20 12:50:14 Ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 20 12:50:25 Ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 20 12:50:38 Ubuntu dhclient: No DHCPOFFERS received.
Apr 20 12:50:38 Ubuntu dhclient: No working leases in persistent database - sleeping.
Apr 20 12:50:46 Ubuntu gconfd (root-32353): GConf server is not in use, shutting down.
Apr 20 12:50:46 Ubuntu gconfd (root-32353): Exiting
Apr 20 12:51:10 Ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Apr 20 12:51:10 Ubuntu NetworkManager: <information>^IUpdating VPN Connections... 
Apr 20 12:51:21 Ubuntu NetworkManager: <information>^IWill activate VPN connection 'VPN Secure', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'user', vpn_data 'ppp-connection-type / pptp / pptp-remote / 135.82.1.2 / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Apr 20 12:51:21 Ubuntu NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN.

by the way, i'm using my wireless connection to connect to the internet and my wifi interface is eth1 not eth0.

please help.

---

### Post by mgmiller on 2007-04-20
I have the same problem.  At least you got yours to mention a VPN connection, mine does not give me the choice after installing network-manager-pptp.

---

### Post by bingnet on 2007-04-22
Same thing, syslog says "[date] [time] [hostname] NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN."

I'm running Feisty with wireless network adapter.

---

### Post by ego1 on 2007-04-23
This success seem that you has not configurated the server by way it can supply any ip address.
I am thinking in a winxp and you don't have activated dhcp from that ip to other ip.
If this is the situation, them remember that this ip must be different that any local network you can access.
hope, was this.

---

### Post by AronVanAmmers on 2007-04-25
I had the same problem: my VPN connection wouldn't come up, same message in the syslog (though not the one with all the parameters).

The cause was that network-manager wasn't managing my network interface, and the VPN connection requires an "existing network connection". Solution for me: set my network interface to "roaming mode" with network-manager. Then it shows info about the interface as well, and it can bring the VPN up.

Now on to the next problem, it removes my DNS settings...

---

### Post by suedama1756 on 2007-04-28
First time posting so apologies for any noob behaviour.

I am running feisty fawn V7.04 and have added the network-manager-pptp pluggin. I have successfully connected to my windows VPN at work using wired connections. I cannot get it to work if I am connected using the wireless adapter. It seems that the pptp plugin is hard wired to connect on eth0, does anyone know if there is there a way I can configure it to use eth1, or even better try eth1 if eth0 is down or both?

In addition to this, the network-manager seems to indicate that I can connect to the wired adapter or the wireless adapter, but not both, is this really the case?

I'm relatively new to linux, I've tryed to make the move several times but always get unstuck with something that I really don't have the time to solve. I really love feisty so I'm hoping this doesn't happen again...

---

### Post by gundee on 2007-05-04
I had the same problem with the openVPN-plugin. I solved it by putting the Ethernet-Device into "Roaming-Mode" in the "manual configuration..."-menu of Network-Manager. Since then, my wired network also appeared in the selection list. 

Cheers

---

### Post by crusader2004 on 2007-05-08
Is there a serious solution for this problem in the meantime?
I have the same problem, and the roaming mode didn't work for me for some reason.
Any answer which helps me would be great.

---

### Post by teslaspigeon on 2007-05-12
I figured I'd offer my 2 cents on the goo-headed way I got my pptp connection to work with feisty and networkmanager.    

A little background:
I have a static IP address on my LAN for ease of connecting to my machine from other machines in my house.
I used to use pptpconfig to connect to the pptp VPN but that seemed to stop working when I initially upgraded to edgy (I am now on feisty).

I find that the network-manager app only shows the VPN connection when I check "enable roaming mode" under the configuration for eth0 - this gives me a DHCP address from my router.

Once I have a DHCP address in "roaming mode", I can see the VPN connection choice under the menu and can connect to the VPN.    

Once I'm done and am disconnected from the VPN, and I want back my static IP address - I uncheck "enable roaming mode" and put back in my static IP address.   Unfortunately, this doesn't give me back my IP address - I have to run this command to get it back:
sudo /etc/init.d/networking restart

This seems a little goo headed to me - but it is the best I have been able to get to work so far.    If anyone has a better suggestion, I'm listening.     

Unfortunately my linksys router doesn't let me set DHCP to give specific IP addresses based on MAC address.    I suppose I could set up a DHCP server on ubuntu, where I could probably probably do the MAC address mapping, but it seems a little much...

---

### Post by mgmiller on 2007-05-13
Thank you teslaspigeon.  I have an identical configuration as you do for static IP at home.  I can now open the VPN tunnel to my office, but I can't seem to connect to it using the  Places>Connect to Server like I used to in Dapper.  I tell it to connect to the Windows share (samba server) and give it the IP address and user name and password, but after trying for a bit, it just says it can't display the contents.  Any thoughts on how to configure the VPN in network manager?  I'm just trying to connect to a winXP pro box at work that I routinely access this way from other windows boxes.  No fancy routing or anything.
I agree it is annoying that after turning off roaming mode, all the static IP info is gone and I have to reenter it and then give the networking restart command.

---

### Post by mgmiller on 2007-05-13
Here is something that may help.  Bring up the network settings gui and while you are still connected by static IP, at the top of the window, next to where it says Location: click the little floppy disk icon and name it static IP.  Next, change the configuration to roaming mode and after it has obtained the IP address from the DHCP server, again click the floppy disk icon and name it Roaming mode for VPN.  Now all you have to do is select the location in the drop down box and click the check mark icon to switch between them.

Now if I could only get it to display the contents of my office machine directory......

---

### Post by teslaspigeon on 2007-05-13
"saving the location" sorta works - still a little screwy, but better.   Saves me a little typing anyway.
I've saved 2 "locations" / configurations:
   static-ip
   roaming

By default I have it on "static-ip" - and I can see the VPN connections in the menu!
After I connect and disconnect from the VPN - it switched back to DHCP address, but with the saved locations it's a little easier:   I set it "roaming", and let it get the IP - and then set it to "static-ip" and I'm back to what I want:   a fixed IP and VPN connections in the menu.    Thanks for the tip!

One note:  the connection information is NOT accurate given by the system tray icon.   I use "ifconfig" from a command line to check my real address.

Onto your problem.   I set up a second version of my VPN settings to connect to school - I think they use Microsoft VPN, but I don't know.
Here is what I changed:

Connection tab
---------------
connection name:  [school name]
gateway: [IP for remote]

Authentication
---------------
checked Refuse EAP

Compression & Encryption
---------------------
checked Allow Deflate compression
checked Allow BSD compression
(left Require MPPE encryption checked)

PPP options
----------------
(left all defaults)

Routing
--------------
checked "Only... these addresses" and entered my school subnet


Depending on your setup - you may or may not want that last step.   This just means I only use the VPN when I have to - not for all traffic.

The *key* step seems to be checking "Refuse EAP" - without this, my VPN doesn't work.

I got that either from another forum post or my old pptpconfig settings, I can't remember which.

Hmmm...  your problem actually was with connecting to a SMB share...  maybe that "routing" setting is just what you need.   
I assume you have something like:   //smbserver/sharename
I'd see if you can do the following:
nmblookup smbserver
    (lookup server address)
ping smbserver
    (test basic VPN connection to SMB machine)
smbclient -d 3 //smbserver/sharename
    (test connection to share with some debugging info.
           you may need "-U username" if your username on the share isn't the same)

Hope it helps.

---

### Post by mgmiller on 2007-05-13
Thank you for the help.
I tried everything you suggested, but I still can't display the contents of my office machine.  This is very frustrating, it worked perfectly in Dapper.  At least the terminal server client works reliably.  I can do work on the office machine, I just can't transfer files back and forth.

---

### Post by teslaspigeon on 2007-05-14
Hmmm...  I wish I could help further.   

I take it that smbclient didn't work either?   If smbclient worked - you should be able to connect with Nautilus or whatever.   Of course if it didn't ...  I was hoping the debug information would give some sort of clue.

---

### Post by crusader2004 on 2007-05-31
I have still this error message when I try to connect to the vpn via my wireless adapter: 

May 31 16:55:06 anubis NetworkManager: <information>^IWill activate VPN connecti
on 'Media Solutions VPN', service 'org.freedesktop.NetworkManager.ppp_starter', 
user_name 'crusader', vpn_data 'ppp-connection-type / pptp / pptp-remote / demo.
media-solutions.de / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / y
es / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock /
 yes / ppp-auth-peer / no / ppp-refuse-eap / no / ppp-refuse-chap / no / ppp-ref
use-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-int
erval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / route
s /  / use-routes / no', route ''. 
May 31 16:55:06 anubis NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_c
onnection (): nm_vpn_manager_activate_vpn_connection(): no currently active netw
ork device, won't activate VPN. 

Some details what I have and what I have done to get a connections:

- I get DHCP for my wireless, and it's working to get internet connection
- Roaming enabled for the eth0 (wired network device) does not solve this problem
- the vpn option is all time accessible but I get the error message posted above
- I tried do use static ip on the wirless device but no change

Any help would be great, I don't know how to solve this problem

---

### Post by teslaspigeon on 2007-05-31
I'm guessing here, but....

from your output it looks like you don't have "Refuse EAP" checked.    At least it mentions:  "ppp-refuse-eap / no" - which sounds like that to me.

I'd see if that box is checked under the VPN settings on the "Authentication" tab, and see if that helps.   

I could be totally off base, but it's my best guess off hand.

---

### Post by crusader2004 on 2007-05-31
Thank you for your answer. This is the new output:

May 31 19:28:27 anubis NetworkManager: <information>^IWill activate VPN connection 'Media Solutions VPN', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'crusader', vpn_data 'ppp-connection-type / pptp / pptp-remote / demo.media-solutions.de / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / compress-mppc / no / compress-deflate / yes / compress-bsd / yes / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes / 192.168.10.0/24 / use-routes / yes', route '192.168.10.0/24'. 
May 31 19:28:27 anubis NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN.

---

### Post by crusader2004 on 2007-06-14
Any idea what could be the problem now?

---

### Post by saxophobe on 2007-07-28
After reading a great deal of posts on this subject, I have noticed one thing in common; everyone that gets it to work is using a wired connection, and no one seems to be able to get this to work using a wireless connection, eth1.

This sounds to me like something needs to be added to the config file to allow the use of not only eth0, but also eth1.  I'm looking for the conf file for this to see if it can be reconfigured, but I haven't yet.

If anyone finds it, please post.

Thanks!

sax

---

### Post by saxophobe on 2007-07-28
Here's how I finally got it to work:

[http://shiny.thorne.id.au/2007/01/pptp-from-ubuntu.html](http://shiny.thorne.id.au/2007/01/pptp-from-ubuntu.html)

This and a few reboots did the trick.

Good Luck all!

sax

---

