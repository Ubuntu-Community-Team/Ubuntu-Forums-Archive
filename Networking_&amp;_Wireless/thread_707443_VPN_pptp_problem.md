---
title: "VPN pptp problem"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by vussvillem on 2008-02-25
I have managed to VPN connect once, I remember that it was very easy - I just had to know the gateway address and left other settings default. However, I have reinstalled Ubuntu and now the VPN connection is not working any more.

Here is the output of  sudo tail -f /var/log/syslog

Feb 25 19:08:30 vussvillem-laptop NetworkManager: <info>  VPN Activation (TUIT VPN) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <info>  VPN Activation (TUIT VPN) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <info>  VPN Activation (TUIT VPN) Stage 2 of 4 (Connection Prepare Wait) complete. 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <info>  VPN Activation (TUIT VPN) Stage 3 of 4 (Connect) scheduled... 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <info>  VPN Activation (TUIT VPN) Stage 3 of 4 (Connect) sending connect request. 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <info>  VPN Activation (TUIT VPN) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <info>  VPN Activation (TUIT VPN) Stage 3 of 4 (Connect) reply received. 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <WARN>  nm_vpn_service_stage3_connect_cb(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not start the VPN 'TUIT VPN'.  dbus says: '(null)'  **'Could not process the request because the VPN connection is already being started**.'. 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <info>  VPN Activation (TUIT VPN) failed. 
Feb 25 19:08:30 vussvillem-laptop NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): **could not stop connection 'TUIT VPN' because service was 6**.

---

