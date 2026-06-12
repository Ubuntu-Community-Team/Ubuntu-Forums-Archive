---
title: "Airport (not Extreme) card, closed WPA2 Airport networks, Ubuntu 8.04.1"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by renichms on 2008-09-20
I just installed Ubuntu 8.04.1 on a G4 iMac with a regular Airport card in it.  My house has 2 closed wireless networks.  One uses WPA2 Personal and the other is just hiding and hoping no one sees it.

I am experiencing this problem both on Ubuntu on the iMac and in Yellow Dog on the PS3.  With Ubuntu, it seems to connect to the WPA2 network but when I try to connect to a website, nothing.  If I try the other network, instant response - it all loads flawlessly.  The same basic thing happens with YDL on the PS3.

So I guess the question is this:  how do I get Linux (any) to connect to a more secure wireless network?  No Mac or Windows computers or even handheld devices have a problem connecting.  Even the Wii and PS3 (when in the game OS) have no issues.  So why is it that Linux won't connect?

I tried reading through threads here and the stickies and didn't find this exact issue so thought it would be safe to throw it out for responses.  If any more details are needed, I can provide them if it means I can more securely connect these two new operating systems (new to this house, at least).

Thanks for any help you can provide.  Hopefully we can get everything connected securely soon.

RN

---

### Post by renichms on 2008-09-21
And still no connection today.  Tried tweaking routers, tried tweaking settings in Ubuntu.  Nothing.  I really need some help getting Ubuntu (technically Ubuntu and YDL since neither one is compatible with WPA/WPA2) to connect to the network.  It's useless to me without a network connection.

RN

EDIT:  Ran a cable from one end of the house to the other in order to get these 118 updates in the hopes that one will help fix the bug that keeps Ubuntu from being able to use wireless networks.

---

### Post by renichms on 2008-09-21
And now I get this on startup:
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Don't know why.

RN

EDIT:  In one of the "Domain" slots, all I did was add the name of the wireless network and it suddenly is zipping along as fast as it should.  I'll keep an eye on it and if it works I guess I have a tip to offer up to people with a regular Airport card that want to dual boot Mac OS and Ubuntu and have the Airport card work for both.

---

### Post by renichms on 2008-09-22
Been trying to connect iMac with regular Airport card to closed Airport network using WPA/WPA2.  NetworkManager is of no use at all.

Wicd is installed and it looks great.  However, it has absolutely nowhere to select WEP, WPA or WPA2 and no way to enter a password either.  I'm about ready to throw in the towel.  I am not a programmer and I loath having to manually create text configuration files to make things like this work when they should work as advertised to start with.

I'll give it a few more days to try and figure out why Ubuntu doesn't support WPA/WPA2 or connect worth a crap, then I'll install Fedora over it and give that a shot.  If that fails, I guess I could just convert the HDD back into one Mac partition.

If anyone out there is using a regular Airport card with an Airport wireless network with WPA/WPA2 and SSID off, PLEASE tell me how you got Ubuntu to connect.

RN

---

### Post by renichms on 2008-09-24
Thanks for the help.  Fedora 9 did the trick.  Everything works now.

RN

---

