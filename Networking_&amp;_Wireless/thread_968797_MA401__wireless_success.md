---
title: "MA401  wireless success"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by prconnor@gmail.com on 2008-11-02
Hello,

I have had quite a lot of trouble getting my netgear MA401 (802.11b pcmcia card) to work with Ubuntu 8.04, where it has worked easily with several other distros over the last several years.  The problem seems to have been a conflict with orinoco and hostap and to have a rather simple solution.  It seems to have been corrected by editing /etc/modprobe.d/blacklist as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

I appended the following to blacklist:

```
# possible conflict with orinoco drivers
blacklist hostap_cs
blacklist hostap
```

I had to reboot my computer twice to get it to start working.  I was then able to configure my wireless setting by clicking the network icon on the task bar.  I hope this will help someone.

-Phil

---

### Post by karlatsaic on 2008-11-04
It turns out that Intersil Prism 2.5 wifi chipsets also can use either the orinoco or hostap driver. After the Intrepid 8.10 upgrade and subsequent kernel updates, the hostap driver was selected. THANKS for the blacklist of hostap tip. My wireless on my old Compaq Presario 2100 is finally humming along again and I really like the new Network Manager 0.7 - quite an improvement over both the old one with Hardy as well as wicd (which has NO vpn support).

---

### Post by oyankee on 2008-11-04
> **karlatsaic said:**
> It turns out that Intersil Prism 2.5 wifi chipsets also can use either the orinoco or hostap driver. After the Intrepid 8.10 upgrade and subsequent kernel updates, the hostap driver was selected. THANKS for the blacklist of hostap tip. My wireless on my old Compaq Presario 2100 is finally humming along again and I really like the new Network Manager 0.7 - quite an improvement over both the old one with Hardy as well as wicd (which has NO vpn support).
span.jajahWrapper { font-size:1em; color:#B11196; text-decoration:underline; } a.jajahLink { color:#000000; text-decoration:none; } span.jajahInLink:hover { background-color:#B11196; }
Did not helped me to blacklist hostap. i have Prism 2.5 Intersil chipset. Any ideas?

---

### Post by oyankee on 2008-11-04
Ok,
so I added this to /etc/modprobe.d/blacklist

blacklist hostap
blacklist hostap_cs
blacklist hostap_pci

and I added this to /etc/modules

orinoco_pci

It works, device is visible and working as eth1 after every start.

---

### Post by karlatsaic on 2008-11-04
I neglected to say that I specifically blacklisted hostap_pci, as that is what my card uses (not hostap_cs). Glad you figured it out. Better to be real specific in these posts. I'll do the explicit addition to /etc/modules as well, although it has not been necessary for me.

---

### Post by prematurebaby on 2008-11-04
I still can't get my wireless internet to work. I'm using a prism 2.5. It reads the networks and can only connect to them if you do manual DHCP. But no internet. All that works is hard wire.

---

### Post by prematurebaby on 2008-11-04
Ok now I got it working you have to do the following.
```
sudo iwconfig
```
then you need to put the mac address into your network connections under BSSID. I have mine under manual DHCP and now its working great!

---

### Post by prematurebaby on 2008-11-04
Actually it was what oyankee did. Then I got it working. Thanks oyankee!

---

### Post by prconnor@gmail.com on 2008-11-10
Wow, I'm happy, and somewhat surprised that someone else had benefit from my experience.  I don't really know too much and nearly didn't post as I figured that everyone else that reads these posts probably knows so much more than I do.

As an after thought I wondered if the hostap modules would perform better than the orinoco set of modules.  So I swapped and blacklisted them instead, and unblacklisted the hostap modules and rebooted my computer.  It seems to work with either set of modules.  I have left the hostap modules unblacklisted as it seems that I get better performance with them, altough I have made no quantitative assessment.

currently the applicable portion of /etc/modprobe.d/blacklist looks like this


> # possible conflict with orinoco drivers
#blacklist hostap_cs #             62868  1 
#blacklist hostap  #              110724  1 hostap_cs

# possible coflict with hostap drivers
blacklist hermes
blacklist orinoco
blacklist orinoco_pci
blacklist orinoco_cs
blacklist orinoco_plx

Best of luck to all of you.  And thank you to the Ubuntu community for making a system that is pleasant to use.  I am running Ubuntu now for about two weeks and am rather pleased.

-Phil

---

### Post by oneguy77 on 2008-12-29
I have installed 8.10 my laptop uses Prism 2.5 Wavelan chipset , tried blacklisting hostap dint help ,my wifi uses WPA but orinoco displays only WEP . So I removed all the changes.

[I]00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
[/I]

My issue is it tries to connect and it displays the authentication required dialog box but nothing works !!!!.

Because of this I'm forced to use wire to connect to my router. Ubuntu experts please help.

---

