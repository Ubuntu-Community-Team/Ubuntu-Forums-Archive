---
title: "NetworkManager PPTP VPN"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by ubuntology on 2007-10-24
Hi,
Just switched to Gutsy after almost 10 years with Red Hat & Fedora, but I feel like a new user because many commands I'm used to are missing. Anyway, on to my issue...

Gutsy installed perfectly on my laptop. The network manager applet lets me choose which WAP I want to connect to and automattically switches to eth0 when connected to a cable. It also let me add the information for my company's pptp vpn and connect to it with no problems.
My desktop didn't fare so well. After installing the VPN Connection Manager (PPP generic), I clicked on the nm-applet to create the connection to the vpn, but the only option was manual configuration. Any ideas why the vpn option is missing?

---

### Post by jcostom on 2007-10-24
You'll be wanting to install the network-manager-pptp package.

It's in the universe repository, i believe.  Check your /etc/apt/sources.list to be sure you've got the repos you need activated.  You can do it through Synaptic as well, but if you've been a Linux user for 10+ years, you'll likely find spending a little quality in vim far simpler than navigating menus & dialogs to find the settings.

After uncommenting, do an aptitude update, followed by an aptitude install network-manager-pptp.

---

### Post by ubuntology on 2007-10-24
Thanks for the help.
The Universe repo is enabled I believe. Here is the sources.list file:
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

And here is the output of those commands:
```

root@jmh-linux:/etc/apt# aptitude update
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US 
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]          
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US               
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release                
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Hit http://archive.canonical.com gutsy Release 
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Hit http://us.archive.ubuntu.com gutsy-updates Release                                    
Hit http://security.ubuntu.com gutsy-security/main Packages                               
Ign http://archive.canonical.com gutsy/partner Packages                                   
Hit http://us.archive.ubuntu.com gutsy/main Packages                 
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Ign http://archive.canonical.com gutsy/partner Sources               
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://archive.canonical.com gutsy/partner Sources
Fetched 4B in 1s (3B/s)  
Reading package lists... Done
root@jmh-linux:/etc/apt# aptitude install network-manager-pptp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
root@jmh-linux:/etc/apt# 

```

If I search for that package in the GUI, it returns the package mentioned in the OP, and indicates that it's already installed.

Any more ideas?

---

### Post by jcostom on 2007-10-25
Ok, I'm fresh out of ideas then..  If the package is installed, it should work..

Only thing I can think of would be to run through your .gnome* directories for the prefs related to network manager, whack them, reboot and hope for the best...

---

### Post by codedmin on 2007-10-26
I have the same issue ... vpn conection don't show up in nm-applet...

---

### Post by ubuntology on 2007-10-26
Looks like this might be a bug that has to be worked out.
[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/123696](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/123696)

---

### Post by ubuntology on 2007-10-26
I think I got it worked out...
Right click nm-applet. Choose manual configuration.
Click Wired Connection, then properties...
Enable Roaming Mode.
That fixed it for me.

