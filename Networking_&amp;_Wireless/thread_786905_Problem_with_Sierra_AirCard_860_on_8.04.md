---
title: "Problem with Sierra AirCard 860 on 8.04"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Horndog on 2008-05-08
I have a Sierra AirCard 860 and followed the howto on a new install of ubuntu 8.04, IBM T41 laptop.

[https://wiki.ubuntu.com/AirCard8X0](https://wiki.ubuntu.com/AirCard8X0)

I get this when I turn on the cards radio:


```

horndog@horndog-laptop:~$ pon ac850
/etc/chatscripts/ac850chat: 1: Permission denied
/etc/chatscripts/ac850chat: 3: TIMEOUT: not found
/etc/chatscripts/ac850chat: 5: OK: not found
/etc/chatscripts/ac850chat: 7: CONNECT: not found
Connect script failed

```
I tried root with same results:
```

horndog@horndog-laptop:~$ sudo pon ac850
/etc/chatscripts/ac850chat: 1: Permission denied
/etc/chatscripts/ac850chat: 3: TIMEOUT: not found
/etc/chatscripts/ac850chat: 5: OK: not found
/etc/chatscripts/ac850chat: 7: CONNECT: not found
Connect script failed

```

I did a google search come up with this:
```

sudo apt-get remove network-manager network-manager-gnome

```
No help

More info:
```

horndog@horndog-laptop:~$ ls /dev/um*
/dev/umts

```

This is interesting. The card is not a network device contrary to the howto
```

horndog@horndog-laptop:~$ pccardctl ident
Socket 0:
  product info: "Sierra Wireless", "AC850", "3G Network Adapter", "R1"
  manfid: 0x0192, 0x0710
  function:[color=red] 2 (serial) [/color]
Socket 1:
  no product info available

```

My syslog entry:
```

May  8 02:52:59 horndog-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
May  8 02:53:01 horndog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  8 02:53:09 horndog-laptop dhclient: No DHCPOFFERS received.
May  8 02:53:09 horndog-laptop dhclient: No working leases in persistent database - sleeping.
May  8 02:53:09 horndog-laptop dhclient: No DHCPOFFERS received.
May  8 02:53:09 horndog-laptop dhclient: No working leases in persistent database - sleeping.
May  8 02:55:52 horndog-laptop pppd[7635]: pppd 2.4.4 started by horndog, uid 1000
May  8 02:55:53 horndog-laptop pppd[7635]: Connect script failed
May  8 02:55:54 horndog-laptop pppd[7635]: Exit.
May  8 02:57:47 horndog-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255

```

Any suggestion?
Thanks

BTW I don't have any internet without this connection.
I have to boot into windows to acess the internet and drag
any files back to ubuntu with a flash drive.

[color=red]EDIT[/color]
Could it be that this is a new install and no network has ever been setup?

[color=red]EDIT2[/color]

This is the information that was requested on the IRC from "soundray"

```

ls -l /dev/umts
crw-rw---- 1 root dialout 4, 65 2008-05-09 13:50 /dev/umts

```

BTW thank soundray

---

### Post by Horndog on 2008-05-08
[color=red][size=10]Bump[/color][/size]

---

### Post by Horndog on 2008-05-08
bump one more time

---

### Post by Horndog on 2008-05-09
bump for some help please

---

### Post by Horndog on 2008-05-09
bump

---

### Post by Horndog on 2008-05-10
I give up. Apparently this AirCard requires some modem files to be installed. I don't have Internet connection to install anything.

An observation,
Ubuntu has gotten too big and therefor there is no support. Some time it's better to pay and have something that works the have nothing for free. You get what you pay for. Too bad.

---

### Post by Darrena on 2008-05-10
> **Horndog said:**
> I give up. Apparently this AirCard requires some modem files to be installed. I don't have Internet connection to install anything.

An observation,
Ubuntu has gotten too big and therefor there is no support. Some time it's better to pay and have something that works the have nothing for free. You get what you pay for. Too bad.

I will ignore the pointless rant since it almost made me not bother to reply (Note: Many people do not troll everyday so it isn't unusual to wait a couple of days for someone to answer a specific problem).

Did you copy the file to /lib/firmware?

Here are the instructions for how I got it to work:
[http://darrenalbers.com/gprsec/aircard.html](http://darrenalbers.com/gprsec/aircard.html)

Quick note:  On my T43 and T40 I had to disable the modem in the bios or the device would not be assigned a serial port.   I did not have to do this on my T61 or any other laptop so it seems specific to the T4x series.   So if you have the files named properly and in /lib/firmware then try disabling the modem in the bios and see if it is assigned a serial port.   Then either use UMTSmon or GPRSEC to connect (Make sure you stop Network Manager before you start either of those programs.   There is not need to uninstall it, just do sudo /etc/dbus-1/event.d/25NetworkManager stop from a terminal before you use your aircard.

NM 0.7 had built in support for Aircards so when it stabilizes you will no longer have to uninstall it.

---

### Post by Darrena on 2008-05-10
> **Horndog said:**
> I give up. Apparently this AirCard requires some modem files to be installed. I don't have Internet connection to install anything.

Specific to this comment, yes you need to download some firmware from Sierra Wireless.   See the link I posted above for the location.   The file is quite small so you can use Sneaker-net to get it to the PC without an internet connection.

---

### Post by Horndog on 2008-05-10
Thanks for taking the time to respond.

> **Horndog said:**
> 
BTW I don't have any internet without this connection.
[color=red]I have to boot into windows to acess the internet and drag
any files back to ubuntu with a flash drive.[/color]


As is stated: I don't have Internet in Ubuntu.

[Quote=Darrena]
Did you copy the file to /lib/firmware?
[/quote]
Yes, as per instructions:
```

sudo mv SW_8xx_SER.dat /lib/firmware/SW_7xx_SER.cis

```

In addition I flashed the firmware on the card itself in windows with the latest firmware from Sierra.

[Quote=horndog]
```

horndog@horndog-laptop:~$ ls /dev/um*
/dev/umts

```[/quote]
As indicated there is a driver made so the install procedure must
be correct. There is a flashing green light on the AirCard which also means the card is registered with the system.

My problem is the script, or at lest that is my understanding.

I'm sorry if you don't agree with my "rant" but when there are 25000 people at one time accessing this forum how can there be much of any support? I have been using ubuntu for years but this is a big problem. Most posts go unanswered.

---

### Post by Horndog on 2008-05-10
Here is a link to another forum:  [http://www.linuxforums.org/forum/wireless-internet/83771-sierra-aircard-860-a.html]("http://www.linuxforums.org/forum/wireless-internet/83771-sierra-aircard-860-a.html")

Apparently The current install doesn't work with kernel 2.6
so unless some one an confirm a success in 8.04 then I guess I'll
dump this install.

---

### Post by Darrena on 2008-05-10
> **Horndog said:**
> Here is a link to another forum:  [http://www.linuxforums.org/forum/wireless-internet/83771-sierra-aircard-860-a.html]("http://www.linuxforums.org/forum/wireless-internet/83771-sierra-aircard-860-a.html")

Apparently The current install doesn't work with kernel 2.6
so unless some one an confirm a success in 8.04 then I guess I'll
dump this install.


It works for me, I use it every day on Hardy.   First thing to check is the device being assigned a serial port.   From a terminal type dmesg | grep tty and post the output here.   

If you will look at my instructions once the device is installed as has a serial port you don't need to do any of the other fancy items if you install GPRSEC.   So first lets make sure you aren't being bitten by the bug with Thinkpads that keeps the card from getting a serial port.

---

### Post by Darrena on 2008-05-10
> **Horndog said:**
> 
I'm sorry if you don't agree with my "rant" but when there are 25000 people at one time accessing this forum how can there be much of any support? I have been using ubuntu for years but this is a big problem. Most posts go unanswered.

I am honestly not sure I agree, but I don't lurk here as much as I used to (A 2 year old around the house has a way of taking over all your time!).   When I look at the recent posts most seem to be getting answers.

Either way back to the problem at hand, if you have the firmware copied over you don't need anything else.   Check to make sure a serial port is being assigned as I describe in the previous post, if it is then we can stop NM, install GPRSEC and then you will be good to go.   

> 
Quote:
Originally Posted by Horndog View Post
BTW I don't have any internet without this connection.
I have to boot into windows to acess the internet and drag
any files back to ubuntu with a flash drive.

You should be able to mount your Windows partition from Ubuntu to copy over the files you need.   GPRSEC has dependencies of:
libgnome2-perl
libgtk2-trayicon-perl
gtk2-engines-pixbuf

You may want to grab them from packages.ubuntu.com when you are in windows as well as GPRSEC.

---

### Post by Horndog on 2008-05-10
> **Darrena said:**
> [color=red]It works for me, I use it every day on Hardy.[/color] First thing to check is the device being assigned a serial port.** From a terminal type dmesg | grep tty and post the output here. That is good news```
$ dmesg | grep tty
[** 14.964054] console [tty0] enabled
[** 16.972448] 00:0a: ttyS0at I/O 0x3f8 (irq = 4) is a NS16550A
[** 39.035645] 0.0: ttyS1 at I/O 0x47f8 (irq = 3) is a 16550A
[** 54.418143] audit(1210459191.810:2): type=1503operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4980 profile="/usr/sbin/cupsd" namespace="default"

```
```
$ sudo wvdial creat
WvDial: Internet dialer version 1.60
--> Warning: section [Dialer creat] does not exist in wvdial.conf
--> Cannot open /dev/modem: No such file or director
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

```

 As you can see there is no /dev/modem 

I'm finding out that this is a symptom of kernel 4.6. Bottom line is I don't have a Dialer script.> **Darrena said:**
> If you will look at my instructions once the device is installed as has a serial port you don't need to do any of the other fancy items if you install GPRSEC.** So first lets make sure you aren't being bitten by the bug with Thinkpads that keeps the card from getting a serial port.


There is no response from my Sierra card because there is no Dialer script because there is no /dev/modem.
Right now I'm looking into fixing that.

Also I've been trying to get my Analog modem to work.
```

horndog@horndog-laptop:~$ dmesg | grep 00:1f.6
[   19.471416] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   19.471427] ACPI: PCI interrupt for device[color=red] 0000:00:1f.6 disabled[/color]


```

[color=red]0000:00:1f.6[/color] being my modem.

I would like to know more about this thinkpad bug.
Thanks for you help.

edit:

I have GPRSEC up and running: It doesn't communicate with the AirCard. It asks that you  turn an the device.

---

### Post by Darrena on 2008-05-11
Did you tell GPRSEC to use TTYS1 to connect?

---

### Post by Horndog on 2008-05-11
> **Darrena said:**
> Did you tell GPRSEC to use TTYS1 to connect?

The best I've gotten so far is for GPRSEC to ask me to turn on the device. There is a script program called "catty"  That I found reference to an a German wiki site. [http://wiki.chaostreff.ch/Sierra_Wireless_AC850]("http://wiki.chaostreff.ch/Sierra_Wireless_AC850").
If you translate through google it's not too bad. I'll report back when I figure things out. BTW there is a big difference between Kernel 2.6.13 and Kernel 2.6.24-16 in the way it handles the pcmcia.

---

### Post by Darrena on 2008-05-11
> **Horndog said:**
> The best I've gotten so far is for GPRSEC to ask me to turn on the device. There is a script program called "catty"  That I found reference to an a German wiki site. [http://wiki.chaostreff.ch/Sierra_Wireless_AC850]("http://wiki.chaostreff.ch/Sierra_Wireless_AC850").
If you translate through google it's not too bad. I'll report back when I figure things out. BTW there is a big difference between Kernel 2.6.13 and Kernel 2.6.24-16 in the way it handles the pcmcia.

Did you check the preferences on GPRSEC and make sure it was set to the right port?

---

### Post by Horndog on 2008-05-11
> **Darrena said:**
> Did you check the preferences on GPRSEC and make sure it was set to the right port?
Yes. If I use a wrong port GPRSEC lets me know. 
There is just no response from the device because there is no file created by wvdialconfig. When I do a wvdialconfig create I get an error (there is no /dev/modem/). This "catty" program is to replace wvdialconfig in later Kernels.

I'm still looking for pcmciautils at least that is what they say to use. I'm looking for a "deb" version. I don't have all the essentials to compile the source code.

---

### Post by Darrena on 2008-05-11
> **Horndog said:**
> Yes. If I use a wrong port GPRSEC lets me know. 
There is just no response from the device because there is no file created by wvdialconfig. When I do a wvdialconfig create I get an error (there is no /dev/modem/). This "catty" program is to replace wvdialconfig in later Kernels.

I'm still looking for pcmciautils at least that is what they say to use. I'm looking for a "deb" version. I don't have all the essentials to compile the source code.

I don't think GPRSEC uses any part of the wvdial configuration.   It calls PPP directly with the proper settings.   

You also don't need pcmciautils.   Ok lets make sure that the card is actually being detected.   Eject the card, then open a terminal and type:

```
tail -f /var/log/messages
```

Then insert the card and watch the messages that show up in the log.   If you could post them here.

Thanks!

---

### Post by Horndog on 2008-05-11
> **Darrena said:**
> I don't think GPRSEC uses any part of the wvdial configuration.   It calls PPP directly with the proper settings.   

You also don't need pcmciautils.   Ok lets make sure that the card is actually being detected.   Eject the card, then open a terminal and type:

```
tail -f /var/log/messages
```

Then insert the card and watch the messages that show up in the log.   If you could post them here.

Thanks!


Have a look


syslog
```

May 11 18:22:42 horndog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 11 18:22:50 horndog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 11 18:23:02 horndog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 11 18:23:13 horndog-laptop dhclient: No DHCPOFFERS received.
May 11 18:23:13 horndog-laptop dhclient: No working leases in persistent database - sleeping.
May 11 18:23:41 horndog-laptop kernel: [  424.437882] pccard: card ejected from slot 0
May 11 18:23:46 horndog-laptop kernel: [  425.297186] pccard: PCMCIA card inserted into slot 0
May 11 18:23:46 horndog-laptop kernel: [  425.297386] pcmcia: registering new device pcmcia0.0
May 11 18:23:46 horndog-laptop kernel: [  159.505499] 0.0: ttyS1 at I/O 0x47f8 (irq = 3) is a 16550A
May 11 18:26:44 horndog-laptop kernel: [  493.646117] pccard: card ejected from slot 0
May 11 18:26:51 horndog-laptop kernel: [  494.661430] pccard: PCMCIA card inserted into slot 0
May 11 18:26:51 horndog-laptop kernel: [  494.661630] pcmcia: registering new device pcmcia0.0
May 11 18:26:51 horndog-laptop kernel: [  494.709368] 0.0: ttyS1 at I/O 0x47f8 (irq = 3) is a 16550A

```
messages
```

May 11 18:12:46 horndog-laptop kernel: [  139.056307] NET: Registered protocol family 10
May 11 18:12:46 horndog-laptop kernel: [  139.058090] lo: Disabled Privacy Extensions
May 11 18:12:46 horndog-laptop kernel: [  139.060643] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 11 18:14:04 horndog-laptop kernel: [  215.386360] PPP generic driver version 2.4.2
May 11 18:14:04 horndog-laptop pppd[5895]: pppd 2.4.4 started by horndog, uid 1000
May 11 18:14:06 horndog-laptop pppd[5895]: Exit.
May 11 18:18:13 horndog-laptop kernel: [  313.494764] pccard: card ejected from slot 0
May 11 18:18:47 horndog-laptop kernel: [  320.349614] pccard: PCMCIA card inserted into slot 0
May 11 18:18:47 horndog-laptop kernel: [  320.349814] pcmcia: registering new device pcmcia0.0
May 11 18:18:47 horndog-laptop kernel: [  120.150324] 0.0: ttyS1 at I/O 0x47f8 (irq = 3) is a 16550A
May 11 18:23:41 horndog-laptop kernel: [  424.437882] pccard: card ejected from slot 0
May 11 18:23:46 horndog-laptop kernel: [  425.297186] pccard: PCMCIA card inserted into slot 0
May 11 18:23:46 horndog-laptop kernel: [  425.297386] pcmcia: registering new device pcmcia0.0
May 11 18:23:46 horndog-laptop kernel: [  159.505499] 0.0: ttyS1 at I/O 0x47f8 (irq = 3) is a 16550A

```

Let me know what you think.
thanks
.

---

### Post by Darrena on 2008-05-12
Well I am at a loss as to why it doesn't work for you...   It has a serial port assigned so you should be able to make a PPP connection using it.   If you tail /var/log/messages is there anything interesting showing up when you try and run GPRSEC?

---

### Post by Horndog on 2008-05-12
> **Darrena said:**
> Well I am at a loss as to why it doesn't work for you...   It has a serial port assigned so you should be able to make a PPP connection using it.   If you tail /var/log/messages is there anything interesting showing up when you try and run GPRSEC?

I will post what you ask for but, when I Try to connect I monitor the syslogs and the only thing of interest is: "script failed"

I'm attempting to use anything installed to connect such as gnome ppp. Same "script failed". There is a consensus the Kppp is the recommended dialer but for me to install it now would be next to impossible because of all the dependencies.

I'll get back with your request.

Thanks.

---

### Post by soundray on 2008-05-15
Make sure that the user who runs pon is a member of the dialout group (should be default, but worth checking).

---

### Post by Horndog on 2008-05-15
> **soundray said:**
> Make sure that the user who runs pon is a member of the dialout group (should be default, but worth checking).

I will. Now I'm taking a brake for a couple of days. I'm wondering if by removing "network Manager" I didn't do something to effect the dialing Script. I get a "Failed Script" in the logs.

Thanks for your reply.

---

### Post by Horndog on 2008-06-15
Conclusion: If anyone thinks that they can install 8.04 from a disk and then successfully setup a cellular air card as a primary Internet source will be disappointed. 

My work around is to buy a 3G router and setup a network.
This a new technology, just insert the pcmcia card into the router go to setup to put in your card specs and connect.

There are three brand routers too choose from: ZyXEL, D-Link, and
AirLink 101. Make sure you choose the right band. At&t (Cingular)
you need "UMTS/HSDPA", Sprint and Verizon you need "EV-DO".

The best thing about this setup is you can share your Cellular connection. 

I bought a D-link DIR-451 "UMTS/HSDPA" and it works sweet. I can use my computer and also connect with my PDA.

I will, some how, get my Sierra Air card to work as a matter of pride but I think I prefer the router anyway.

Thanks for your help, Darrena and soundray.

---

### Post by jedijf on 2008-07-13
i am using and having similar difficulty with a thinkpad 600.

everything seems ok, but gprsec times out.

any help would be appreciated.

---

### Post by achim_59 on 2008-07-14
To anyone still following this thread....

I first found this thread through google. I have an AC850 that I'd really like to get working with my HP nx6325. I'm using Feisty Fawn 7.04.

I have trawled a number of forums and various other sites. I cobbled things together and got as far as the "ATZ" init before my attempts hit a wall.

I cannot post new threads at the moment (probably been away too long - 2 years) so I have to try it via a reply.

Here's what I've got so far:

/etc/udev/rules.d/99-aircard.rules
<code/>
# Original suggested script
# BUS=="pcmcia", SYSFS{card_id}=="0x0710", NAME="umts", SYMLINK="tts/umts", RUN+="/usr/local/bin/umtsinit" 
# If correct, should add the pin for umts card init
BUS=="pcmcia", SYSFS{card_id}=="0x0710", NAME="umts", SYMLINK="tts/umts", RUN+="/usr/local/bin/eplusinit" 

<code>

pccardctl....
<code>
Socket 0:
  product info: "Sierra Wireless", "AC850", "3G Network Adapter", "R1"
  manfid: 0x0192, 0x0710
  function: 2 (serial)

</code>

/usr/local/bin/eplusinit....
<code>
#!/bin/sh
# 20060517
# Daniel Aubry
# SyGroup GmbH
# Version 0.1
# Initscript fuer Sierra Wireless Karte mit pcmciautils
# benoetigt catty [http://catty.sourceforge.net/](http://catty.sourceforge.net/) oder [http://debian.syhosting.ch/software/catty_2006.03.13-3_i386.deb](http://debian.syhosting.ch/software/catty_2006.03.13-3_i386.deb)


sleep 5 && (
. /etc/profile

PIN="4269"

antwort=`catty -r0 -d /dev/umts -b 460800 -w "\nAT+CPIN=\"$PIN\"\n" | tail -n1`
signal=`catty -r 0 -d /dev/umts -b 460800 -w "\nAT+CSQ\n" | grep CSQ: | cut -d" " -f2`
echo "Rueckmeldung vom Modem: $antwort"
echo "Signalqualitaet: $signal" ) 

[edit]

</code>

/etc/chatscripts....
<code>
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
</code>

Have I forgotten something?
When I try pon I get....

<code>

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

</code>

I'm wondering if the fact that I get "function: 2 (serial)" with pccardctl has anything to do with it. The ubutu help that I got onto suggested that I should get something like: function: 6 (network)" instead.

I'll post a new thread when I can (and id I need to).

Many thanks for any help that anyone can give.

---

### Post by achim_59 on 2008-07-14
Sorry, that last message really didn't come out like I wanted. Still, the information is there and if somebody could tell me how to get my code to LOOk like code, I'd be grateful. As far as I can remember it only required HTML tags <code>...</code> to make it work. Ahhh.... it should have been [code]...[code] eh?

Should I try again or can somebody read it anyway and offer some help?

Achim_59


P.S. I'm going to bed now... I need to get some sleep. I'll check this thread tomorrow.

---

### Post by achim_59 on 2008-07-16
OK, I think I can get the stuff correctly formated, so I'll try again. I still cannot post new threads, otherwise I would. Perhaps somebody could give me a clue as to the reason.

As for my problem with the AC850 under Feisty Fawn 7.04.... Here's what I've got so far:

/etc/udev/rules.d/99-aircard.rules

```
# Original suggested script
# BUS=="pcmcia", SYSFS{card_id}=="0x0710", NAME="umts", SYMLINK="tts/umts", RUN+="/usr/local/bin/umtsinit"
# If correct, should add the pin for umts card init
BUS=="pcmcia", SYSFS{card_id}=="0x0710", NAME="umts", SYMLINK="tts/umts", RUN+="/usr/local/bin/eplusinit"

```


pccardctl....

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

achim_59 [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

