---
title: "BCM4318 wireless signal degradation"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by deadlines on 2007-04-23
Hi all,

I've been monitoring the forums to see if this issue would crop up with anyone else but I've yet to see my exact problem.  With that being said, here is what I'm experiencing, if anyone has any idea what might be causing it I'd be glad to try their solution.

The issue I'm running into is that I can connect to my router with minimal problems but given enough time the connection degrades to a point where websurfing becomes almost impossible.  After looking around a bit trying to track the issue down, I realize I am seeing an increasing number of "RX invalid Crypt" packets in iwconfig.  

Here's an example:
```
erussell@geedorah:~$ iwconfig wlan0
wlan0     IEEE 802.11b/g  ESSID:"Mayhem"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.417 GHz  Access Point: 00:18:3F:A5:45:D9   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=40/100  Signal level=-76 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  **Rx invalid crypt:34**  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

At the moment I just rebooted the laptop so as you can see the RX invalid crypt count is rather low.  If I leave the laptop connected, the RX invalid crypt count continues to climb and it is not uncommon for me to return home after working all day to discover this count at 300k or higher, with the connection being adequate enough to support an IM connection but not much else.  As I said before, attempting to contact websites or do any heavy file xfers at that point becomes an exercise in frustration.  The only cure I've been able to find is to bounce the laptop and reconnect.

Some more details:

I'm running Feisty on a Dell Inspiron 2200 which comes with a BCM4318 wireless chipset.

```
erussell@geedorah:~$ lspci | grep Broadcom
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I'm currently using the BCM43xx firmware from this post:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318)

The router I'm using is one purchased through AT&T for my DSL connection, it is a 2WIRE 2700HG-B, configured for WPA w/ TKIP and no MAC filtering.  The SSID is NOT being broadcast (I don't know if this is significant).

Checking kern.log I see a constant stream of the following error:

```
Apr 23 21:30:16 geedorah kernel: [ 2328.844000] TKIP: ICV error detected: STA=00:18:3f:a5:45:d9
Apr 23 21:30:16 geedorah kernel: [ 2328.844000] TKIP: ICV error detected: STA=00:17:ab:e2:07:c5
Apr 23 21:30:25 geedorah kernel: [ 2337.796000] TKIP: ICV error detected: STA=00:17:ab:e2:07:c5
Apr 23 21:30:33 geedorah kernel: [ 2346.040000] TKIP: ICV error detected: STA=00:18:3f:a5:45:d9
Apr 23 21:30:45 geedorah kernel: [ 2357.864000] TKIP: ICV error detected: STA=00:17:ab:e2:07:c5
Apr 23 21:31:05 geedorah kernel: [ 2377.828000] TKIP: ICV error detected: STA=00:17:ab:e2:07:c5
Apr 23 21:31:25 geedorah kernel: [ 2397.792000] TKIP: ICV error detected: STA=00:17:ab:e2:07:c5
Apr 23 21:31:45 geedorah kernel: [ 2417.860000] TKIP: ICV error detected: STA=00:17:ab:e2:07:c5
```

Furthermore, each time this error occurs the following is logged in messages:
```
Apr 23 20:25:34 geedorah kernel: [85290.684000] printk: 15 messages suppressed.
Apr 23 20:25:34 geedorah kernel: [85291.552000] printk: 1 messages suppressed.
Apr 23 20:25:44 geedorah kernel: [85301.376000] printk: 13 messages suppressed.
Apr 23 20:26:04 geedorah kernel: [85321.344000] printk: 9 messages suppressed.
Apr 23 20:50:24 geedorah kernel: [86780.860000] printk: 15 messages suppressed.
Apr 23 20:50:44 geedorah kernel: [86800.828000] printk: 1 messages suppressed.
Apr 23 21:18:33 geedorah kernel: [ 1625.456000] printk: 34 messages suppressed.
Apr 23 21:22:25 geedorah kernel: [ 1857.864000] printk: 2 messages suppressed.
Apr 23 21:30:25 geedorah kernel: [ 2337.796000] printk: 6 messages suppressed.
```

Here are some things I've tried to track this down:

1.  Changed my router to operate in 80211b mode exclusively (have also tried it in 80211g but to no avail).  It is currently set back to operate in b & g mode.

