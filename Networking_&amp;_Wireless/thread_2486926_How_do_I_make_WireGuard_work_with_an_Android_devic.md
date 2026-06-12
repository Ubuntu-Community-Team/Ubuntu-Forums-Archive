---
title: "How do I make WireGuard work with an Android device?"
date: 2023-05-17
forum: Networking &amp; Wireless
---

### Post by managerrose on 2023-05-17
On Ubuntu 22.04, I've used the guide at [How to Set Up WireGuard VPN Server on Ubuntu]("https://tech.serhatteker.com/post/2021-01/how-to-set-up-wireguard-vpn-server-on-ubuntu/") to setup a Wireguard server on Ubuntu 22.04. All Ok except for "4. Test WireGuard":[INDENT] You can now check you IP searching on the browser **what is my ip**.
 You should now see your YOUR_SERVER_IP_ADDRESS instead of your your local IP which your ISP provided.
 [/INDENT]
I have port 51820 directed to my PC's static LAN ip address on same  port & port open for UDP on my PC's firewall. Is that  YOUR_SERVER_IP_ADDRESS necessary?
 I then tried the guide at [How to Set Up WireGuard VPN Client on Android Phone]("https://tech.serhatteker.com/post/2021-01/how-to-set-up-wireguard-client-on-android/") but Wireguard doesn't seem to work.
 Here is wg0.conf:
```
[Interface] 
Address = 10.0.0.1/24 
SaveConfig = true 
PostUp = iptables -A FORWARD -i %i -j ACCEPT; iptables -t nat -A POSTROUTING -o enp2s0 -j MASQUERADE PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -t nat -D POSTROUTING -o enp2s0 -j MASQUERADE 
ListenPort = 51820 
PrivateKey = ***...***

 [Peer] 
PublicKey = ***...*** 
AllowedIPs = 10.220.0.2/32 Endpoint = 92.24.27.85:54160


``` 
Here is mobile.conf:
```
[Interface] 
PrivateKey = ***...*** 
Address = 10.220.0.2/24 
DNS = 1.1.1.1, 1.0.0.1

 [Peer] 
PublicKey = ***...*** 
Endpoint = rose-server.duckdns.org:51820 
AllowedIPs = 0.0.0.0/0

 
```

Presumably the Peer section in wg0.conf comes from the 'sudo wg set  wg0 peer MOBILE_CLIENT_PUBLIC_KEY allowed-ips 10.220.0.2' command in the  'How to setup Wireguard on Android' web page. I don't understand why  that section has the line 'Endpoint = 92.24.27.85:54160' i.e. why is  54160 used?

 Here is extract from ufw log:
 May 15 13:16:37 Desktop kernel: [199339.807699] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=1.1.1.1 LEN=68 TOS=0x00 PREC=0x00 TTL=63 ID=6780 DF PROTO=UDP SPT=41077 DPT=53 LEN=48 
May 15 13:16:37 Desktop kernel: [199339.807756] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=157.240.221.24 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=7555 DF PROTO=TCP SPT=36682 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0 
May 15 13:16:37 Desktop kernel: [199339.869709] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=1.1.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=63 ID=6787 DF PROTO=UDP SPT=40210 DPT=53 LEN=42 
May 15 13:16:37 Desktop kernel: [199339.879707] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=1.1.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=6788 DF PROTO=UDP SPT=50850 DPT=53 LEN=40 
May 15 13:16:37 Desktop kernel: [199339.903631] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=216.58.212.196 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=52875 DF PROTO=TCP SPT=52620 DPT=80 WINDOW=65535 RES=0x00 SYN URGP=0 
May 15 13:16:37 Desktop kernel: [199339.915724] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=173.194.76.188 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=37140 DF PROTO=TCP SPT=60794 DPT=5228 WINDOW=65535 RES=0x00 SYN URGP=0 
May 15 13:16:37 Desktop kernel: [199339.956181] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=157.240.221.18 LEN=1260 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=57701 DPT=443 LEN=1240 
May 15 13:16:37 Desktop kernel: [199339.965995] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=1.1.1.1 LEN=64 TOS=0x00 PREC=0x00 TTL=63 ID=6802 DF PROTO=UDP SPT=26393 DPT=53 LEN=44 
May 15 13:16:37 Desktop kernel: [199339.967239] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=157.240.221.18 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=59938 DF PROTO=TCP SPT=54862 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0 
May 15 13:16:37 Desktop kernel: [199339.970614] [UFW BLOCK] IN=wg0 OUT=enp2s0 MAC= SRC=10.220.0.2 DST=157.240.221.18 LEN=99 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=57701 DPT=443 LEN=79 
May 15 13:17:35 Desktop kernel: [199398.281782] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:54:af:97:bd:f3:28:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
May 15 13:19:40 Desktop kernel: [199523.212847] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:54:af:97:bd:f3:28:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
May 15 13:21:45 Desktop kernel: [199648.233911] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:54:af:97:bd:f3:28:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
May 15 13:23:50 Desktop kernel: [199773.205319] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:54:af:97:bd:f3:28:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
 
