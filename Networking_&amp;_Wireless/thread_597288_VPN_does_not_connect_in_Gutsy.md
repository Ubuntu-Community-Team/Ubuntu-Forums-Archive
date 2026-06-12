---
title: "VPN does not connect in Gutsy"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by pvravi on 2007-10-30
Hi,

I use Network manager and VPNC to connect to my VPN. This absolutely worked in Fiesty. Since Gutsy, however, I get a message saying:

```
'The VPN login failed because the VPN program could not connect to the VPN server.'
```

The syslog indicates "Disabled Privacy Extensions". Here's the snippet:

```
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  Will activate VPN connection 'xxx', service 'org.freedesktop.NetworkManager.vpnc', user_name 'xxx', vpn_data 'IPSec gateway / xxx.xxx.40.181 / IPSec ID / xxx / Xauth username / xxx', route ''. 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 1 of 4 (Connection Prepare) scheduled... 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.vpnc (PID 9614) 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 1 of 4 (Connection Prepare) complete. 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 1 -> 6. 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 2 of 4 (Connection Prepare Wait) complete. 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 3 of 4 (Connect) scheduled... 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 3 of 4 (Connect) sending connect request. 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 6 -> 3. 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 3 of 4 (Connect) reply received. 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Oct 30 08:29:19 pvravi-laptop NetworkManager: <info>  VPN Activation (xxx) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Oct 30 08:29:19 pvravi-laptop kernel: [17407.620000] tun0: Disabled Privacy Extensions
Oct 30 08:29:20 pvravi-laptop NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.vpnc', signal 'ConnectFailed', with message 'The VPN login failed because the VPN program could not connect to the VPN server.'. 
Oct 30 08:29:20 pvravi-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 3 -> 6. 
Oct 30 08:29:20 pvravi-laptop NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.vpnc): could not stop connection 'xxx' because service was 6. 
```

Can anyone help me fix this? I might have patched the fiesty kernel, but I don't remember well. Appreciate any and all help, and thanks in advance.

-pvravi

---

### Post by pvravi on 2007-10-30
bump.

Anyone?

---

### Post by pvravi on 2007-10-30
Well, Cisco VPN client works for now, at least.

---

### Post by giosue_c on 2007-11-01
same problem.  anyone know the solution?

---

### Post by lisc998 on 2007-11-02
I'm using either vpnc or the cisco vpn client. Both connect, but after a variable amoutn of time (anywhere from 2 minutes to 20 minutes) the tunnelk seems to break. At first I can't make new connects (ssh or http, etc) and the existing ssh connections freeze. 

I've tried downloading and compiling the latest version of vpnc, but it makes no difference. 

Is anyone else experiencing this problem?

---

### Post by pvravi on 2007-11-03
FWIW this worked for me:

```
 sudo apt-get install network-manager-pptp  
```

After this, the VPNC works for me from the Network-Manager icon on the panel.

---

### Post by xeolhades on 2007-11-07
Same problem here.

My confs work without trouble in Feisty.

Ohhhh s***! :(

---

### Post by panki on 2008-03-13
Same here... any ideas?

---

### Post by wohenben on 2008-04-30
Well for me, the problem has arisen since upgrading to HH - it connected about 70% of attempts in Gutsy, then was pretty stable.  I'm wondering if there's a timeout problem as the concentrator I'm connecting to can be very slow.  If I use the Cisco client in XP, it sometimes takes a minute or so to complete the login, etc., whereas xvpnc gives up after only about 10 secs.

Anybody know if there are timings in the network manager / vpnc that can be tweaked to test this or are they built-in?

---

### Post by wohenben on 2008-04-30
OK, knock that idea on the head.  Just got connected using vpnc command line. Let me dig a bit further. Presumably the network manager interface calls vpnc somewhere along the line?

---