2.  Shortened my WPA key to the minimum of 8 characters and stripped out special characters.

3.  Connected the laptop to a Linksys router, this seems to be a much lower RX Invalid crypt count although I did still get some.  Sadly this router belongs to a friend so I was unable to test it for very long, maybe an hour tops.

4.  Set my router to broadcast my SSID, this did not seem to make a difference.

5.  Booted into Ubuntu passing the, "noapic" option to the kernel, again no change.

At this point I'm out of ideas, not only does the connection degrade over time but I cannot for the life of me obtain a connection higher than 11Mb/s.  Any ideas or suggestions on what the cause might be would be most welcome, this machine had XP on it about a week ago and there were never any problems with the wireless so I'm fairly sure this is not a hardware issue.  Finally, I have not tried to use ndiswrapper as of yet, but I'm on the verge since I'm not too confident in these drivers anymore.

---

### Post by Merlin_Guy on 2007-04-23
I have an Acer 5003WLMi and I have the same issues.  I have to use the iwconfig command to get the encryption key set since the network manager doesn't seem to handle this correctly.

My Link Quality starts at about 70/100 and then can drop much lower even when laptop is sitting a foot from the wifi router.

The ndiswrapper which worked well under Dapper and Edgy fails completely.

---

### Post by deadlines on 2007-04-24
Another strange thing I noticed after posting this, a large bulk of the TKIP errors I am seeing in my kern.log seem to be origination from this MAC address, "17:ab:e2:07:c5" 

After running iwlist scan I realized this MAC address is not any of the WAPs in my area.  Upon further investigation I realized it is actually my Wii!  Talk about weird, anyways I disabled the Wii standy mode connect so it's not always on and went to bed.  This morning I'm still seeing RX invalid crypts though, so most likely it's not the cause.  Touching upon your signal quality, I have never gotten better than 46/100.

What kind of router are you using?

---

### Post by deadlines on 2007-04-24
Bumping this thread, does anyone have a clue on this?

---

### Post by Merlin_Guy on 2007-04-24
I have a Linksys Wireless G cable modem router and Wifi.  When I used ndiswrapper on previous releases I never had a problem with connection or speed.  There are other threads that talk about speed hit using fwcutter.  

Also under Feisty my touch pad is erratic and very few of my applets show up.  As far as my Acer laptop is concerned Feisty is a complete bust so I will probably dig out my Edgy disk and give Fiesty a pass.  Well, at least until someone fixes things.

---

### Post by deadlines on 2007-04-24
I've been doing a little digging on the side today and found a suggestion to try upgrading my kernel to 2.6.20.7 and to upgrade IEEE80211 SoftMAC to version 1.2.16.

Assuming I'm not already up to date on these I plan to give this a shot when I get home and will post my results.

---

### Post by PartisanEntity on 2007-04-24
I have a broadcom chip too and I have similar issues:

In my case the signal strength does not degrade, but it does not appear to be as good as it was in Edgy. For example in Edgy, I had 100% signal strength according to Network Manager all the time.

Now it is down to about 58% all the time.

Also, it takes me much longer to connect to my home wifi network, in Edgy the connection was much quicker.

I am actually sick and tired of the tinkering I keep having to do to get my broadcom card to work and so I have ordered an Intel Pro Wireless card.

---

### Post by dyrer on 2007-04-24
I have Netgear WPN311 and signal strength is 23-24% and with Windows XP is 90%, what cause this ?

---

### Post by thomasbaker on 2007-04-25
I have a dell b130 and my signal is around 58% also, and the laptop is only about 4 feet from the router.  I hope someone has a fix for this.  I can't figure it out.

---

### Post by PartisanEntity on 2007-04-25
An update to my case:

It takes ages to connect, I must try about 4-5 times in order to get Network Manager to connect. It tries to connect, then gives up and I have to repeat the process.

There definitely seems to be a performance degradation as far as my broadcom wifi card and Feisty are concerned.

---

### Post by deadlines on 2007-04-25
I've found the solution, at least for the BCM4318 chipset.  

Here's how I fixed it:

