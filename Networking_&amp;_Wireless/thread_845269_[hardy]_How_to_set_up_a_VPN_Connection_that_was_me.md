---
title: "[hardy] How to set up a VPN Connection that was meant for Cisco VPN Client"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by Data83 on 2008-06-30
Hi, 
 
this is not a call for support but a small information for all out there that have the same problems that I had connecting to a VPN-Network that was meant for Cisco VPN Client.
(Threat [http://ubuntuforums.org/showthread.php?t=726729](http://ubuntuforums.org/showthread.php?t=726729) asks the same question but was unfortunately closed without an answer)

If this is the wrong place for my post, please feel free to move it  to the appropriate section!
-----------------------------------------------

First of all, you have to install the network-manager-vpnc plugin:

sudo apt-get install network-manager-vpnc

Then you have to create a new Profile by clicking on the network-manager-applet in the tray and selecting VPN-Connections->Configure VPN

Then click "add" and follow the steps in the window.
In the field "Gateway" you enter the appropriate URL of the VPN-Server, in "Group Name" the group (the same one you would use for the Cisco VPNClient)

In the tab "optional" you have to select "Override Username" and enter the username you would also enter in the Cisco VPN Client.

So far so good. Now comes the tricky part.
When clicking the network-manager-applet in the tray and selecting VPN-Connections->NameOfYourVPNConnection, you are asked for your password and group password.
The password is just the one you would also enter in the Cisco VPN Client.
However, there is also the group password. DO NOT LEAVE THAT FIELD BLANK. If you do, the nm-applet will just vanish and only return after a complete reboot (not evern loging out will help). Probably a bug in nm-applet.
You will have to enter the appropriate group password. You can usually find out about it in the profile-file for the cisco client. 
If you are unlucky, however, and the group uses an encrypted password, it does not work.
You want to ask your system administrator to create another group with a clear text password.

I hope that helps anyone,

Cheers!

P.S.: I hope intrepid will make it easier to connect to vpn networks ;)

---

### Post by cebesius on 2008-07-01
> **Data83 said:**
> 
You will have to enter the appropriate group password. You can usually find out about it in the profile-file for the cisco client. 
If you are unlucky, however, and the group uses an encrypted password, it does not work.

Actually you do not need to bug your administrator.  You can use the [cisco vpnclient password decoder](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode).

---

