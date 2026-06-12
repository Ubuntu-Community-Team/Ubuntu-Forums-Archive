---
title: "Can see the network but cannot connect"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by jdnyinger on 2007-12-07
Hello.

I apologise in advance if this has already been answered.  I recently upgraded to Ubuntu 7.10 on my desktop PC.  Everything works perfectly except the wifi connection.  I can see the connections via the network manager and everything comes up when i do the iwconfig scanning.  However, whenever I try to connect to the network it asks for the WPA key, which I give and is correct, and then it just times out, over and over again.  My neihbors connection brodcasts right into my house and is unprotected and I can't connect to it either.  Any advice would be greatly appreciated.  Thank you so very much.  Take care.

---

### Post by A + on 2007-12-07
Mind if I jump into your thread? Looks like I've got a similar/the same problem so I'll be watching this thread anyway unless you tell me your problem is very different from this below.

Wireless not connecting.  My laptop connects fine plugged with cable into the router but no wifi.  Last week I couldn't even see a 'Wireless Connection' option in Network Manager until I did the ndiswrapper business on my Atheros AR5007EG wifi card.  Now I can not only see the option but the signal strength is very good.  

I assume I've got the correct WEP key as it works in Vista and now that I know it off by heart  I think typos are out of the equation.  I've selected DHCP as opposed to static is that ok?  Can't get it out of my head that it could be some stupid setting I haven't found.  I've tried kevdogs CLI config tutorial but to no avail. "No dhcoffers" the result.  Could it be a device conflict between the Realtek card and the Atheros? or something?

Stumped so far.

---

### Post by jdnyinger on 2007-12-10
Well comrade, that sounds the same as mine.  I have searched everything I can.  And I have an identical situation with a D-Link.  I suppose we wait...

---

### Post by carnaka04 on 2007-12-10
I'll jump on this wagon, too.  Same exact problem (even down to the "My neighbors connection broadcasts right into my house and is unprotected and I can't connect to it either").  Wireless is goofy for me in other places, too.  For example, I can get a VPN connection at school, but webpages load halfway ([www.google.com](www.google.com) loads one link and no images, then freezes at 23% loaded).  Any solutions yet?

---

### Post by kendalw3 on 2007-12-10
Well...... while we are adding people to this thread... i'm having the same troubble as well.  I have the atheros ar5006eg and it is working just fine.... detects networks and all that but won't connect to them.... i am also using wicd if that makes any difference.... hopefully we find some help this is one of the last things i need to work before i can be free of the dark side if you know what i mean (vista sucks!)

KJ

---

### Post by mdurham on 2007-12-10
I had a similar problem.
I finally got my WG111 v3 to work by:
disconnect my wired connection
plug in the WG111 v3
using the manual network config
disable roaming
insert the ESSID
Password type: WEP key (hexadecimal)
paste the hex code obtained from the router (I obtained this with a wired connection)
Configuration: Automatic (DHCP)
Click the enable tick box on and off and on again
wait for a connection, use Firefox or whatever as there is no other indication that it's working.

I 'think' my problem was having the wired connection at the same time I was trying to connect via wireless. Anyway it seems to work at the moment.

Cheers, Mike

---

### Post by thk on 2007-12-11
This issue has only popped up for me in the last week or so. Things were working fine before that. (I can connect sporadically using roaming mode; however manual config works everytime.)  My version of the network-manager packages is 0.6.5-0ubuntu1 (try "dpkg -l network-manager"). I have "proposed updates" installed which may be the culprit. It will help if folks list which version of the network-manager package  they have installed.

---

### Post by nosh276 on 2007-12-11
I'm having a similar problem and have been watching the forums for days and trying everything offered. I have a Linksys WPC54g v2.0 wireless card. I can see the network and it attempts to connect, but it never can. I've tried ndiswrapper, reinstalling the drivers, everything everyone seems to suggest.

---

### Post by kevdog on 2007-12-11
If you could previous connect but now you cant -- it probably was an update that broke a package.  If you could never connect, #1 - ensure you can connect to an unencrypted network first, then if WPA still does not work, try connecting from the command line -- see the guide in my signature.

---

