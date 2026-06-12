---
title: "Can't Connect to Linksys Wireless-B Router with WEP Enabled"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by mlnease on 2009-05-12
Hello,

I'm connecting to the internet via a Linksys Wireless-B 802.11-B Broadband Router.  It all goes swimmingly unless I enable WEP (or any kind of security) on the router, then I instantly lose the connection and can't reconnect no matter how I reconfigure in Network Manager.

I've searched and found hundreds of posts with the pertinent parameters but nothing that seems to directly address this issue.  I'd be most grateful for any suggestions.

Thanks in advance.

mike

p.s.  I've looked at the option of installing wicd and using that instead of network manager.  However, installing wicd will remove network manager and I have no working wired connection; also, installation of wicd seems to require the removal of ubuntu-desktop which I would like to avoid if at all possible.

---

### Post by spiderbatdad on 2009-05-12
what is your wireless card?
```
sudo lshw -C net
```

---

### Post by mlnease on 2009-05-12
> **spiderbatdad said:**
> what is your wireless card?
```
sudo lshw -C net
```

Thanks for the quick response.  It's a Linksys Wireless-B 802.11B--

~$ sudo lshw -C net
[sudo] password for mn: 
  *-network:0             
       description: Wireless interface
       product: WMP11v4 802.11b PCI card
       vendor: Linksys, A Division of Cisco Systems
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:0c:41:73:e7:e6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsipnds driverversion=1.52+Linksys,06/27/2003,3.0.6.20 ip=192.168.1.104 latency=32 link=yes maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:0f:fe:3d:87:6c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

---

### Post by spiderbatdad on 2009-05-12
Are you using ndiswrapper for this card? I believe you should be using the bcm43xx frimware.
Have you tried WPA instead of WEP? Also some older cards will not work with WPA without a frimware upgrade...usually this is done in a windows environment for cards with proprietary firmware, so as not to damage the card and or bios. Came across a long rant here, and some referenced questions/answers.

You can usually get information on whether the card has WPA support from the system dmesg...maybe near tail```
dmesg | tail
```If not ```
dmesg > ~/Desktop/dmesg.txt
```

---

### Post by mlnease on 2009-05-12
[QUOTE=spiderbatdad;7267259]Are you using ndiswrapper for this card?

Yes--

 I believe you should be using the bcm43xx frimware.

Maybe so, but I hope not--the learning curve for making ndiswrapper was...challenging.  I've got the hang of it after many installs and versions and am loath to give it up unless necessary.

Have you tried WPA instead of WEP? 

Nos--I try that next and get back to you.

Also some older cards will not work with WPA without a frimware upgrade...usually this is done in a windows environment for cards with proprietary firmware, so as not to damage the card and or bios. Came across a long rant here, and some referenced questions/answers.

I'll bear it in mind--

You can usually get information on whether the card has WPA support from the system dmesg...maybe near tail```
dmesg | tail
```

Here's the output--afraid I don't know what to make of it:

[http://paste.ubuntu.com/171046/](http://paste.ubuntu.com/171046/)

Thanks for your advice and patience.

mike

Checked the router--WPA is not an option, it's WEP or nothing.

---

### Post by spiderbatdad on 2009-05-12
well this looks encouraging:
```
[ 46.188210] ndiswrapper (set_iw_encr_mode:710): setting encryption mode to 0 failed (00010003)
[ 46.188220] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
```Need some more time to look at it though...In the mean time could I convince you to cut all that dmesg output from your previous post and paste it to Ubuntu pastebin:
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)
Then replace all that text with a link to your pastebin, after you have pasted. Then do a clean boot...run the demsg >> ~/Desktop/dmesg.txt command again...and copy it to another pastebin?

---

### Post by spiderbatdad on 2009-05-12
Well. a couple of ideas. #1 would be trying WPA personal via your router settings. Also I have had some better results with HP's using the boot option pci=routeirq. There is an explanation here on how to apply boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) You would look at the section: Change Boot Options Temporarily For An Existing Installation.
And if it helps you. Then change permanently.
Finally, you might consider upgrading. The wireless drivers are improved in Jaunty.

---

### Post by mlnease on 2009-05-12
> **spiderbatdad said:**
> well this looks encouraging:
```
[ 46.188210] ndiswrapper (set_iw_encr_mode:710): setting encryption mode to 0 failed (00010003)
[ 46.188220] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
```Need some more time to look at it though...In the mean time could I convince you to cut all that dmesg output from your previous post and paste it to Ubuntu pastebin:
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)
Then replace all that text with a link to your pastebin, after you have pasted. Then do a clean boot...run the demsg >> ~/Desktop/dmesg.txt command again...and copy it to another pastebin?

This seems redundant, hope I haven't misundersood:

