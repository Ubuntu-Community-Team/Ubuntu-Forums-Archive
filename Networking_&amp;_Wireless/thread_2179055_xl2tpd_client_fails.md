---
title: "xl2tpd client fails"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by quentin4 on 2013-10-06
Hello All - hoping if someone can assist me here.

I have the following configuration files:

I have tested this setup using Linux Mint as a client and it connects to my ISP. They use the L2TP without IPSec to give subscribers a fixed IP address.
Hence they have programmed it in such a manner that when I create a L2TP I always will receive the same IP address on the tunnel.

For the last two weeks I have been trying without any success to connect using Ubuntu LTS 64 bit server edition.
I take exactly the same configuration files and run them on Ubuntu, and I get in the error log is a message stating that I do not have authorisation to create a tunnel.

Please someone - I am not a Linux boffin, but something is weird here. Any input will be welcomed.

[COLOR=#4c1900][FONT=BellGothic BT]# /etc/xl2tpd/xl2tpd.conf[/FONT][/COLOR]

[COLOR=#000000][FONT=BellGothic BT][global]                                                                                    [/FONT][/COLOR]
[FONT=BellGothic BT][COLOR=#000000]auth file = [/COLOR][COLOR=#94006b]/etc/xl2tpd/l2tp-secrets                                     [/COLOR][COLOR=#000000]; Where our challenge secrets are[/COLOR][/FONT]
[COLOR=#000000][FONT=BellGothic BT]debug tunnel = yes                         [/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                                         ; Enable debug[/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]debug avp = yes                             ; Enable debug[/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]debug network = yes                       ; Enable debug    [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]debug packet = yes                         ; Enable debug[/FONT][/COLOR]

[FONT=BellGothic BT][COLOR=#000000][lac [/COLOR][COLOR=#0084d1]l2tp-connection[/COLOR][COLOR=#000000]]                       [/COLOR][COLOR=#000000]; VPN LAC definition[/COLOR][/FONT]
[COLOR=#000000][FONT=BellGothic BT]lns = xxx[COLOR=#c5000b].xxx.xxx.xxx[/COLOR]                   ; The IP address of our LAC[/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]redial = yes                                  ; Reconnect if disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]redial timeout = 15                        ; Wait n seconds between redials[/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]max redials = 5                            ; Give up after n consecutive failures[/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]hidden bit = yes                            ; User hidden AVP's?[/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]length bit = no                             ; Use length bit in payload? [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]require chap = no                         ; Require CHAP auth. by peer  [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]refuse chap = yes                          ; Refuse CHAP auth. by peer [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]require pap = yes                         ; Require PAP auth. by peer [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]refuse pap = no                            ; Require PAP authentication  [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]refuse authentication = no             ; Refuse authentication altogether 
[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]require authentication = yes          ;Require peer to authenticate
[/FONT][/COLOR][FONT=BellGothic BT][COLOR=#000000]name = [/COLOR][/FONT][COLOR=#C5000B][FONT=BellGothic BT]User@isp                        [/FONT][/COLOR][FONT=BellGothic BT][COLOR=#000000]; [/COLOR][/FONT][FONT=BellGothic BT][COLOR=#000000]VPN Username[/COLOR][/FONT]
[COLOR=#000000][FONT=BellGothic BT]ppp debug = yes                          ; Turn on PPP debugging
[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]pppoptfile =[/FONT][/COLOR][COLOR=#008000][FONT=BellGothic BT] /etc/ppp/options.l2tpd.[/FONT][/COLOR][COLOR=#008000][FONT=BellGothic BT]client[/FONT][/COLOR][COLOR=#008000][FONT=BellGothic BT]    [/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]; [/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]ppp options file for this lac[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]

[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT][COLOR=#94006b][SIZE=2]


#[/SIZE][/COLOR][COLOR=#94006b][SIZE=2]/etc/xl2tpd/l2tp-secrets[/SIZE][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas][FONT=BellGothic BT][SIZE=2]
# [/SIZE][/FONT][FONT=BellGothic BT][SIZE=2][https://github.com/xelerance/xl2tpd/blob/master/doc/l2tp-secrets.5](https://github.com/xelerance/xl2tpd/blob/master/doc/l2tp-secrets.5) [/SIZE][/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=BellGothic BT][COLOR=#c5000b]# [/COLOR][COLOR=#c5000b]_Secrets for authenticating l2tp tunnels_[/COLOR] [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]# The l2tp-secrets file contains challenge-response authentication information for xl2tpd, the implementation of l2tp protocol. [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]# The format of the file is derived from the pap and chap secrets file format used in pppd. The secrets file is composed of zero or # more lines with 3 fields each. Each line represents an authentication secret.  
# The 3 fields represent our hostname, the remote # hostname and the secret used in the authentication process. [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]# The [COLOR=#c5000b]first [/COLOR][COLOR=#c5000b](us)[/COLOR] field is for our hostname, a "*" may be used as a wildcard.  [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]# The [COLOR=#004586]second [/COLOR][COLOR=#004586](them)[/COLOR] field is for the remote system's hostname.  Again, a "*" may be used as a wildcard. [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]# The [COLOR=#579d1c]third [/COLOR][COLOR=#579d1c](secret)[/COLOR] field is the secret used if the previous two fields match the hostnames of the systems involved.  [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]# The secret should, ideally, be at 16 characters long (the length of an MD5 digest output), and should probably be longer to [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]# ensure sufficient security.  There is no minimum length requirement, however.[/FONT][/COLOR]

[COLOR=#000000][FONT=BellGothic BT]# [COLOR=#c5000b]_us_[/COLOR]     [COLOR=#004586]_them_[/COLOR]     [COLOR=#008000]_secret_[/COLOR][/FONT][/COLOR]
[FONT=BellGothic BT][COLOR=#c5000b][COLOR=#000000]*[/COLOR][/COLOR][COLOR=#008000][COLOR=#000000]    [/COLOR][/COLOR][COLOR=#004586]somename[/COLOR][COLOR=#008000][COLOR=#000000]    somesecret[/COLOR][/COLOR][/FONT]

[COLOR=#355e00][FONT=BellGothic BT]



#/etc/ppp/options.l2tpd.client[/FONT][/COLOR]
[FONT=BellGothic BT][COLOR=#000000]ipcp-accept-local          # pppd will accept the peer's idea of our local IP address[/COLOR][/FONT]
[COLOR=#000000][FONT=BellGothic BT]mru 1410                    # MRU is the maximum size for a received packet[/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT]mtu 1452                    # MTU is the maximum size for a transmitted packet[/FONT][/COLOR]
[FONT=BellGothic BT][COLOR=#000000]debug                         # pppd will log contents of control packets[/COLOR] - [COLOR=#c5000b]set up /etc/syslog.conf[/COLOR] [/FONT]
[COLOR=#000000][FONT=BellGothic BT][COLOR=#c5000b]refuse-eap[/COLOR]                   # [COLOR=#c5000b]pppd will not agree to authenticate itself to the peer using EAP[/COLOR] [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT][COLOR=#c5000b]refuse-chap[/COLOR]                 # [COLOR=#c5000b]pppd will not agree to authenticate itself to the peer using CHAP[/COLOR] [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT][COLOR=#c5000b]refuse-mschap[/COLOR]               # [COLOR=#c5000b]pppd will not agree to authenticate itself to the peer using MS-CHAP[/COLOR] [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT][COLOR=#c5000b]refuse-mschap-v2[/COLOR]           # [COLOR=#c5000b]pppd will not agree to authenticate itself to the peer using MS-CHAPv2[/COLOR] [/FONT][/COLOR]
[COLOR=#000000][FONT=BellGothic BT][COLOR=#004586]require-pap[/COLOR]                 # [COLOR=#004586]Requires PAP [Password Authentication Protocol] authentication[/COLOR]. 
[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]noccp                         #[/FONT][/COLOR][COLOR=#C5000B][FONT=BellGothic BT]Disable compression control if the peer is buggy[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]
[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]show-password             # When logging PAP packets[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]pppd[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT] will log[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT] the password string[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT] as well
[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]lcp-echo-failure 20       # pppd presumes peer to be dead if [/FONT][/COLOR]*n*[COLOR=#000000][FONT=BellGothic BT] LCP echo-request are not ack'd 
[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]lcp-echo-interval 50      # pppd will send an LCP echo-request frame every[/FONT][/COLOR]* n*[COLOR=#000000][FONT=BellGothic BT]seconds   
[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]asyncmap 0                 # pppd will ask the peer not to escape any control characters 
[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]nocrtscts[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                      #[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]No flow control using the RTS and CTS signals in RS-232 
[/FONT][/COLOR][COLOR=#004586][FONT=BellGothic BT]#[/FONT][/COLOR][COLOR=#004586][FONT=BellGothic BT]crtscts[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                       # [/FONT][/COLOR][COLOR=#004586][FONT=BellGothic BT]Use flow control using the RTS and CTS signals in RS-232 
[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]lock                            # pppd creates a UUCP-style lock file for exclusive access [/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT] 
[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]local[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                           # [/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]Do not use modem control lines
[/FONT][/COLOR][COLOR=#004586][FONT=BellGothic BT]#[/FONT][/COLOR][COLOR=#004586][FONT=BellGothic BT]modem[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                     # [/FONT][/COLOR][COLOR=#004586][FONT=BellGothic BT]Use the modem control lines[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT] 
[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]noauth[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                          # [/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]Do not require the peer to authenticate itself. Option is privileged[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT] 
[/FONT][/COLOR][COLOR=#004586][FONT=BellGothic BT]#auth[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                          # [/FONT][/COLOR][COLOR=#004586][FONT=BellGothic BT]The peer does have to authenticate itself
[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]noipx[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                          #[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]Disable IPXCP and IPX Protocols only required if the peer is buggy
[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]defaultroute                  # Make this the default route
[/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]nomppe-128[/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT]                 # [/FONT][/COLOR][COLOR=#c5000b][FONT=BellGothic BT]Disable 128-bit encryption with MPPE[/FONT][/COLOR][COLOR=#008000][FONT=BellGothic BT][FONT=Consolas] 

[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=BellGothic BT][COLOR=#c5000b]




#[/COLOR][COLOR=#c5000b]/etc/ppp/pap-secrets[/COLOR][/FONT][/COLOR]
[COLOR=#4b1f6f][FONT=BellGothic BT][COLOR=#000000]#[/COLOR][COLOR=#000000]user[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]_hostname_[/COLOR][COLOR=#000000]        [/COLOR][COLOR=#000000]_secret_[/COLOR][/FONT][/COLOR]
[COLOR=#000000][COLOR=#c5000b][FONT=BellGothic BT]User@isp[/FONT][/COLOR][FONT=BellGothic BT]    [/FONT][COLOR=#c5000b][FONT=BellGothic BT]*[/FONT][/COLOR][FONT=BellGothic BT]        [/FONT][COLOR=#c5000b][FONT=BellGothic BT]mysecret

[/FONT][/COLOR][/COLOR]

---