### Post by Bpa on 2007-12-16
I am having the exact same problem. I just recently installed Ubuntu 7.10 and I just got my wireless to work using [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/) which just changes the native linux kernel drivers instead of having to use ndiswrapper.  My wireless adapter is a Linksys WUSB54GS v2.1.  After installing the above drivers, I can now see the wireless network essid's, but I cannot connect to my wireless network with WPA. I am sure I have entered the pass phrase correctly and I have selected the TKIP option, but it just times out without connecting.

---

### Post by sanctified-x on 2007-12-16
Hey guys, mind if I join? My Atheros AR5007EG wifi card is just killing me here...

---

### Post by AJWhitewolf on 2007-12-16
I have a D-Link PCI card that uses the Atheros drivers, and I am having a similar problem.  I can connect to encrypted networks without a problem, but not any unencrypted networks.  I didn't have the card before I upgraded to 7.10, so I don't know if it would have worked in 7.04.  I ditched the network manager and started using the terminal instead, and I don't get any DHCPOFFERs either.  I went through all of [this thread]("http://ubuntuforums.org/showthread.php?t=571188&highlight=unencrypted") and tried all of the possible resolutions, but nothing has worked.  Any help or suggestions would be appreciated!

---

### Post by kevdog on 2007-12-16
AJ

Can you post some output like:

iwlist scan

Tell me the network you are trying to connect to

Along with

lshw -C network

---

### Post by Prometheum on 2008-01-03
I'm using an Atheros AR5007EG, with Ndiswrapper and the 64-bit windows driver from here:
[http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

I can see every one of my WAP's. One of them is using WPA, one is using WEP, and one us unencrypted. I cannot connect to any of them, though NetworkMonitor says that I'm sending and receiving packets from all the WAP's I test.

At first I thought it was because of some things I might have done to the mini-PCI slot, but seeing this thread is making me reconsider.

lspci -vvv entry: (I think the listing is wrong, this is an example of the "bug" that causes 5007's to be listed in lspci as 5006)

```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: IBM Unknown device 058a
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at f6000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [60] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 <64us
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <512ns, L1 <64us
                Link: ASPM L0s Enabled RCB 128 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                Vector table: BAR=0 offset=00000000
                PBA: BAR=0 offset=00000000

```

---

### Post by jellytree on 2008-01-04
Let's add another frustrated user to the list. I have a broadcom 43xx installed (both ndiswrapper and native fwcutter methods tried) and it always comes down to the same thing - it sees the card, enables the card but can never connect.

I did once manage to trick it somehow by setting the router ESSID broadcast to hidden, attempting to connect with WPA (but it didn't work), reset to a non-hidden broadcast and then tried to reconnect and it worked. I did have intermittent connection lapses though with this fix.

Another time I got it working by changing the router to an unsercured WEP network, then back to a WPA secured network and re-entered the key. I was then able to establish a connection to the router.

Both times I have used WICD as my network manager as network-manager itself has never worked with my broadcom card.  Back in Feisty 7.04 I was using wifi-radar successfully for WEP connections, but I never tried to get WPA working with that manager, and I have not tried wifi-radar in Gutsy yet.

I hope this helps someone else, or provides some clues as to the underlying problem.  Both times, it involved re-entering router configuration, though....

---

### Post by Prometheum on 2008-01-05
Alright, I believe I have solved this for my setup at least.
EDIT: no I didn't :(

---

### Post by Prometheum on 2008-02-10
Bump!

Has anyone gotten this working yet? I can't find anything else about this, and I have heard or found no explanation for this behaviour, except that apparently its limited to AMD64 machines. 

I've just started using a broadcom card. However, that occasionally makes my kernel panic. I can't seem to win.

Has anyone else had some luck?

---

### Post by ackey on 2008-04-28
I don't know if I have the same problem or not, but perhaps someone here has fought enough already to help me...

I can connect to *most* networks *most* of the time.  Sometimes, on the university residential wifi network I see the access point, have a great signal, but can't get an IP address. (no dhcpoffers)  Strangely, I can connect from this location *some* of the time and rarely have problems on any other network.  My boyfriend has an identical laptop and doesn't have problems connecting when I do.  The network is visible and not password protected.

I've tried using the command line, restarting the computer, restarting the wireless - any ideas of how to debug this?

---

### Post by ironjon on 2008-04-29
I´m in this situation.
My card is ar5007eg and don´t connect.
OS ubuntu 7.10

---