[http://paste.ubuntu.com/171054/](http://paste.ubuntu.com/171054/)

---

### Post by spiderbatdad on 2009-05-12
Also not sure what is going on with all that ufw blocking. The source is your machine and it results in FIFO time out. Some process is running that should NOT be?

---

### Post by spiderbatdad on 2009-05-12
> **mlnease said:**
> This seems redundant, hope I haven't misundersood:

[http://paste.ubuntu.com/171054/](http://paste.ubuntu.com/171054/)

Was wondering if the boot option would clear that up...or upgrading. Have you added the line ndiswrapper to your /etc/modules file? The encouraging part was the support for wireless encryption.

---

### Post by mlnease on 2009-05-12
> **spiderbatdad said:**
> Also not sure what is going on with all that ufw blocking. The source is your machine and it results in FIFO time out. Some process is running that should NOT be?

OK--ran 'ufw disable' and still no luck.  On to the next post--

---

### Post by mlnease on 2009-05-12
> **spiderbatdad said:**
> Was wondering if the boot option would clear that up...or upgrading. Have you added the line ndiswrapper to your /etc/modules file? 

Yes, just did--no luck.

> **spiderbatdad said:**
> The encouraging part was the support for wireless encryption.

Yes, very encouraging...Well.  Looks like bareback or upgrade.  The horrors of forcing my beloved Ubuntu to conform yet AGAIN to ndiswrapper vie with the expense of an new router and a new PCI card.  Not for the first time, by any means.  I have no faith at all that Ubuntu will have by now accomodated the Linksys router/PCI card.  Why should they?

I'll sleep on it and hope that someday I'll eat my words.

Thanks again for your really great patience and advice.

mike

---

### Post by spiderbatdad on 2009-05-12
Sincerely the drivers have improved...however, would not want to encourage an upgrade if you are at all reluctant.
There are some post available where others have solved this problem using the same card: [http://ubuntuforums.org/archive/index.php/t-7319.html](http://ubuntuforums.org/archive/index.php/t-7319.html) for example. You can find others as well. Best of luck. Hope you get this fixed to your satisfaction. I have 2 laptops running 9.04 an ancient IBM T-30 (no WPA or WEP support) and a new Acer Aspire One, which connects to WPA networks perfectly using the ath5k module.

---

### Post by mlnease on 2009-05-12
> **spiderbatdad said:**
> Sincerely the drivers have improved...however, would not want to encourage an upgrade if you are at all reluctant.
There are some post available where others have solved this problem using the same card: [http://ubuntuforums.org/archive/index.php/t-7319.html](http://ubuntuforums.org/archive/index.php/t-7319.html) for example. You can find others as well. Best of luck. Hope you get this fixed to your satisfaction. I have 2 laptops running 9.04 an ancient IBM T-30 (no WPA or WEP support) and a new Acer Aspire One, which connects to WPA networks perfectly using the ath5k module.

Upgrading (with the utmost reluctance) as I type this, spiderbatdad--thanks again and if I can still connect to the web when I'm done, I'll get back to you.

Cheers,

mike

---

### Post by mlnease on 2009-05-12
!

---

### Post by mlnease on 2009-05-13
> **spiderbatdad said:**
> Sincerely the drivers have improved...however, would not want to encourage an upgrade if you are at all reluctant.
There are some post available where others have solved this problem using the same card: [http://ubuntuforums.org/archive/index.php/t-7319.html](http://ubuntuforums.org/archive/index.php/t-7319.html) for example. You can find others as well. Best of luck. Hope you get this fixed to your satisfaction. I have 2 laptops running 9.04 an ancient IBM T-30 (no WPA or WEP support) and a new Acer Aspire One, which connects to WPA networks perfectly using the ath5k module.

Good Morning Spiderbatdad,

Words eaten, I'm still on line with Intrepid and it looks great.  A couple of questions though, if you have time:  I notice that System/Administration/Network has changed to System/Preferences/Network Configuration.  Although Network Connection shows that wlan0 is running (and is much stronger and more stable than before--thanks!), Network Configuration can't find the wireless connection at all.  (NetworkManager Applet also says, "No valid active connections found!"  This is a problem since it's in Network Configuration that I need to change the connection type to WEP (since WPA isn't an option on my router).  By the way I notice that ndiswrapper and windows wireless drivers are still installed--but not sure if I'm still using them or how to find out.

Any suggestions?  Thanks in advance and again for all the great help and the encouragement to upgrade.  Intrepid looks really good so far.

mike

p.s.  [http://paste.ubuntu.com/171803/](http://paste.ubuntu.com/171803/)

---

### Post by spiderbatdad on 2009-05-13
I actually thought you would be upgrading to Jaunty...How did you upgrade, through the update manager or clean install? I would not recommend consecutive upgrades through the update manager. I would recommend burning a Jaunty disk. Why not try it out on a partition rather than the whole disk...can you split the space with your Intrepid install, until you realize how awesome it is?

---

### Post by mlnease on 2009-05-13
> **spiderbatdad said:**
> I actually thought you would be upgrading to Jaunty...How did you upgrade, through the update manager or clean install? I would not recommend consecutive upgrades through the update manager. I would recommend burning a Jaunty disk. Why not try it out on a partition rather than the whole disk...can you split the space with your Intrepid install, until you realize how awesome it is?

Hmm, I think I did apt-get dist-upgrade--a bit hard to remember at this point, it took twelve hours followed by a lot of configuring (and it wouldn't allow me to jump to jaunty)...It really looked nice--until it lost all my network connections.  Couldn't find 'em again...since I have no wired connection, I couldn't connect to the internet to troubleshoot it so...reinstalled Hardy.  Lost all my data (no backup hardware, that's the way it goes)...

It's sound advice to burn a Jaunty disk, of course, but no burner (I requested a Jaunty disk by mail).  No hardware budget here I'm afraid (or software for that matter).

So I'm back to square one.  I'd still like to get WEP protection on my router but I guess that just isn't going to be possible in Ubuntu with my current router and PCI card at least until the Jaunty disk arrives.  A pity but that's the way it goes.

Oh, well!  Thanks again for all your time and patience.

mike

---

