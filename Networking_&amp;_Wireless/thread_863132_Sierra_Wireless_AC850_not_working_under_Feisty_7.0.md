---
title: "Sierra Wireless AC850 not working under Feisty 7.04"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by achim_59 on 2008-07-18
I have a Sierra Wireless AC850 that I'd really like to get working with my HP nx6325. I'm using Feisty Fawn 7.04.

I have trawled a number of forums and various other sites. I cobbled things together. My chatscript got as far as the "ATZ" init before my attempts hit a wall.

I'm mostly away from home (working), so at present I only have the UMTS connection to the Internet and that's only working under WinXP. When I'm at home I'll use the DSL connection & Ubuntu but for the moment I'm stuck with switching back and forth.

Here's what I've got so far:

/etc/udev/rules.d/99-aircard.rules

```


# Original suggested script
# BUS=="pcmcia", SYSFS{card_id}=="0x0710", NAME="umts", SYMLINK="tts/umts", RUN+="/usr/local/bin/umtsinit"
# If correct, should add the pin for umts card init
BUS=="pcmcia", SYSFS{card_id}=="0x0710", NAME="umts", SYMLINK="tts/umts", RUN+="/usr/local/bin/eplusinit"

```

pccardctl give the following....

```

Socket 0:
product info: "Sierra Wireless", "AC850", "3G Network Adapter", "R1"
manfid: 0x0192, 0x0710
function: 2 (serial)


```

/usr/local/bin/eplusinit....

```

#!/bin/sh
# 20060517
# Daniel Aubry
# SyGroup GmbH
# Version 0.1
# Initscript fuer Sierra Wireless Karte mit pcmciautils
# benoetigt catty http://catty.sourceforge.net/ oder http://debian.syhosting.ch/software/....13-3_i386.deb


sleep 5 && (
. /etc/profile

PIN="4269"

antwort=`catty -r0 -d /dev/umts -b 460800 -w "\nAT+CPIN=\"$PIN\"\n" | tail -n1`
signal=`catty -r 0 -d /dev/umts -b 460800 -w "\nAT+CSQ\n" | grep CSQ: | cut -d" " -f2`
echo "Rueckmeldung vom Modem: $antwort"
echo "Signalqualitaet: $signal" )

```

/etc/ppp/peers/eplus...

```

hide-password 
noauth
debug
-detach
/dev/umts
460800
crtscts
lock
defaultroute
mtu 1500
mru 1500
debug
idle 300
noauth
noipdefault
novj
#
#Added: The following 4 lines should disable ppp compression.
nobsdcomp
novjccomp
nopcomp
noaccomp
#
nomagic
user eplus
connect '/usr/sbin/chat -v -f /etc/chatscripts/epluschat'

```


/etc/chatscripts....

```


TIMEOUT 240
ABORT BUSY
ABORT 'NO CARRIER'
ABORT VOICE
ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
ABORT ERROR
# modeminit
'' ATZ
OK "ATE0V1"
# ispnumber
OK "ATD*99#"
# ispconnect
"CONNECT" ""


```

Have I forgotten something?
When I try pon I get....

tail /var/log/syslog....

```

root@hp-laptop:/etc/chatscripts# pon eplus
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/umts
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x81fb730> <pcomp> <accomp>]
sent [LCP ConfRej id=0x0 <magic 0x81fb730>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MD5> <pcomp> <accomp>]
sent [LCP ConfNak id=0x1 <auth pap>]
rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <auth pap> <pcomp> <accomp>]
sent [LCP ConfAck id=0x2 <asyncmap 0x0> <auth pap> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x0]
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
sent [PAP AuthReq id=0x1 user="eplus" password=<hidden>]
rcvd [LCP DiscReq id=0x3 magic=0x81fb730]
rcvd [LCP EchoRep id=0x0 magic=0x81fb730 00 00 00 00]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0>]
rcvd [LCP ProtRej id=0x4 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Modem hangup
Connection terminated.

```

I'm wondering if the fact that I get "function: 2 (serial)" with pccardctl has anything to do with it. The ubutu help that I got onto suggested that I should get something like: "function: 6 (network)" instead.