Downloaded the ndiswrapper drivers from this post - [http://ubuntuforums.org/showthread.p...hlight=BCM4318](http://ubuntuforums.org/showthread.p...hlight=BCM4318)

Downloaded Wicd from their site - [http://compwiz18.ig3.net/wicd/wb/pages/releases.php](http://compwiz18.ig3.net/wicd/wb/pages/releases.php)

Uninstalled bcm43xx drivers package

Installed ndiswrapper drivers & wicd packages

Cranked up wicd daemon - sudo /etc/init.d/wicd start

Cranked up wicd gui - sudo /opt/wicd/gui.py

Configured wicd and connected to my WAP no problems.

The wireless connection no longs reports the TKIP ICV errors, and I am connecting at the full 54Mb/s that my router is capable of handling, whereas before it was only connecting at 11Mb/s max.

Frankly I'm not sure Wicd is necessary, however, I went ahead and tried it anyways as network-manager just seemed to be really flaky with this chipset.  I'd be curious to hear how ndiswrapper drivers perform using network-manager, as frankly I really like the pptp plugin for it to create VPN connections.  Anyways, a few minor issues to wrap up (setting up wicd daemon & tray applet to start on boot) and this is a shut case for me.  I'm also happy to report that although I left this laptop connected all day while I was at work, "iwconfig" is no longer reporting any of the, RX Invalid Crypt packets... it's at 0!  woot.

Anyways this worked for me on a BCM4318 chipset on a Dell Inspiron 2200, hopefully it helps someone else out as well although your mileage may vary.  ;)

Cheers

---

### Post by d-Pixie on 2007-08-26
Adding some new info to this post ... The ones of you out there running fiesty and the new BCM43xx driver package; these are very new and while not beat still not perfect ;o)

I to experience some strangeness whit this card and the nm-applet. My signal is always around 50%. The signal degrades over time. I get the "TKIP: ICV error detected". Havent checked my speed per sé, but it's been good enough so that I'm not suspicious ;o)

Heres how I "solved" it ... Dump a new shell script somewhere:

```
#!/bin/bash
modprobe -r bcm43xx
modprobe bcm43xx
```

Set +x on the script. Create a launcher with: gksu -S /path/to/script and run when needed (nm-applet notices the reload and reconnects automagicaly) ... All it does is to reload the driver for the card. But it seams to help. Any more info on how to _FIX_ this problem, with the bcm43xx drivers, would be gold.

Also, my problem is new. It hasn't happened before. Worked like a charm ever since I fixed it when fiesty first came. But now I got problems. Should indicate environmental factors?

---

### Post by PartisanEntity on 2007-08-26
I forgot about this thread, I actually ended up buying the intel wifi card and replaced the broadcom. I have not had to worry about signal degradation anymore, the card works great and right out of the box.

---

### Post by MaGaM on 2008-06-15
I was experiencing the same problems. My setup is Ubuntu 8.04 Hardy Heron with network-manager (v0.6.6-0ubuntu5) package installed.
The Linksys wireless USB54Gv4 dongle I own worked out of the box with the native rt2500usb driver. But the signal strength was far lower then under windows even when sitting right beside the access point in a clear line of sight.

Today I forgot to take that dongle with me, so I managed to get another one, a Belkin F5D7050 v1 USB dongle. It didn't seem to work out of the box, so I tried the p54usb, rt2500usb and rt73usb native drivers. Once again the rt2500usb kicked in and network-manager(-gnome) saw my access point and could connect, though after giving it much effort. Walking away a few meters, made the signal strength considerably lower. Resulting in an inadequate network connection.

Ok, I thought, well maybe those native wireless linux drivers aren't that mature yet and thus installed ndiswrapper and the windows wireless drivers. Although this did boost the reception to my feeling, after walking a few meters keeping a clear line of sight with the router still resulted in an inadequate network connection. 

Searching and searching on the net for solutions. Found something to change the wireless transfer rate (e.g. iwconfig command), but it seemed that the windows driver did not support it through ndiswrapper. Then I found this thread saying that network-manager somehow 'capped' the network connection. Heck, let's give it a try and I uninstalled network-manager and network-manager-gnome packages. Now I'm connecting with a wireless network through a terminal and wonderously the network connection is more then adequate also when walking a few meters.

Apparently network-manager's 'managing' of wireless networks and such is suboptimal. So I recommend in the case of low reception in comparison when in windows, try it without network-manager and see if it works better then.

---

