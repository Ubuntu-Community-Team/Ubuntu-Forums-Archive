---
title: "GDBus.Error Modem in Disabled State. Need help with setting up a USB modem."
date: 2023-07-19
forum: Networking &amp; Wireless
---

### Post by nobody96 on 2023-07-19
Hello.

Relative newbie here. So brace yourselves, doublefold. I  purchased three ZTE MF667 3g+ modems, to use, hopefully to connect to  three at once ( no load balancing, just to connect and bridge to VMs ). 
 I  can't  get it to work. Modem works on windows 10, using the  configuration/dialup software included with the driver. But software  locks me to one modem at once, so I hoped Linux would be superior in  that regard.
On Linux, when the modem with a sim card is connected,  the LED changes from red, to green, to blue ( as it should, indicating  modeswitch? ), and it appears that the modem is somewhat recognized and  pseudo working. **Note:The it still works in storage capacity, and  I can access the auto mounted ISO?CD? driver setup.  Unmounting/disconnecting the drive disconnect's it, but doesn't seem to  do anything to make the modem behave any differently**
 It  appears in mobile networks. But when I enable network connection, and  set up APN, the status connection icon in upper right corner glitches  and flashes from 3 dots ( connecting ), to bars ( connected ). Really  high frequency of flashing.
I figured out, that I can enable PIN sim card locking from mobile networks menu, and it works.
When I press network-type of network, and attempt to change it from "auto" to "manual", error pops up.

"```
GDBus.Error:org.freedesktop.ModemManager1.Error.Core.WrongState: modem in disabled state
```"

( online searches for that exact error give 0 results :lolflag: )

Qualcomm chipset is recognized in modem information. Power strenght appears as 0%.

Modem  appears at /dev/cdc-wdm2 , and in Ubuntu modem connection step by step  modem thingy ( as cdc-wdm2 ) in network configuration. When it's set up,  nothing happens connection wise, but when the priority on the  connection is set to "0", system glitches out, and I can move the mouse,  but can't click anything.
Usually it goes away if I unplug the modem from USB. Sometimes I have to reset the PC.

Modem  appears as wwan0 also. In some places at least. It's not in any fold  down menus for creating an ethernet connection. One guy on his forum  said, that this modem works like that. It first appears as an ethernet  connection, you connect to it,access modem settings via IPV4 in browser,  and configure it there (  [https://www.lourdas.eu/blog/zte-mf667-3g-usb-modem-and-linux](https://www.lourdas.eu/blog/zte-mf667-3g-usb-modem-and-linux) )

```
"Ip a"
``` spews out:

```
wwan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 9e:73:xx:xx:xx:00  brd ff:ff:ff:ff:ff:ff
```

( normal MAC, I just censored it )

When I "```
Ifconfig wwan0 up
```" it, it appears like so in "```
ip a
```"

```
wwan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether 9e:73:xx:xx:xx:00brd ff:ff:ff:ff:ff:ff
    inet6 fe80::9c73:xxxx:xxxx:xxxx/64 scope link 
       valid_lft forever preferred_lft forever
```

IPV6 can be pinged, without problems.
I  can occasionally assign an IPV4 to it, ( I can assign 192.168.0.100 to  it via terminal for example, and sometimes it shows as 192.168.0.40  wwan0 in "netstat -r", but can be pinged only at 192.168.0.100" ).  Although I don't know why it sometimes works, and sometimes doesn't.

Can't access it via IPV4 via browser. I get an instant "CONNECTION_REFUSED".

"```
mmcli -m any -e
```" spews out:

```
error:  couldn't enable the modem:  'GDBus.Error:org.freedesktop.libqmi.Error.Protocol.MissingArgument:  Couldn't register for power indications: QMI protocol error (17):  'MissingArgument'
```

```
lsusb
``` shows it as ```
Bus 005 Device 003: ID 19d2:0017 ZTE WCDMA Technologies MSM MF669
```

So, at this point, I'm dazed, bamboozled, and confused. Especially as a newbie.
Help would be appreciated.
I will answer questions as best as I can.

Thanks.

---