Here is extract from wireguard log:
 --------- beginning of main
05-15 13:16:34.685 11302 11302 E reguard.androi: Not starting debugger since process cannot load the jdwp agent.
05-15 13:16:34.738 11302 11302 W reguard.androi: JIT profile information will not be recorded: profile file does not exist.
05-15 13:16:34.738 11302 11302 I chatty  : uid=10242(com.wireguard.android) identical 1 line
05-15 13:16:34.738 11302 11302 W reguard.androi: JIT profile information will not be recorded: profile file does not exist.
05-15 13:16:34.747 11302 11302 I LoadedApk: No resource references to update in package com.blackview
05-15 13:16:34.747 11302 11302 D NetworkSecurityConfig: No Network Security Config specified, using platform default
05-15 13:16:34.748 11302 11302 D NetworkSecurityConfig: No Network Security Config specified, using platform default
05-15 13:16:34.800 11302 11302 E libc    : Access denied finding property "ro.vendor.pref_scale_resolution"
05-15 13:16:34.812 11302 11302 I WireGuard/Application: WireGuard/1.0.20230512 (Android 30; arm64-v8a; te855_dk_dk030_71_r0_eea; wheatek A95; Blackview/A95_EEA/A95:11/RP1A.200720.011/1659490719:user/release-keys)
05-15 13:16:34.835 11302 11330 D libMEOW : meow reload base cfg path: na
05-15 13:16:34.835 11302 11330 D libMEOW : meow reload overlay cfg path: na
05-15 13:16:34.837 11302 11330 D libMEOW : applied 1 plugins for [com.wireguard.android]:
05-15 13:16:34.837 11302 11330 D libMEOW :   plugin 1: [libMEOW_gift.so]:
--------- beginning of events
05-15 13:16:34.848 11302 11302 I auditd  : type=1400 audit(0.0:3299242): avc: denied { search } for comm="DefaultDispatch" name="mm" dev="sysfs" ino=5710 scontext=u:r:untrusted_app:s0:c242,c256,c512,c768 tcontext=u:object_r:sysfs_mm:s0 tclass=dir permissive=0 app=com.wireguard.android
05-15 13:16:34.848 11302 11302 W DefaultDispatch: type=1400 audit(0.0:3299242): avc: denied { search } for name="mm" dev="sysfs" ino=5710 scontext=u:r:untrusted_app:s0:c242,c256,c512,c768 tcontext=u:object_r:sysfs_mm:s0 tclass=dir permissive=0 app=com.wireguard.android
05-15 13:16:34.848 11302 11302 W reguard.androi: Accessing hidden field Ljava/util/Collections$SynchronizedCollection;->mutex:Ljava/lang/Object; (greylist-max-o, reflection, denied)
05-15 13:16:34.848 11302 11302 W reguard.androi: Accessing hidden method Ljava/util/Collections$SynchronizedSet;-><init>(Ljava/util/Set;Ljava/lang/Object;)V (greylist-max-o, reflection, denied)
05-15 13:16:34.848 11302 11302 W reguard.androi: Accessing hidden method Ljava/util/Collections$SynchronizedCollection;-><init>(Ljava/util/Collection;Ljava/lang/Object;)V (greylist-max-o, reflection, denied)
05-15 13:16:34.853 11302 11302 D AppCompatDelegate: Checking for metadata for AppLocalesMetadataHolderService : Service not found
05-15 13:16:34.915 11302 11302 I wm_on_create_called: [72334417,com.wireguard.android.activity.MainActivity,performCreate]
05-15 13:16:34.961 11302 11302 I wm_on_start_called: [72334417,com.wireguard.android.activity.MainActivity,handleStartActivity]
05-15 13:16:34.963 11302 11302 I wm_on_resume_called: [72334417,com.wireguard.android.activity.MainActivity,RESUME_ACTIVITY]
05-15 13:16:34.968 11302 11302 I SurfaceFactory: [static] sSurfaceFactory = com.mediatek.view.impl.SurfaceFactoryImpl@43bbb11
05-15 13:16:34.975 11302 11302 D ViewRootImpl[MainActivity]: hardware acceleration = true , fakeHwAccelerated = false, sRendererDisabled = false, forceHwAccelerated = false, sSystemRendererDisabled = false
05-15 13:16:34.979 11302 11302 D libMEOW : applied 1 plugins for [com.wireguard.android]:
05-15 13:16:34.979 11302 11302 D libMEOW :   plugin 1: [libMEOW_gift.so]:
05-15 13:16:34.980 11302 11302 I InputTransport: Create ARC handle: 0xb4000070452e72e0
05-15 13:16:34.981 11302 11302 V PhoneWindow: DecorView setVisiblity: visibility = 0, Parent = android.view.ViewRootImpl@8ff74d, this = DecorView@d33f202[MainActivity]
05-15 13:16:34.988 11302 11302 I wm_on_top_resumed_gained_called: [72334417,com.wireguard.android.activity.MainActivity,topStateChangedWhenResumed]
05-15 13:16:35.008 11302 11328 D libMEOW : applied 1 plugins for [com.wireguard.android]:
05-15 13:16:35.008 11302 11328 D libMEOW :   plugin 1: [libMEOW_gift.so]:
05-15 13:16:35.018 11302 11328 I libMEOW_gift: ctx:0xb400007175385818, ARC not Enabled.
05-15 13:16:35.031 11302 11328 E ion     : ioctl c0044901 failed with code -1: Invalid argument
05-15 13:16:36.922 11302 11327 I WireGuard/GoBackend: Bringing tunnel Desktop UP
05-15 13:16:36.922 11302 11327 D WireGuard/GoBackend: Requesting to start VpnService
05-15 13:16:37.040 11302 11302 I auditd  : type=1400 audit(0.0:3299243): avc: denied { read } for comm="DefaultDispatch" name="somaxconn" dev="proc" ino=14663658 scontext=u:r:untrusted_app:s0:c242,c256,c512,c768 tcontext=u:object_r:proc_net:s0 tclass=file permissive=0 app=com.wireguard.android
05-15 13:16:37.040 11302 11302 W DefaultDispatch: type=1400 audit(0.0:3299243): avc: denied { read } for name="somaxconn" dev="proc" ino=14663658 scontext=u:r:untrusted_app:s0:c242,c256,c512,c768 tcontext=u:object_r:proc_net:s0 tclass=file permissive=0 app=com.wireguard.android
05-15 13:16:37.041 11302 11327 D WireGuard/GoBackend: Go backend 2163620
05-15 13:16:37.042 11302 11327 D WireGuard/GoBackend/Desktop: Attaching to interface tun0
05-15 13:16:37.042 11302 11327 D WireGuard/GoBackend/Desktop: UAPI: Updating private key
05-15 13:16:37.042 11302 11327 D WireGuard/GoBackend/Desktop: UAPI: Removing all peers
05-15 13:16:37.043 11302 11327 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - UAPI: Created
05-15 13:16:37.043 11302 11327 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - UAPI: Adding allowedip
05-15 13:16:37.043 11302 11327 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - UAPI: Updating endpoint
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: handshake worker 5 - started
05-15 13:16:37.043 11302 11366 D WireGuard/GoBackend/Desktop: Routine: handshake worker 3 - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: encryption worker 4 - started
05-15 13:16:37.043 11302 11365 D WireGuard/GoBackend/Desktop: Routine: handshake worker 7 - started
05-15 13:16:37.043 11302 11363 D WireGuard/GoBackend/Desktop: Routine: decryption worker 7 - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: decryption worker 4 - started
05-15 13:16:37.043 11302 11366 D WireGuard/GoBackend/Desktop: Routine: decryption worker 2 - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: handshake worker 4 - started
05-15 13:16:37.043 11302 11365 D WireGuard/GoBackend/Desktop: Routine: encryption worker 3 - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: encryption worker 5 - started
05-15 13:16:37.043 11302 11365 D WireGuard/GoBackend/Desktop: Routine: handshake worker 2 - started
05-15 13:16:37.043 11302 11365 D WireGuard/GoBackend/Desktop: Routine: handshake worker 6 - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: decryption worker 5 - started
05-15 13:16:37.043 11302 11365 D WireGuard/GoBackend/Desktop: Routine: encryption worker 7 - started
05-15 13:16:37.043 11302 11365 D WireGuard/GoBackend/Desktop: Routine: handshake worker 8 - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: encryption worker 6 - started
05-15 13:16:37.043 11302 11365 D WireGuard/GoBackend/Desktop: Routine: TUN reader - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: encryption worker 8 - started
05-15 13:16:37.043 11302 11363 D WireGuard/GoBackend/Desktop: Routine: encryption worker 1 - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: decryption worker 1 - started
05-15 13:16:37.043 11302 11335 D WireGuard/GoBackend/Desktop: Routine: event worker - started
05-15 13:16:37.043 11302 11331 D WireGuard/GoBackend/Desktop: Routine: encryption worker 2 - started
05-15 13:16:37.043 11302 11367 D WireGuard/GoBackend/Desktop: Routine: decryption worker 6 - started
05-15 13:16:37.043 11302 11363 D WireGuard/GoBackend/Desktop: Routine: handshake worker 1 - started
05-15 13:16:37.043 11302 11364 D WireGuard/GoBackend/Desktop: Routine: decryption worker 8 - started
05-15 13:16:37.043 11302 11366 D WireGuard/GoBackend/Desktop: Routine: decryption worker 3 - started
05-15 13:16:37.044 11302 11327 D WireGuard/GoBackend/Desktop: UDP bind has been updated
05-15 13:16:37.044 11302 11366 D WireGuard/GoBackend/Desktop: Routine: receive incoming v4 - started
05-15 13:16:37.044 11302 11327 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - Starting
05-15 13:16:37.044 11302 11364 D WireGuard/GoBackend/Desktop: Routine: receive incoming v6 - started
05-15 13:16:37.044 11302 11368 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - Routine: sequential sender - started
05-15 13:16:37.044 11302 11366 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - Routine: sequential receiver - started
05-15 13:16:37.044 11302 11327 D WireGuard/GoBackend/Desktop: Interface state was Down, requested Up, now Up
05-15 13:16:37.045 11302 11327 D WireGuard/GoBackend/Desktop: Device started
05-15 13:16:37.079 11302 11335 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - Sending handshake initiation
05-15 13:16:37.085 11302 11335 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - Received handshake response
05-15 13:16:38.843 11302 11302 I menu_item_selected: [0,Settings]
05-15 13:16:38.853 11302 11302 I wm_on_top_resumed_lost_called: [72334417,com.wireguard.android.activity.MainActivity,topStateChangedWhenResumed]
05-15 13:16:38.854 11302 11302 I wm_on_paused_called: [72334417,com.wireguard.android.activity.MainActivity,performPause]
05-15 13:16:38.867 11302 11420 D libMEOW : applied 1 plugins for [com.wireguard.android]:
05-15 13:16:38.867 11302 11420 D libMEOW :   plugin 1: [libMEOW_gift.so]:
05-15 13:16:38.873 11302 11302 I wm_on_create_called: [12564124,com.wireguard.android.activity.SettingsActivity,performCreate]
05-15 13:16:38.904 11302 11302 I wm_on_start_called: [12564124,com.wireguard.android.activity.SettingsActivity,handleStartActivity]
05-15 13:16:38.905 11302 11302 I wm_on_resume_called: [12564124,com.wireguard.android.activity.SettingsActivity,RESUME_ACTIVITY]
05-15 13:16:38.905 11302 11302 V PhoneWindow: DecorView setVisiblity: visibility = 4, Parent = null, this = DecorView@7749b56[]
05-15 13:16:38.907 11302 11302 D ViewRootImpl[SettingsActivity]: hardware acceleration = true , fakeHwAccelerated = false, sRendererDisabled = false, forceHwAccelerated = false, sSystemRendererDisabled = false
05-15 13:16:38.910 11302 11302 I InputTransport: Create ARC handle: 0xb40000704530d260
05-15 13:16:38.911 11302 11302 V PhoneWindow: DecorView setVisiblity: visibility = 0, Parent = android.view.ViewRootImpl@78723ad, this = DecorView@7749b56[SettingsActivity]
05-15 13:16:38.916 11302 11302 I wm_on_top_resumed_gained_called: [12564124,com.wireguard.android.activity.SettingsActivity,topStateChangedWhenResumed]
05-15 13:16:39.203 11302 11302 I wm_on_stop_called: [72334417,com.wireguard.android.activity.MainActivity,STOP_ACTIVITY_ITEM]
05-15 13:16:39.206 11302 11302 V PhoneWindow: DecorView setVisiblity: visibility = 4, Parent = android.view.ViewRootImpl@8ff74d, this = DecorView@d33f202[MainActivity]
05-15 13:16:40.511 11302 11422 D ProfileInstaller: Installing profile for com.wireguard.android
05-15 13:16:44.550 11302 11302 I wm_on_top_resumed_lost_called: [12564124,com.wireguard.android.activity.SettingsActivity,topStateChangedWhenResumed]
05-15 13:16:44.551 11302 11302 I wm_on_paused_called: [12564124,com.wireguard.android.activity.SettingsActivity,performPause]
05-15 13:16:44.559 11302 11425 D libMEOW : applied 1 plugins for [com.wireguard.android]:
05-15 13:16:44.559 11302 11425 D libMEOW :   plugin 1: [libMEOW_gift.so]:
05-15 13:16:44.578 11302 11302 I wm_on_create_called: [4101607,com.wireguard.android.activity.LogViewerActivity,performCreate]
05-15 13:16:44.580 11302 11302 I wm_on_start_called: [4101607,com.wireguard.android.activity.LogViewerActivity,handleStartActivity]
05-15 13:16:44.581 11302 11302 I wm_on_resume_called: [4101607,com.wireguard.android.activity.LogViewerActivity,RESUME_ACTIVITY]
05-15 13:16:44.581 11302 11302 V PhoneWindow: DecorView setVisiblity: visibility = 4, Parent = null, this = DecorView@6a78029[]
05-15 13:16:44.582 11302 11302 D ViewRootImpl[LogViewerActivity]: hardware acceleration = true , fakeHwAccelerated = false, sRendererDisabled = false, forceHwAccelerated = false, sSystemRendererDisabled = false
05-15 13:16:44.586 11302 11302 I InputTransport: Create ARC handle: 0xb400007045303930
05-15 13:16:44.586 11302 11302 V PhoneWindow: DecorView setVisiblity: visibility = 0, Parent = android.view.ViewRootImpl@194e0dc, this = DecorView@6a78029[LogViewerActivity]
05-15 13:16:44.592 11302 11302 I wm_on_top_resumed_gained_called: [4101607,com.wireguard.android.activity.LogViewerActivity,topStateChangedWhenResumed]
05-15 13:16:44.834 11302 11302 I wm_on_stop_called: [12564124,com.wireguard.android.activity.SettingsActivity,STOP_ACTIVITY_ITEM]
05-15 13:16:44.835 11302 11302 V PhoneWindow: DecorView setVisiblity: visibility = 4, Parent = android.view.ViewRootImpl@78723ad, this = DecorView@7749b56[SettingsActivity]
05-15 13:16:51.203 11302 11363 D WireGuard/GoBackend/Desktop: peer(UdpJ&#8230;gwlw) - Receiving keepalive packet
05-15 13:16:52.099 11302 11302 I menu_item_selected: [0,Export log file]

---

### Post by mIk3_08 on 2023-05-17
I have tried this guide and it was a success on my end. I just follow  the instructions thoroughly on my system and works perfectly. 
If you are interested here's the link. [Click here]("https://vladtalks.tech/vpn/setup-wireguard-on-android").
Regards and cheers

---