I'll post a new thread when I can (and if I need to).

Many thanks for any help that anyone can give.

Achim

P.S. One odd thing: when I boot up, the splash screen says it's starting kubuntu but when I log in I get the Gnome desktop (which I prefer anyway) rather than KDE. Just thought I'd mention it, because it's a bit odd.

---

### Post by achim_59 on 2008-07-21
bump?

---

### Post by achim_59 on 2008-07-22
Once more: [COLOR="Red"]**bump**[/COLOR]. Anyone?

P.S. Upgraded to Gutsy today!

---

### Post by achim_59 on 2008-07-23
I'll try one more **[COLOR="Red"]bump[/COLOR]** and add a little more info....

Firstly, I've added etc/ppp/peers/eplus to the info in the original post. 

Secondly, I upgraded to Gusty and re-installed the firmware before giving it another try.

Thirdly, I checked comments in another forum help. This suggested turning off the ppp compression. I added that to etc/ppp/peers/eplus. The 4 lines I added are indicated with a comment. The result was sadly exactly the same. The error I get still refers to a rejection due to the compression protocol. 

I have to confess that I don't really know what it means and if this doesn't elicit a response, I guess I'm back to hunting on the web for details.

If anyone has even a *clue* as to what the problem is, I'd be ever so grateful for your insight.

Achim

---

### Post by achim_59 on 2008-08-06
Another [COLOR="Red"]**BUMP**[/COLOR] to see if something can't be done.

I've also tried once again by checking other forums... after a week of being held away from the problem with work and other programming tasks.

One forum suggested that the APN (access point name) was not sent correctly. I tried several variations in /ets/ppp/peers/eplus based on what that user did:

```

# user = eplus
# user = eplus@internet.eplus.de
# user = umts@internet.eplus.de
user = umts

```

this was based on what I have in my etc/ppp/pap-secrets file:

```

umts                                    *umts
eplus * eplus

```

That in turn was taken from the eplus (service provider) help.

So now does anyone have an idea?? PLEASE HELP! I'm having to use WinXP (hate it, hate it, hate it) for all my internet access when I'm away from home (which is 4 to 5 days a week).

Achim

---

### Post by achim_59 on 2008-08-06
[color="red"]***bump***[/color]

---

### Post by achim_59 on 2008-08-11
[COLOR="Red"]**Bump** yet again.[/COLOR]
Well I seem to have gotten a tiny bit further. I found the option "noccp" which I have added to my /etc/ppp/peers/eplus. I also tried a number of different configurations for my chat script but it all boiled down to the following in /var/log/syslog

```

Aug 11 20:40:10 hp-laptop chat[6203]: OK
Aug 11 20:40:10 hp-laptop chat[6203]:  -- got it 
Aug 11 20:40:10 hp-laptop chat[6203]: send (ATE0V1^M)
Aug 11 20:40:10 hp-laptop chat[6203]: expect (OK)
Aug 11 20:40:10 hp-laptop chat[6203]: ^M
Aug 11 20:40:10 hp-laptop chat[6203]: ATE0V1^M^M
Aug 11 20:40:10 hp-laptop chat[6203]: OK
Aug 11 20:40:10 hp-laptop chat[6203]:  -- got it 
Aug 11 20:40:10 hp-laptop chat[6203]: send (AT+CPIN='4269'^M)
Aug 11 20:40:10 hp-laptop chat[6203]: expect (OK)
Aug 11 20:40:10 hp-laptop chat[6203]: ^M
Aug 11 20:40:10 hp-laptop chat[6203]: ^M
Aug 11 20:40:10 hp-laptop chat[6203]: ERROR
Aug 11 20:40:10 hp-laptop chat[6203]:  -- failed
Aug 11 20:40:10 hp-laptop chat[6203]: Failed (ERROR)
Aug 11 20:40:10 hp-laptop pppd[6200]: Connect script failed
Aug 11 20:40:11 hp-laptop pppd[6200]: Exit.
Aug 11 20:41:56 hp-laptop firmware_helper[6206]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:30:00.0' with driver 'bcm43xx'
Aug 11 20:41:56 hp-laptop kernel: [ 3208.700000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 11 20:41:58 hp-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 

```