Step by step with screenshots is here: [http://ubuntology.com/2007/10/26/ubuntu-710-gutsy-networkmanager-pptp-vpn/](http://ubuntology.com/2007/10/26/ubuntu-710-gutsy-networkmanager-pptp-vpn/)

---

### Post by ubuntology on 2007-10-27
Is this working for anyone else?

---

### Post by tcommbee on 2007-10-28
This "works" for me, despite the fact that i need a static IP for my LAN, so activating roaming mode makes matters worse...

---

### Post by dargles on 2007-10-29
Hmm... this all seems very buggy at the moment.
It is great to be able to use the VPN - I never managed to get that working until Gutsy Gibbon - but when I enabled roaming mode (which I can live with) and saw & picked up my stored VPN connection, it failed to validate.  So I set up a "work VPN (2)" and everything works fine again.  It feels rather flaky,,,?
Regards, David

---

### Post by ubuntology on 2007-10-29
> **tcommbee said:**
> This "works" for me, despite the fact that i need a static IP for my LAN, so activating roaming mode makes matters worse...

Is there any chance you could setup a DHCP reservation for your IP? That would ensure that you get the same IP every time and keep you on DHCP.

---

### Post by snmahmood on 2007-10-30
My Network connection has DHCP enabled but the problem is that how could i install VPN PPTP network manager as i don't have acces to internet without it.

Plz tell me in detail how could i setup my connection in Ubuntu 7.10.In windows my VPN details r 

Device Name: WAN Miniport (PPTP)
Device Type: VPN
Server Type: PPP
Transports: TCP/IP
Authentication: MS CHAP V2
Compression: MPPC
PPP Multilink Framing: off

waiting 4 ur reply

---

### Post by ubuntology on 2007-10-30
So how are you connecting now? I guess from windows? You can go here: [http://packages.ubuntu.com/gutsy/net/network-manager-pptp](http://packages.ubuntu.com/gutsy/net/network-manager-pptp)

Get the package and the dependencies and copy to a cd or flash drive.

---

### Post by Misto on 2007-11-08
Okay, I'm starting to feel like an idiot. I can't seem to troubleshoot what's going wrong here. I've gone through the process of adding Network_Manager_pptp and configured my vpn connection in accordance with the guidelines for my university. I just can't seem to figure out what's going wrong. 

Other than the syslog (the pertinent portion of which is affixed below) is there somewhere else I might look for clues as to why it isn't connecting? Is there a means to include a Windows domain that I'm not seeing? Would that be the problem? Any thoughts are welcome.

Thanks, 
Misto

Output from tail -f /var/log/syslog 

```

Nov  8 09:47:07 travesty NetworkManager: <info>  Will activate VPN connection 'IUS VPN', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'jdenison', vpn_data 'ppp-connection-type / pptp / pptp-remote / 149.160.30.68 / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / yes / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Nov  8 09:47:07 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 1 of 4 (Connection Prepare) scheduled... 
Nov  8 09:47:07 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 6644) 
Nov  8 09:47:07 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 1 of 4 (Connection Prepare) complete. 
Nov  8 09:47:07 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Nov  8 09:47:07 travesty NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 2 of 4 (Connection Prepare Wait) complete. 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 3 of 4 (Connect) scheduled... 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 3 of 4 (Connect) sending connect request. 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 3 of 4 (Connect) reply received. 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Nov  8 09:47:08 travesty NetworkManager: <info>  VPN Activation (IUS VPN) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Nov  8 09:47:08 travesty pppd[6645]: Plugin nm-pppd-plugin.so loaded.
Nov  8 09:47:08 travesty pppd[6645]: nm-pppd-plugin: plugin initialized.
Nov  8 09:47:08 travesty pppd[6647]: pppd 2.4.4 started by root, uid 0
Nov  8 09:47:08 travesty pptp[6649]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Nov  8 09:47:08 travesty pppd[6647]: Using interface ppp0
Nov  8 09:47:08 travesty pppd[6647]: Connect: ppp0 <--> /dev/pts/2
Nov  8 09:47:08 travesty pptp[6652]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Nov  8 09:47:08 travesty pptp[6652]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Nov  8 09:47:08 travesty pptp[6652]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Nov  8 09:47:09 travesty pptp[6652]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Nov  8 09:47:09 travesty pptp[6652]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Nov  8 09:47:09 travesty pptp[6652]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 37783). 
Nov  8 09:47:09 travesty pppd[6647]: nm-pppd-plugin: CHAP check hook.
Nov  8 09:47:09 travesty pppd[6647]: Received bad configure-ack:  02 06 00 00 00 00 05 06 d3 b0 89 91 07 02 08 02
Nov  8 09:47:15 travesty last message repeated 2 times
Nov  8 09:47:15 travesty pptp[6652]: anon log[ctrlp_disp:pptp_ctrl.c:911]: Received Call Clear Request.
Nov  8 09:47:19 travesty pppd[6647]: Terminating on signal 15
Nov  8 09:47:19 travesty NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Nov  8 09:47:19 travesty NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Nov  8 09:47:19 travesty NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Nov  8 09:47:19 travesty NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'IUS VPN' because service was 6. 
Nov  8 09:47:19 travesty pptp[6652]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Nov  8 09:47:19 travesty pptp[6652]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Nov  8 09:47:19 travesty pptp[6652]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Nov  8 09:47:19 travesty pppd[6647]: Modem hangup
Nov  8 09:47:19 travesty pppd[6647]: Connection terminated.
Nov  8 09:47:19 travesty pppd[6647]: Child process /usr/sbin/pptp 149.160.30.68 --nolaunchpppd (pid 6648) terminated with signal 15
Nov  8 09:47:19 travesty pppd[6647]: Exit.
```

---

