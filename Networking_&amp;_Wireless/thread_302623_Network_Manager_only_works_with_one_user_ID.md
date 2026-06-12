---
title: "Network Manager only works with one user ID"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by tobi.wan.kenobi on 2006-11-18
Hello Everyone.
I counldn't find an answer in any of the currently available threads, so this is the first time for me to create my own.

I am running the Network Manager (nm-applet) in Ubuntu Edgy.  It works just greate with "User1" but I'm having issues with "User2".

I got to the point (with User2) that my wireless network is found.  When I click onto the icon for the network manager, it shows me my wireless network.  When I click it, it asks me for my encryption passphrase.  After entering it, I gain access to the network as expected.  It also asks me for my password of my "keyrings", and the keyring manager shows the wireless access points ID, as it does for User1.

The challenge I have is that this process re-occurs every time I re-logon as User2.  I have to click on the network manager icon and provide my passphrase every time I login as User2.  I don't have to do this with User2.

Here's some further information from my syslog file:
Successful login with User1:
Nov 18 18:53:02 kimchee NetworkManager: <information>^Istarting... 
Nov 18 18:53:02 kimchee NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'ipw2200'. 
Nov 18 18:53:02 kimchee NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 18 18:53:02 kimchee NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 18 18:53:02 kimchee NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
Nov 18 18:53:02 kimchee NetworkManager: <information>^IDeactivating device eth1. 
Nov 18 18:53:26 kimchee NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 18 18:53:26 kimchee NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth1'. 
Nov 18 18:53:26 kimchee NetworkManager: <information>^IWill activate connection 'eth1/wLan1'. 
Nov 18 18:53:26 kimchee NetworkManager: <information>^IDevice eth1 activation scheduled... 
Nov 18 18:53:26 kimchee NetworkManager: <information>^IActivation (eth1) started... 

Unsuccesful attemps with User2:
Nov 18 18:38:51 kimchee NetworkManager: <information>^Istarting... 
Nov 18 18:38:51 kimchee NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'ipw2200'. 
Nov 18 18:38:51 kimchee NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 18 18:38:51 kimchee NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 18 18:38:51 kimchee NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
Nov 18 18:38:51 kimchee NetworkManager: <information>^IDeactivating device eth1. 
Nov 18 18:39:14 kimchee NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 18 18:39:14 kimchee NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..


Any suggestion is highly apprechiated.
Thanks.

---

### Post by Amitava on 2006-11-19
To run NetworkManager you generally need root privilage. In ubuntu the root a/c is disabled by default, the user who installed ubuntu has the root like privilage, i think User1 has installed the linux thats why user2 will always need the user1's password..

---