I' assume from this that my pin is not being accepted. What I find susupect (verdaechtig) is the last few lines about "bcm43xx_microcode5.fw" not being available. Is bcm43xx_microcode a package that I should have? I did a check and there is a bcm43xx_microcode package that has indeed not been installed.

I'm faced with using windoze (ugh) at the  moment, so I cannot simply switch over and try an install... I need a cable!!!

As the Germans say: "Egal!" Eventually I'll solve the problem and to the hundred or so that have read this without even bothering to give a hint or even say "geez I'm sorry but I can't help," or whatever: YOU DON'T MAKE ME FEEL LIKE A MEMBER OF A COMMUNITY!!

I think I'll spend a bit of time seeing if I can help some other people before I go to bed.

Achim

---

### Post by achim_59 on 2008-08-12
OK, I'm feeling better now... sort of, anyway. I've come one step further.

At work today I latched the laptop onto the lan and used the package manager to install bcm433xx-fwcutter (the firmware package for broadcom wireless). My pin is now being accepted. I'm not sure what this has to do with the umts card but, what the hell, who cares? It seems to have done some good.

However, I am now stuck at the next step... AT_OPSYS. I tried 3,2 (umts with gprs fallback) and also 1,2 (gprs only) but the result was precisely the same. /var/log/syslog now contains the following

```

achim@hp-laptop:~$ tail -20 /var/log/syslog
Aug 12 22:33:29 hp-laptop chat[6067]: expect (OK)
Aug 12 22:33:29 hp-laptop chat[6067]: ^M
Aug 12 22:33:29 hp-laptop chat[6067]: ATE0V1^M^M
Aug 12 22:33:29 hp-laptop chat[6067]: OK
Aug 12 22:33:29 hp-laptop chat[6067]:  -- got it 
Aug 12 22:33:29 hp-laptop chat[6067]: send (AT+CPIN=\"4269\"^M)
Aug 12 22:33:29 hp-laptop chat[6067]: expect (OK)
Aug 12 22:33:29 hp-laptop chat[6067]: ^M
Aug 12 22:33:29 hp-laptop chat[6067]: ^M
Aug 12 22:33:29 hp-laptop chat[6067]: OK
Aug 12 22:33:29 hp-laptop chat[6067]:  -- got it 
Aug 12 22:33:29 hp-laptop chat[6067]: send (AT_OPSYS=1,2^M)
Aug 12 22:33:29 hp-laptop chat[6067]: expect (OK)
Aug 12 22:33:29 hp-laptop chat[6067]: ^M
Aug 12 22:33:29 hp-laptop chat[6067]: ^M
Aug 12 22:33:29 hp-laptop chat[6067]: ERROR
Aug 12 22:33:29 hp-laptop chat[6067]:  -- failed
Aug 12 22:33:29 hp-laptop chat[6067]: Failed (ERROR)
Aug 12 22:33:29 hp-laptop pppd[6064]: Connect script failed
Aug 12 22:33:30 hp-laptop pppd[6064]: Exit.

```

Is there a log that I should look at to tell me what's going on? Maybe there is some site that can inform me what the various chat commands are doing. "man chat" was no help, unfortunately.

I guess this counts as yet another bump.

Somebody please help!

Achim

---

### Post by achim_59 on 2008-08-20
I guess this is another bump. However, I have come a (very) small step further. The problem I have doesn't lie with any of the aforementioned hypotheses,but rather, as earlier mentioned, the fact that pccardctl ident returns "function: 2(serial)" rather than "function: 6 (network)". This means the device is not being recognised as a network device. I reasoned this out after reading the advice at "GlobeSurfer-UMTS_Ubuntu-Dapper_index.html".

This lead me to "http://www.draisberghof.de/usb_modeswitch/" where I am reading at the moment. Somewhere along the line my device is not being correctly recognised. I'm thinking about installing the switching software but am also hesitant, because others (whose advice I have already taken) have indicated that it shouldn't be necessary.

