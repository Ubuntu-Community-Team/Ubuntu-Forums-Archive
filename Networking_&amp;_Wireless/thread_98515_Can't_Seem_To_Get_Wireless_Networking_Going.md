---
title: "Can't Seem To Get Wireless Networking Going"
date: 2005-12-03
forum: Networking &amp; Wireless
---

### Post by Orporg on 2005-12-03
Dear Sirs and Madams,

I can't seem to get my wireless card to work under Ubuntu.  As far as I can tell, Linux detected it and configured it properly.  It identifies the card correctly 
(D-Link DWL-520+) and even the chipset but I can't seem to see my access point via the card.  I have two other machines (a Windows XP desktop and a Mac OS X laptop) that connect to the access point just fine.  

I went on to the IRC channel and while the folks there were wonderful, we couldn't seem to get it working.  The access point serves up IPs via DHCP so I tried it that way and I tried it with a static IP and nothing worked.  According to some of the utilities the IRC folks had me run I was getting no signal from the access point at all (which is about 5 feet away).

I have WEP turned off (though I'd like to turn it on again before too long) and I know the access point works because other machines use it regularly.

The IRC folks told me about something called "ndiswrapper" but I'm somewhat reluctant to use that.  For one, the Ubuntu wiki said that my card should work right out of the box.  Second, I didn't see my card listed under the supported cards on the ndiswrapper documentation I saw.

Any suggestions would be appreciated.

(Note:  I am probably one of those Windows "power users" that are supposed to be especially aggrivating (I happen to agree, actually) so please bear with me.  I'm kind of stuck halfway between tech land and complete know nothingness.  I know just enough to be dangerous, I suppose).

Thanks in advance.

---

### Post by Lambert on 2005-12-03
I show this using a ti acx chipset so lets get some command outputs. post the following here.

sudo lshw -C network
lspci -v
iwconfig
ifconfig
iwlist <wlan0> scan

where <wlan0> = the device logical name with out the <>

Your router doesn't have mac filter or limited connections that won't let it connect does it?

---

### Post by Orporg on 2005-12-04
Now the damn card won't even show up in the networking panel.  I stuck in a wired card temporarily, in order to download some stuff.  I didn't see the wireless card in the networking panel then, but I figured the wired card was somehow taking precedence.  I have now removed the wired card and Ubuntu has "forgotten" the wireless card.

The access point does not have mac address filtering or limited connections.  I wish it did.

---

### Post by Orporg on 2005-12-04
I'm going to bump this once.  Is there any way to get Linux to re-recognize my wireless card?  Then I can go on to giving the output of those commands.

---

### Post by pau on 2005-12-04
look here

[http://ubuntuforums.org/showthread.php?t=96998&highlight=pau]("http://ubuntuforums.org/showthread.php?t=96998&highlight=pau")

good luck

---

### Post by Lambert on 2005-12-04
Don't worry about it being recognized in the networking window. Just go to a terminal and run the commands.

It's not showing in network-admin because of a driver level problem, not because the device isn't recognized.

---

### Post by Orporg on 2005-12-09
Sorry it too so long but here are the results of the commands:

For sudo lshw -C network:

On just one line, it went quickly through some stuff that looked like: PCI, IDE, Frambuffer and lots more.  And then there was no output on the screen, it just gave me the shell prompt again.

For lspci -v:

I got a huge screenfull of information.  None of it pertained to network devices.  I got entries for the motherboard chipset like the host bridge, ISA bridge, pci bridge, USB controller, VGA compatible controller, IDE interface.

For iwconfig:  

lo no wireless extensions

sit0 no wireless extensions

For ifconfig:

lo Link encap: Local Loopback
inet addr: 127.0.0.1  Mask:  255.0.0.0
inet6 addr: ::1/128  Scope: Host
UP LOOPBACK RUNNING  MTU:16436  Metric: 1
RX packets: 7820  errors: 0  dropped: 0  overruns: 0 frame: 0
TX packets:  7820  errors: 0  dropped: 0  overruns: 0 frame: 0
collisions: 0  txqueuelen: 0
RX bytes: 466183  (455.2 KiB)  TX bytes:  466183 (455.2 KiB)

For iwlist <wlan0> scan:

wlan0    Interface doesn't support scanning


That's all.  I don't have WEP or MAC filtering on.  The network is open.  Also, someone had me run the iwlist command before and while it didn't find anything, it did do the scan.  I think Ubuntu isn't seeing the card at all now.

---

### Post by Lambert on 2005-12-09
run this command

top | grep hald

This is to see if the hal daemon is running

You're correct, there is a device layer problem currently and you said it used to work so something is wrong. I'm not knowledgeable in this area but believe hal daemon is what identifies devices and then does something through dbus.

Once you see it's running you can just hit q to quit and get back to prompt.

---

### Post by Orporg on 2005-12-09
When I type that command I get nothing.  The cursor moves down one line to a blank line and nothing happens.  When I hit "q" I just get a new shell prompt.

---

