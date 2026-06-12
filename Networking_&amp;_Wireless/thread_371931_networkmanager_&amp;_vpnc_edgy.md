---
title: "networkmanager &amp; vpnc edgy"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by octopuskevin on 2007-02-27
Hi there, I'm hoping that someone could point me in the right direction here...

I'm running edgy, and have nm-applet installed fine, as well as the unoffical vpnc plugin for it. However now that I am using edgy from dapper, vpnc doesn't seem to connect, although it claims that it is.

i have vpnc installed and connecting through the terminal works fine, however I get the same problems as above when using kvpnc, so I'm not quite sure where the problem lies.

Has anyone else had problems getting vpnc to work through edgy? I'm pretty sure its something minor, but any advise will help. I do know that the VPN settings are correct in terms of host, group password etc...


Cheers,

Kevin

---

### Post by neilius on 2007-02-27
Hi,

I'm also experiencing connection difficulties with the vpnc plugin  for NetworkManager in Ubuntu Edgy. I have ran vpnc from the command line and it seems to just hang. If I deliberately type the wrong group password/username or my own username/password incorrectly I get booted off the server so I know it's connecting, just seems to hang when my credentials are correct. I was successfully using kvpnc in Kubuntu Edgy a month or so ago without problems.

The only things that come to mind are perhaps my machine blocking connections from my work VPN? I'm not sure how I'd go about changing iptables rules or the like if that is the problem. Other than that, I'm stumped, having spent the last couple of weeks googling around and finding very little.

Regards,

Neil.

Edit: here is the contents of my daemon.log file:

> Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IWill activate VPN connection 'UEL Staff - Docklands VPN Service', service 'org.freedesktop.NetworkManager.vpnc', user_name 'neil', vpn_data 'IPSec gateway / dl-vpn.uel.ac.uk / IPSec ID / cvc-staff / Xauth username / neil4 / Domain / UEL', route ''. 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 1 of 4 (Connection Prepare) scheduled... 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.vpnc (PID 8717) 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 1 of 4 (Connection Prepare) complete. 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 1 -> 6. 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 2 of 4 (Connection Prepare Wait) complete. 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 3 of 4 (Connect) scheduled... 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 3 of 4 (Connect) sending connect request. 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 6 -> 3. 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 3 of 4 (Connect) reply received. 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Feb 27 21:30:49 neil-desktop NetworkManager: <information>^IVPN Activation (UEL Staff - Docklands VPN Service) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Feb 27 21:30:59 neil-desktop NetworkManager: <WARNING>^I nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.vpnc', signal 'ConnectFailed', with message 'The VPN login failed because the VPN program could not connect to the VPN server.'. 
Feb 27 21:30:59 neil-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 3 -> 5. 
Feb 27 21:30:59 neil-desktop NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.vpnc): could not stop connection 'UEL Staff - Docklands VPN Service' because service was 5. 
Feb 27 21:30:59 neil-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 5 -> 6.

---

### Post by octopuskevin on 2007-02-27
strange

well i can atleast connect via the terminal


i'm a bit of a noob still to linux, but I would be glad to post some system config logs if that will help... maybe we can figure out what the problem is

...just tell what what I should do in the terminal :P

- Kevin

---

