---
title: "Wireless card not recognized after upgrade to Feisty"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by Duffy on 2007-03-28
After upgrading the Feisty beta, the wireless card is not only no longer working, it is not even recognized by the system. Worked out of the box with Edgy 6.04 and 6.10. Tried ndiswrapper, but that did not help. I guess if the system does not even see the card, ndiswrapper is not going to help. The card is a Trendnet TEW-228PI. This is a real bummer. Any suggestions?

duffy@linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

duffy@linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:B2:18:39
          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:feb2:1839/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2579681 (2.4 MiB)  TX bytes:4422399 (4.2 MiB)
          Interrupt:20

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3642 (3.5 KiB)  TX bytes:3642 (3.5 KiB)

---

### Post by Floppyjoe on 2007-03-28
I pulled this off the ndiswrapper-list site at sourceforge.net
> Card: Trendnet TEW-228PI

    * Chipset: Realtek RTL8180L
    * pciid: (as reported by lspci -n ) 00:0e.0 Class 0200: 10ec:8180 (rev 20) Windows#*Driver: [284] used win2k driver contained in ndis5x-8180(173).zip
    * Other: Works with WEP with a netgear WGR 614 v4 router ok, have not tried other encryptions version of ndiswrapper 0.11, mdk10.1 kernel 2.6.8.1-10mdk, using windows drivers (which worked ok in doze) that came with cd caused freezes 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#T](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#T)

---

### Post by Duffy on 2007-03-29
I used that exact driver downloaded from the Trendnet website and installed it with the ndsiwrapper graphical interface, and it basically gives me an error message that the card is not there. I think the issue is not the ndiswrapper is not working, it seems like Feisty cannot even detect that the card exists.

---

### Post by chili555 on 2007-03-29
Feisty installs NetworkManager by default. NM gives preference to wired connections, which you have hooked up . If you disconnect the wire and give it a precautionary *sudo ifdown eth0* are you then able to see and configure your wireless?

---

### Post by Duffy on 2007-03-29
> **chili555 said:**
> Feisty installs NetworkManager by default. NM gives preference to wired connections, which you have hooked up . If you disconnect the wire and give it a precautionary *sudo ifdown eth0* are you then able to see and configure your wireless?

No, when the system was first upgraded, the cat5 was not even connected because that system used wireless only prior to the upgrade.  It's not that it cannot see the network, I wish that was my issue, the issue is that Feisty is not even detecting/acknowledging that the Trendnet card is even in the system. It does not know it's there. Taking the fixed Ethernet port out of the picture does not change anything - the result is no available Ethernet connection.

---

### Post by Duffy on 2007-03-29
I had to mess around quite a bit with ndiswrapper to finally get the driver installed and actually working! Yeah, that's the good news. The bad news is that knetworkmanager will not connect to the access point. I have messed with it for hours and it hangs at 57%. I eventually closed it and configured the network for the system settings menu. Problem is so far, I can't get it to save the settings. I have to reconfigure with each restart of the system.

---

### Post by zonetripper on 2007-03-31
> **Duffy said:**
> I had to mess around quite a bit with ndiswrapper to finally get the driver installed and actually working! Yeah, that's the good news. 

I'm in exactly the same boat and I guess we will see more of this to come as more ppl install the beta.

What irks me is that my card installs automatically on previous versions and now, no longer. anyway...

I'm exactly in the position where you were before you messed around. Ndiswrapper, via Feisty, says the card is not present.

From an alternative viewpoint, Network manager says no wireless cards. Device manager reports a PCMCIA card with appropriate chipset designation.

What exactly did you mess about with? My messing about hasnt led me down the right path yet.

Just point.... 
Thanks.

Update: Dont let ndisgtk (graphic installer for ndiswrapper) fool you with its "no device" status after you have installed the windows driver.
Just go ahead to the network manager and continue configuring. Mine is working fine and it /*still*/ says "no device". 
I too had problems with connecting to my AP/Router with WEP. Some true non-specific messing about sorted that. Like resetting the WEP keys a few times on both the Router/AP and on the laptop. Maybe the order, can't explain it. Go figure.

---

### Post by kolslorr on 2007-03-31
Just get rid of Network Manager, it sucs

---

### Post by zonetripper on 2007-03-31
> **kolslorr said:**
> Just get rid of Network Manager, it sucs

I apologise: what I referred to as network manager is System>Administration>Network as opposed to Network Manager which I now understand to be a seperate app.

Newbeh mistake ;)

---

### Post by mells on 2007-04-25
I'm sorry not to be much help, but I have the same problem with FF and my trendnet wireless. It works out the box in edgy but doesnt see it at all in FF. I have the same problem when using Open Suse 10.2 also, all require a wired connection.... :-(

I've just gone back to using edgy till I have the time a patience to work it out.

---

### Post by Peacemaker/Dispatch on 2007-04-27
this fixed it for me in feisty, for some reason they Blacklisted the drivers for my wifi card's chipset(RLT8180) I just unblacklisted it and feisty found my card 

open the blacklist file with:     sudo gedit /etc/modprobe.d/blacklist

then i removed the rtl8180x entry at the bottom
then it found my card in System>administration>network

also i had to add an extra character to the end of my essid because some bug was dropping off the last character

if you put in 12345678 the computer sees 1234567
so just put in 12345678x and the computer will see 12345678

hope that helps

update: [https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/88430](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/88430)
heres a link to the bug report, apparently this driver was making some computers crash 
worked for me though, use this trick at your own risk

---

### Post by persev on 2007-08-14
> **Peacemaker/Dispatch said:**
> this fixed it for me in feisty, for some reason they Blacklisted the drivers for my wifi card's chipset(RLT8180) I just unblacklisted it and feisty found my card 

open the blacklist file with:     sudo gedit /etc/modprobe.d/blacklist

then i removed the rtl8180x entry at the bottom
then it found my card in System>administration>network

also i had to add an extra character to the end of my essid because some bug was dropping off the last character

if you put in 12345678 the computer sees 1234567
so just put in 12345678x and the computer will see 12345678

hope that helps

update: [https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/88430](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/88430)
heres a link to the bug report, apparently this driver was making some computers crash 
worked for me though, use this trick at your own risk
Thanks this worked for me on a pcmcia netgear card.

---

