---
title: "Huawei E1550 modem intermittent connection ubuntu 10.10"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by cloube on 2011-02-02
[SIZE=2]I'm using Huawei modem E1550 .my problem is the connection for the modem is intermittently sometime can connect to the network and sometime can't . i've tried setting on Network connection GUI and also the wvdial . both the connection can work but the problem is the connection is intermittent. i try to search forum and change the setting in /etc/ppp/options as below

[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
 
and try change my setting  to[/SIZE]

[FONT=Verdana][SIZE=2]# [COLOR=Blue]replacedefaultroute

[COLOR=Black]and also change ipcp max failure setting from 30 until 20 (currently and stil trying)

[/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]# Set the maximum number of [COLOR=Blue]IPCP[/COLOR] configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).

[COLOR=Blue]ipcp-max-failure 30[/COLOR]
[/SIZE][/FONT][SIZE=2]
but the connection is stil intermittent.[/SIZE]
[SIZE=2]
the last step i try to do is try to create a pppconfig manually refering to  link below

[http://ubuntuforums.org/showpost.php?p=9223400&postcount=7](http://ubuntuforums.org/showpost.php?p=9223400&postcount=7)

but after i finish the configuration i can't run  #sudo pon me 
and i reboot the pc. after reboot , i try to connect using wvdial and it succeed[/SIZE]..
[SIZE=2]
below are the logs i capture from the kernel[/SIZE]

Feb  2 22:53:20 Positive pppd[1845]: pppd 2.4.5 started by root, uid 0
Feb  2 22:53:20 Positive pppd[1845]: speed 1843200 not supported
Feb  2 22:53:20 Positive pppd[1845]: Using interface ppp0
Feb  2 22:53:20 Positive pppd[1845]: Connect: ppp0 <--> /dev/ttyUSB0
Feb  2 22:53:20 Positive pppd[1845]: CHAP authentication succeeded
Feb  2 22:53:20 Positive pppd[1845]: CHAP authentication succeeded
Feb  2 22:53:20 Positive kernel: [  190.762629] PPP BSD Compression module registered
Feb  2 22:53:20 Positive kernel: [  190.804192] PPP Deflate Compression module registered
Feb  2 22:53:22 Positive pppd[1845]: Could not determine remote IP address: defaulting to 10.64.64.64
Feb  2 22:53:22 Positive pppd[1845]: local  IP address 10.177.91.104
Feb  2 22:53:22 Positive pppd[1845]: remote IP address 10.64.64.64
Feb  2 22:53:22 Positive pppd[1845]: primary   DNS address 203.82.64.129
Feb  2 22:53:22 Positive pppd[1845]: secondary DNS address 203.82.64.145

[SIZE=2]
and from the terminal[/SIZE]

@Positive:~$ sudo wvdial celcom3g
[sudo] password for syafiq: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
@Positive:~$ sudo wvdial celcom3g
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Feb  2 22:53:20 2011
--> Pid of pppd: 1845
--> pppd: 0&#1331;
--> Using interface ppp0
--> pppd: 0&#1331;
--> pppd: 0&#1331;
--> pppd: 0&#1331;
--> pppd: 0&#1331;
--> pppd: 0&#1331;
--> pppd: 0&#1331;
--> local  IP address 10.177.91.104
--> pppd: 0&#1331;
--> remote IP address 10.64.64.64
--> pppd: 0&#1331;
--> primary   DNS address 203.82.64.129
--> pppd: 0&#1331;
--> secondary DNS address 203.82.64.145
--> pppd: 0&#1331;
[SIZE=2]

please give suggestion on what other things i can do to solve this intermittent problem .any idea??[/SIZE]

---

### Post by cloube on 2011-02-03
i just got quite constant connection when using the setting via pppdconfig.. from the previous setting, i change to chap "authentication" and so far it helps . but my connection via wvdial still intermittent. i change the configuration in the /etc/ppp/options file to enabling "chap" authentication and disable the "pap"



# Require the peer to authenticate itself using PAP.
#+pap

# Don't agree to authenticate using PAP.
#-pap

# Require the peer to authenticate itself using CHAP [Cryptographic
# Handshake Authentication Protocol] authentication.
+chap

# Don't agree to authenticate using CHAP.
#-chap


for the wvdial connection normally after the connection succeed when using
@Positive:~$ sudo pon cell

the connection using wvdial will succeed..but if conneted randomly before connect using sudo pon cell,the connection is intermittent..if any of the ubuntu gurus know about it maybe can help give ideas on why this problem happen or where can i check to further investigate about this problem...

---

