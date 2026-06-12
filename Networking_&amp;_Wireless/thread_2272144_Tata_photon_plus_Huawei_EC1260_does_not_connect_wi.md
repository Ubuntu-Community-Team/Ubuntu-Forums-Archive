---
title: "Tata photon plus Huawei EC1260 does not connect with trusty 14.04"
date: 2015-04-04
forum: Networking &amp; Wireless
---

### Post by uma-sawant on 2015-04-04
Hi all, 

I have a tata photon+ 2G dongle ( Huawei EC1260 ). I am unable to connect it to the internet using either network manager or wvdial. Some details below. 

(1) lsusb shows that the usb is detected (12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card)

(2) Network tray shows "Tata indicom (photon+) connection" as an option. When I click on it, it tries to connect and gives up. Here is what syslog says :

```
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> Activation (ttyUSB2) starting connection 'Tata Indicom (Photon+) connection 1'
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> NetworkManager state is now CONNECTING
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> (ttyUSB2): device state change: prepare -> need-auth (reason 'none') [40 60 0]
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> (ttyUSB2): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr  3 16:38:07 uma-Lenovo-Z50-70 NetworkManager[934]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Apr  3 16:38:07 uma-Lenovo-Z50-70 ModemManager[848]: <info>  Simple connect started...
Apr  3 16:38:07 uma-Lenovo-Z50-70 ModemManager[848]: <info>  Simple connect state (4/8): Wait to get fully enabled
Apr  3 16:38:07 uma-Lenovo-Z50-70 ModemManager[848]: <info>  Simple connect state (5/8): Register
Apr  3 16:39:08 uma-Lenovo-Z50-70 NetworkManager[934]: <warn> (ttyUSB2) failed to connect modem: Network timeout
Apr  3 16:39:08 uma-Lenovo-Z50-70 NetworkManager[934]: <info> (ttyUSB2): device state change: prepare -> failed (reason 'gsm-registration-timeout') [40 120 32]
Apr  3 16:39:08 uma-Lenovo-Z50-70 NetworkManager[934]: <info> NetworkManager state is now DISCONNECTED
Apr  3 16:39:08 uma-Lenovo-Z50-70 NetworkManager[934]: <info> Marking connection 'Tata Indicom (Photon+) connection 1' invalid.
Apr  3 16:39:08 uma-Lenovo-Z50-70 NetworkManager[934]: <warn> Activation (ttyUSB2) failed for connection 'Tata Indicom (Photon+) connection 1'
Apr  3 16:39:08 uma-Lenovo-Z50-70 NetworkManager[934]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr  3 16:39:08 uma-Lenovo-Z50-70 NetworkManager[934]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
```

(3) Wvdial just waits after dialing in, doesn't connect

```
uma@uma-Lenovo-Z50-70:~/Downloads$ sudo wvdial
[sudo] password for uma: 
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 3100000
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&FUV}$}'}"}(}"i}4~
--> PPP negotiation detected.
--> Starting pppd at Fri Apr  3 16:36:15 2015
--> Pid of pppd: 13992
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> local  IP address <blanked>
--> pppd: &#65533;[7f]
--> remote IP address <blanked>
--> pppd: &#65533;[7f]
--> primary   DNS address <blanked>
--> pppd: &#65533;[7f]
--> secondary DNS address <blanked>
--> pppd: &#65533;[7f]
```

Stops at this point forever. 

I couldn't find any useful information about "gsm-registration-timeout". Can anybody guide me as to how do I debug this? I am using ubuntu 14.04 on Lenovo z50-70, 64 bit, kernel is 3.16.0-031600-generic. 

Thanks a lot for your time!
Uma

---

### Post by Vladlenin5000 on 2015-04-04
Hello and welcome.

You need a working SIM with 2G data plan and with the PIN request disabled, just in case. Then you may need to change the settings for the new connection and make sure it matches the ones from the carrier.
Apparently there's nothing wrong with the hardware detection. It just can't connect to the network.

---

### Post by uma-sawant on 2015-04-05
Hi, 

Thanks for the reply!
I am able to connect on windows without any trouble, so the 2G connection is working. This is a ubuntu-specific issue. Is there any way to get logs on a deeper level than what I got from syslog? Perhaps that will tell me more about "gsm-registration-timeout".

Best,
Uma

---

### Post by Vladlenin5000 on 2015-04-07
Your connection works in Windows because it install a driver/software which includes all the settings required for the carrier. Not the same in Ubuntu.
In Ubuntu you need to setup a connection. You can use the wizard: In standard Ubuntu or variants using the network manager, just click its icon and select new data connection or similar, under the modem. Then select country followed by network and data plan (if applicable). If you don't find yours then you must select the option for manually entering the data required, which you must know beforehand. That's all.

---

### Post by uma-sawant on 2015-04-07
I was able to resolve the issue. Apparently it couldn't accept the dns  addresses provided by photon (dunno why). I manually set to google's public dns  addresses in /etc/resolv.conf and voila! It worked! 

Thanks a ton!
Uma

---

### Post by adityaprakash on 2015-04-18
Hi Uma,

I am facing the same problem, where I am able to connect my Photon plus in Windows, but not in Ubuntu 14.04. I was able to connect the dongle earlier, but somehow it failed to connect since yesterday. I went to the file /etc/resolv.conf, but a comment in the file says that it should not be edited by hand.

Can you help me out on this issue, with a more step by step process for resolving the problem. I am a newbie to using Ubuntu as well as Linux.

Thanks,
Aditya Prakash

UPDATE: I tried to edit the /etc/resolve.conf file, and replaced the namerserver 127.0.1.1 with the two lines:
nameserver 8.8.8.8
nameserver 8.8.4.4

and then saved the changes. After that I restarted my system, and found the resolve.conf file was reset to its original content, i.e. nameserver 127.0.1.1.

Problem still not fixed.

---