Any ideas out there?

despondently Yours,

Achim

Incidentally, my pcmcia card (sierra wireless AC850) blinks a happy green... leads me to wonder if it has a USB serial function in addition to its modem function.

---

### Post by achim_59 on 2008-08-26
***BUMP!***

Help, *please!*

I've checked the firmware, looked the at the configs, checked the chatscript, etc, etc, etc.

Nothing tells me why my card is not being recognised as a network device. "pccardctl ident" gives the same old message: function: 2 (serial).... weep!

Can't *somebody* out there tell me what's going on? Does it have to do with the machine (HP nx6325)? Should I delete everything and start from scratch?

Any response would be better than the silence I've received.

Achim

---

### Post by harbaugh on 2008-08-29
I am probably going to be getting one of these cards in a couple of days.

Have you seen this page: [https://help.ubuntu.com/community/AirCard8X0?](https://help.ubuntu.com/community/AirCard8X0?)  It has
some unusual firmware setup info at the beginning?

Toni

---

### Post by achim_59 on 2008-09-01
No, haven't tried that one... thanks very much for the tip. I'll add to this reply as soon as I've had a chance to look at it... I'm at work now.

Achim

No, haven't tried that one... thanks very much for the tip. I'll add to this reply as soon as I've had a chance to look at it... I'm at work now.

Achim

-->
I couldn't wait, I just had to look! The link should have been familiar but I'd made a copy of it and used the copy on the hard-disk. I have indeed used the info at that URL and had some initial success... except for the part where *pccardctl* gives the message "function 2 (serial)".

The specified "/etc/udev/rules.d/99-aircard.rules" text contains a reference to a file "/usr/local/bin/umtsinit". This should contain a script or program for udev to run when */etc/udev restart* is executed. However, there is no mention anywhere of what should be in that script. From reading other forum info I came to the conclusion (perhaps wrongly) that it isn't really important. I initially used the scripting option to enter the PIN. I then switched to entering the PIN in the chat-script and removed the script option from the udev rule altogether.

Having said that, I have now read through the information again and have come up with a few ideas on what to try next. Failing that, there is some new info available from the Sierra people: 
[COLOR="Blue"]http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=118[/COLOR]
This describes a rather different approach which I have not tried, yet.

Something I may need to try is another laptop. The nx6325 is known for being somewhat... um... unique? That'll be the next step... I've got an old Acer Aspire 1350 (weighs a ton!) in which the card functions under win2K, so I'll give it a try on that machine with Linux if I can't get it to work on the HP machine.

Thanks again for the response, Toni.

Achim

P.S. The card itself is good... I've had this one for 2 years!

---

### Post by achim_59 on 2010-12-07
[COLOR="Red"]BUMP!![/COLOR]

I've come a long way in the past few years but still haven't managed to get the AC850 to work under Linux. I now use an IBM T43 for Linux and have come full circle. I got the compression error again but that doesn't seem to be the problem.

The compression error goes away when I add "noccp" to the ppp-script. After reading a lot of forums and related reference material I have found that the AC850 doesn't recognise the "AT_OPSYS" command at all. I removed it and hoped I would get a simple GPRS connection. 

Well... I did. Trouble is the modem hangs up as soon as the connection is made. Here is the result from /var/log/syslog:
> 
Dec 7 19:50:06 achim-laptop chat[2540]: abort on (NO CARRIER)
Dec 7 19:50:06 achim-laptop chat[2540]: abort on (NO DIALTONE)
Dec 7 19:50:06 achim-laptop chat[2540]: abort on (ERROR)
Dec 7 19:50:06 achim-laptop chat[2540]: abort on (NO ANSWER)
Dec 7 19:50:06 achim-laptop chat[2540]: abort on (BUSY)
Dec 7 19:50:06 achim-laptop chat[2540]: send (ATZ^M)
Dec 7 19:50:07 achim-laptop chat[2540]: expect (OK)
Dec 7 19:50:07 achim-laptop chat[2540]: ATZ^M^M
Dec 7 19:50:07 achim-laptop chat[2540]: OK
Dec 7 19:50:07 achim-laptop chat[2540]: -- got it
Dec 7 19:50:07 achim-laptop chat[2540]: send (ATE0V1^M)
Dec 7 19:50:07 achim-laptop chat[2540]: expect (OK)
Dec 7 19:50:07 achim-laptop chat[2540]: ^M
Dec 7 19:50:07 achim-laptop chat[2540]: ATE0V1^M^M
Dec 7 19:50:07 achim-laptop chat[2540]: OK
Dec 7 19:50:07 achim-laptop chat[2540]: -- got it
Dec 7 19:50:07 achim-laptop chat[2540]: send (AT+CGDCONT=1,"IP","internet.eplus.de","",0,0^M)
Dec 7 19:50:07 achim-laptop chat[2540]: expect (OK)
Dec 7 19:50:07 achim-laptop chat[2540]: ^M
Dec 7 19:50:07 achim-laptop chat[2540]: ^M
Dec 7 19:50:07 achim-laptop chat[2540]: OK
Dec 7 19:50:07 achim-laptop chat[2540]: -- got it
Dec 7 19:50:07 achim-laptop chat[2540]: send (ATD*99*1#^M)
Dec 7 19:50:07 achim-laptop chat[2540]: expect (CONNECT)
Dec 7 19:50:07 achim-laptop chat[2540]: ^M
Dec 7 19:50:07 achim-laptop chat[2540]: ^M
Dec 7 19:50:07 achim-laptop chat[2540]: CONNECT
Dec 7 19:50:07 achim-laptop chat[2540]: -- got it
Dec 7 19:50:07 achim-laptop chat[2540]: send (^M)
Dec 7 19:50:07 achim-laptop pppd[2536]: Script /usr/sbin/chat -v -f /etc/chatscripts/eplus finished (pid 2539), status = 0x0
Dec 7 19:50:07 achim-laptop pppd[2536]: Serial connection established.
Dec 7 19:50:07 achim-laptop pppd[2536]: using channel 3
Dec 7 19:50:07 achim-laptop NetworkManager: SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 7 19:50:07 achim-laptop NetworkManager: SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 7 19:50:07 achim-laptop pppd[2536]: Using interface ppp0
Dec 7 19:50:07 achim-laptop pppd[2536]: Connect: ppp0 <--> /dev/umts
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0x8228888> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [LCP ConfRej id=0x3 <magic 0x8228888>]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP ConfReq id=0x4 <asyncmap 0x0> <auth chap MD5> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [LCP ConfAck id=0x4 <asyncmap 0x0> <auth chap MD5> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [LCP EchoReq id=0x0 magic=0x0]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP DiscReq id=0x5 magic=0x8228888]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [CHAP Challenge id=0x1 <0c5dd2dd9a30db1dc6dd532142030509>, name = "UMTS_CHAP_SRVR"]
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [CHAP Response id=0x1 <a00984bbaeab0a552df8b36a82e29237>, name = "eplus"]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP EchoRep id=0x0 magic=0x8228888 00 00 00 00]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [CHAP Success id=0x1 ""]
Dec 7 19:50:08 achim-laptop pppd[2536]: CHAP authentication succeeded
Dec 7 19:50:08 achim-laptop pppd[2536]: CHAP authentication succeeded
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Dec 7 19:50:08 achim-laptop pppd[2536]: Modem hangup
Dec 7 19:50:08 achim-laptop pppd[2536]: Connection terminated.


So there it is. The problem seems to lie in those last few lines. In particular: "sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]", since that is the point at which the successful connection ends.

I've posted all this and more on another forum:
[http://www.linuxquestions.org/questions/showthread.php?p=4184035#post4184035](http://www.linuxquestions.org/questions/showthread.php?p=4184035#post4184035)

I'm not all that hopeful that this will ellicit a response but maybe somebody will find this information useful.

When I finally do find a solution, in whatever form, I will be sure to let you all know.

Achim

---

