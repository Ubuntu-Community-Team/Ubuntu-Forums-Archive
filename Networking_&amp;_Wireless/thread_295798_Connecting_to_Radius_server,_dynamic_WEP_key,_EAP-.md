---
title: "Connecting to Radius server, dynamic WEP key, EAP-TLS via xsupplicant"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by Blizzz on 2006-11-08
Hi there,

hope someone can help me here...

My university provides acces to server and internet. EAP-TLS is used, you get ab root-ca called certificate and a user certificate with password.

(btw: on windows, my colleagues import the licences, give in the password and can connect easily. So, it must work with (k)ubuntu as well, mustn't?)

What I have done is as follows:
- for all cases i imported root-ca und user certificate by konqueror
- installed xsupplicant
- tried around with the xsupplicant.conf, but always luckyless

In fact, i am trying to handle this problem for around five weeks now and i am getting kinda frustrated :(

My network part of xsupplicant.conf is like this: 

> [FONT="Courier New"]my_network
{ 
  allow_types = eap_tls

  ## method-specific parameters are kept in the method 
  eap_tls {
     user_key = "/home/arthur/BA HDH/WI0617-3.p12"
     user_key_pass = <BEGIN_PASS>**********<END_PASS>
     root_cert = "/home/arthur/BA HDH/root.pem"
     root_dir = "/home/arthur/BA HDH/"
     chunk_size = 1398
     random_file = "/dev/random/"

     session_resume = yes
  }
}[/FONT]

i start xsupplicant this way:

> sudo xsupplicant -w -dasic -i ath0 -f 

and all i get is this:

> [FONT="Courier New"]Use of <BEGIN_PASS> and <END_PASS> have been deprecated!
[STATE] Reinit state machine
[STATE] [backend_sm] REQUEST -> INITIALIZE
[STATE] [backend_sm] INITIALIZE -> IDLE
[STATE] [backend_sm] UNKNOWN -> INITIALIZE
[STATE] [backend_sm] INITIALIZE -> IDLE
[INT] Initializing socket for interface ath0..
[INT] Allmulti mode is already enabled on this device!
[INT] Interface ath0 is wireless!
[INT] Interface has no encryption capabilities, or unknown abilitites.
[INT] Interface initialized!
[CONFIG] Working from config file /etc/xsupplicant/xsupplicant.conf.
No configuration information for network "(null)" found.  Using default.
[INT] Opened socket descriptor #5
[INT] Interface ath0 is wireless!
Your card is currently set for wireless network "RZ BA-HDH".  Looking for a config.
[CONFIG] Working from config file /etc/xsupplicant/xsupplicant.conf.
Couldn't build a config for ESSID RZ BA-HDH!
[STATE] Init wireless state machine.
UNASSOCIATED -> ACTIVE_SCAN
[STATE] Reinit state machine
[STATE] [backend_sm] IDLE -> INITIALIZE
[STATE] [backend_sm] INITIALIZE -> IDLE
Scanning for wireless networks ...
[INT] Issuing active scan request for interface ath0!
[INT] Called cardif_clear_keys!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
[INT] Checking for returned SSID information....
[INT] Reaping data. (Size : 381)
000 | 14 00 15 8b 01 00 00 0f b5 c3 85 ea 00 00 00 00 | ................
010 | 00 00 00 00 11 00 1b 8b 09 00 01 00 52 5a 20 42 | ............RZ B
020 | 41 2d 48 44 48 08 00 07 8b 03 00 00 00 0c 00 05 | A-HDH...........
030 | 8b 80 74 9d 0e 01 00 00 00 08 00 01 8c 12 b3 a1 | ..t.............
040 | 07 08 00 2b 8b 00 00 00 08 64 00 21 8b 40 42 0f | ...+.....d.!.@B.
050 | 00 00 00 00 00 80 84 1e 00 00 00 00 00 60 ec 53 | .............`.S
060 | 00 00 00 00 00 c0 d8 a7 00 00 00 00 00 80 8d 5b | ...............[
070 | 00 00 00 00 00 00 1b b7 00 00 00 00 00 00 36 6e | ..............6n
080 | 01 00 00 00 00 00 51 25 02 00 00 00 00 40 54 89 | ......Q%.....@T.
090 | 00 00 00 00 00 80 a8 12 01 00 00 00 00 00 6c dc | ..............l.
0a0 | 02 00 00 00 00 80 f9 37 03 00 00 00 00 13 00 02 | .......7........
0b0 | 8c 0b 00 00 00 62 63 6e 5f 69 6e 74 3d 31 30 30 | .....bcn_int=100
0c0 | 14 00 15 8b 01 00 02 0e 35 00 71 0e 00 00 00 00 | ........5.q.....
0d0 | 00 00 00 00 0e 00 1b 8b 06 00 01 00 61 64 20 68 | ............ad h
0e0 | 6f 63 08 00 07 8b 01 00 00 00 0c 00 05 8b a0 15 | oc..............
0f0 | a5 0e 01 00 00 00 08 00 01 8c 18 b9 a1 07 08 00 | ................
100 | 2b 8b 00 00 00 08 64 00 21 8b 40 42 0f 00 00 00 | +.....d.!.@B....
110 | 00 00 80 84 1e 00 00 00 00 00 60 ec 53 00 00 00 | ..........`.S...
120 | 00 00 c0 d8 a7 00 00 00 00 00 80 8d 5b 00 00 00 | ............[...
130 | 00 00 40 54 89 00 00 00 00 00 00 1b b7 00 00 00 | ..@T............
140 | 00 00 80 a8 12 01 00 00 00 00 00 36 6e 01 00 00 | ...........6n...
150 | 00 00 00 51 25 02 00 00 00 00 00 6c dc 02 00 00 | ...Q%......l....
160 | 00 00 80 f9 37 03 00 00 00 00 13 00 02 8c 0b 00 | ....7...........
170 | 00 00 62 63 6e 5f 69 6e 74 3d 31 30 30          | ..bcn_int=100
[INT] AP MAC : 00 0f b5 c3 85 ea
[CONFIG] Found new ESSID block, adding...
[INT] ESSID : RZ BA-HDH
[INT] Quality : 18  Signal : -77   Noise : -95
[INT] IWEVCUSTOM : bcn_int=100
[INT] AP MAC : 02 0e 35 00 71 0e
[CONFIG] Found new ESSID block, adding...
[INT] ESSID : ad hoc
[INT] Quality : 24  Signal : -71   Noise : -95
[INT] IWEVCUSTOM : bcn_int=100
[INT] No valid network data!! (wireless_sm_check_globals)
[CONFIG] Checking RZ BA-HDH with Priority 255
[CONFIG] Checking ad hoc with Priority 255

[INT] Closing socket descriptor #5
Invalid network data!  (backend_sm_deinit:730)
[INT] Sending Logoff for int ath0!
No network information available.  Not sending a logoff!
[INT] Clearing keys!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
[INT] Turning off WPA support/state.
[INT] Called event_core_cleanup()!
[INT] Called cardif_linux_rtnetlink_cleanup()![/FONT]

I cancel the process by CTRL+C. If i let it run the part between "Scanning for wireless networks ..." and "[CONFIG] Checking ad hoc with Priority 255" just repeats. 

Can anyone help me with that information given? Would be great!

Kind Regards
Blizzz

EDIT:
xsupplicant version is 1.2.4.dfsg.1-(from repositories)

---

