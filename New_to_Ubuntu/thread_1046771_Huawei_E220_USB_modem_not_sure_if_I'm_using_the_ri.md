---
title: "Huawei E220 USB modem: not sure if I'm using the right band (UMTS or HSDPA)..."
date: 2009-01-21
forum: New to Ubuntu
---

### Post by mtl on 2009-01-21
Hello!

I have an USB modem: the famous **Huawei E220 USB modem**.
I'm a beginner with Linux. This is my problem: on Windows XP my Huawei modem automatically detected the HSDPA band (via the Dashboard) and I was able to reach nice EFFECTIVE download speeds, like 250 kiB/s... (with DAP, Azureus or simply Firefox). That was the way of functioning I wanted.

Now I switched to Xubuntu (Intrepid) 8.10 x86, and, using the *network monitor* applet on my bar, I see _that the maximum effective download speed only reaches about 60 kiB/s_... The question is this: **I'm I really on a HSDPA connection or is it only UMTS, or something else?**

I managed to successfully install the modem, compiling Aktboo"something".c and all the rest (i successfully followed your guides... thanks!).

I use *wvdial* to initialize the connection; this is bash's output:

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet.wind"
AT+CGDCONT=1,"IP","internet.wind"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Jan 21 23:56:44 2009
--> Pid of pppd: 5713
--> Using interface ppp0
--> local  IP address 151.82.10.38
--> remote IP address 10.64.64.64
--> primary   DNS address 193.70.152.25
--> secondary DNS address 193.70.192.25

```

Here are my questions:

1) Is there a way to check if I'm using the right band? Here where I live we have HSDPA (that's for sure). How can I find out if I'm using the right (fastest) band? I don't want to browse the web at the "slow" UMTS/GPRS/EDGE speeds....

2) Are there AT commands to see if I'm using the right band?

3) **Can I use AT commands in wvdial.conf to make my Huawei E220 USB modem use the HSDPA band** and finally reach the good ol' 250 kiB/s speeds like before (on Windows XP and with Huawei's dashboard)?

Come on, let us beat Windows also with these 3G connections. Help me!

Thank you Ubuntu Community, you're the best!

---

### Post by mtl on 2009-01-22
**Bump!**

Hey, does anyone know anything about AT modem commands, in particular about how to assign the correct band to the Huawei E220 via wvdial.conf?

---

