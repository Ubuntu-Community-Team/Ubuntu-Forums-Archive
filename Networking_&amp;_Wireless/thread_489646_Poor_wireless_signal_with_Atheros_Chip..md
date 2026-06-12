---
title: "Poor wireless signal with Atheros Chip."
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by wastedfluid on 2007-07-01
Hello,

I upgraded to 7.04 Fiesty this past weekend.  Had been using 6.06LTS for the longest time.  On 6.06, I had to use ndizwrapper to get the networking to work wirelessly..

When I upgraded to 7.04 Fiesty, it "just worked".  But I notice one thing.  Five feet from my router, in the same room, I get 50-59%.  If I place my router and laptop together, The highest I see is 79%.

On Ubuntu 6.06LTS, I never rememeber having this issue.  I would get 50-59% outside in the yard.

Here's what I'm running:

Router: My essentials(A belkin)

Computer: Acer 5100. 1.6ghz, 1gb ram, ubunt 7.04 lts.. atheros AR5005G chip.

here's what iwconfig is spitting out:

```

wastedfluid@wastedfluid:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"STRIAGHT CHEVY"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:47:C5:5E   
          Bit Rate:54 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/94  Signal level=-39 dBm  Noise level=-93 dBm
          Rx invalid nwid:2948  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

and lspci

```

06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC 
(rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0418
        Flags: bus master, medium devsel, latency 168, IRQ 20
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>


```
Any help is GREATLY appreciated.  It's no longer wireless if I start dropping my connection before I even GET outside!  Thanks!

---

### Post by FeestBijtje on 2007-07-01
Perhaps buying an new wireless router...

---

### Post by wastedfluid on 2007-07-01
> **FeestBijtje said:**
> Perhaps buying an new wireless router...

Well, with 6.06LTS, I was peaking 80-90% just 5 feet away.

Outside, in the yard, I would get 50-60%.

I upgraded to Fiesty, and I'm getting 50-60% 5 feet away.

I don't think it's the router..

---

### Post by tturrisi on 2007-07-01
There's nothing wrong with your connection.  The signal is just fine.
Signal level=-39
The % signal level reported in other apps is incorrect and inaccurate.
My atheros card: iwconfig says Signal level=-52 dBm, net-admin says 85% and I'm 6 feet from my AP.
The only accurate signal level is "can you connect or not" !

Change your AP channel to 11 or another channel w/ less overlap and the reported signal levels will also change.

---

### Post by digicrime on 2007-07-01
Im right next to mine and it says 60-69% its built in wireless so thats a reilef that its not just a wireless issue

---

### Post by wastedfluid on 2007-07-02
> **digicrime said:**
> Im right next to mine and it says 60-69% its built in wireless so thats a reilef that its not just a wireless issue


Well, switching to channel level boosted my signal to 60-65.  I feel somewhat better, for whatever reason.  Mine is built in - too.  So I don't think i'm ging to worry about it anymore.

---

### Post by thierce on 2007-07-02
Try reinstalling the WiFi drivers but WITH NDISWRAPPER. I had similar "problems" with my card (Well I was glad everything worked :P) and after installing drivers with ndiswrapper the connection and the speed improved.

---

### Post by Riel on 2007-07-02
My signal is 30%. In XP it was near 100%.

But the connection in Ubuntu is much smoother and FASTER.

Those % don't say much. Just do some speedtest or so.

---

### Post by wastedfluid on 2007-07-02
> **thierce said:**
> Try reinstalling the WiFi drivers but WITH NDISWRAPPER. I had similar "problems" with my card (Well I was glad everything worked :P) and after installing drivers with ndiswrapper the connection and the speed improved.

Everything I've read about NDISWRAPPER for the AR5005G is bad.  Most people are referring people to install madwifi, as it comes with atheros 5005G drivers.  However, I'm not going to start battling Ubuntu over sginal stregnth.  I walked outside, had 4% internet signal.. but still was running at 3mbps/1mbps .. so the signal stregnth is OBVIOUSLY a bogus reading.  Test your signal before you assume it's correct is the best thing I can tell you.  I'm not about to try to fix something that isn't really broken I guess.  Sorry for the waste of thread; hope this helps someone else.

---

### Post by tturrisi on 2007-07-02
in a nutshell:

> Signal strength is defined in 802.11 as the Received Signal Strength Indicator
(RSSI). RSSI, is intended to be used as a ‘relative value’ within the
chipset. This is a 1-byte value so that it could have values ranging from
0 to 255, but vendors prefer to use arbitrary scales from 0 to RSSI_Max
where the latter is vendor-specific (for instance, Cisco uses 101, Symbol
31, Atheros 60).  It is not associated with any particular power scale 
(e.g. mW) and is not required to be of any particular accuracy or
precision. The RSSI value is used internally by the microcode in the
adapter and this is why vendors are not forced to use a compatible
standard. As an example of its use, if the RSSI value is below some
threshold, the NIC knows that the channel is idle. Therefore, the signal
strength numbers reported by an 802.11 card will probably not be
consistent between two vendors, and should not be assumed to be particularly
accurate or precise.

---

### Post by Supandero on 2007-07-05
In the "for what it's worth category" , I too have low txpower on my Atheros chip set.  I have a Lenovo T60 that connects just fine in XP, with ranges throughout the house.  But, when trying to connect with Ubuntu to two different routers, SMC and Buffalo, I find that I must be within 5-6 feet, or I loose connection.  It is not a matter of receiving, as the utility detects all the wireless routers that I see in XP.  

The power setting from the utility claims that I have 8dbM, which is about what I would expect for the range.  Since the intensity falls off as 1/r**2, 4x would give a minimum range increase 2x.  Practically speaking, it must be more, from observation.

I have tried using the iwpriv command to sed the power level, but am denied by the driver.  Needless to say, this is somewhat frustrating.  The Lenovo Thinkvantage software will allow you to set the txpower, but there doesn't seem to be any equivalent command that I can find in linux.

---

### Post by tturrisi on 2007-07-05
lots of info here re signals, etc.:
[http://madwifi.org/wiki/UserDocs](http://madwifi.org/wiki/UserDocs)

---

### Post by Supandero on 2007-07-07
Thanks for the info on the documents, but I have tried all of that.  Infact, I can change the power using the iwconfig command, and then view it using the iwlist command.  However, as soon as you touch the network manager and try to connect, the power returns to the value of 8dbM.  There must be a config setting somewhere that can be changed.

---

### Post by tturrisi on 2007-07-08
> **Supandero said:**
> Thanks for the info on the documents, but I have tried all of that.  Infact, I can change the power using the iwconfig command, and then view it using the iwlist command.  However, as soon as you touch the network manager and try to connect, the power returns to the value of 8dbM.  There must be a config setting somewhere that can be changed.

LOL!  Yes, there is.  Get rid of network-manager & use net-admin (system > administration > networking)

---

### Post by marktechey on 2007-07-09
This bug was reported in launchpad. Here is the fix [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/69709](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/69709)

I had this problem as well

---

### Post by tava0002 on 2007-07-12
> **marktechey said:**
> This bug was reported in launchpad. Here is the fix [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/69709](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/69709)

I had this problem as well

I have the same issue as the original poster using Xubuntu but have a AR5212 chipset which is using the default Windows restricted drivers, ath_pci I believe.  I get wireless working with WPA but if I go the next room I lose the connection even though signal to noise is good, but kind of defeats the purpose of wireless.  I have another wireless machine that works fine from the other side of the house connecting to same router.  

Does this bug only address that an inaccurate signal value is being reported?  because to me it sounds like there's a fundamental problem with the driver, I've read several threads where people With Atheros chipsets can't connect from more than several feet away.

Once they get this ironed out I will be very happy.

---

### Post by tava0002 on 2007-07-13
Switching from ath_pci drivers to ndiswrapper worked like a charm for me.  The signal quality is much stronger now, before it got no higher than 40/100, now it gets up to 80/100 and I can connect from the  other side of the house.

---

### Post by wastedfluid on 2007-07-23
> **tava0002 said:**
> Switching from ath_pci drivers to ndiswrapper worked like a charm for me.  The signal quality is much stronger now, before it got no higher than 40/100, now it gets up to 80/100 and I can connect from the  other side of the house.


I have switched, too.

```

wastedfluid@wastedfluid:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001A) present (alternate driver: ath_pci)
wastedfluid@wastedfluid:~$

```

I downloaded ndiswrapper from Synaptic Package Manager,, and used the drivers I found on ndiswrapper's wiki from Acer... and all you have to do is 

```
 sudo rmmod ath_pci
```

This unloads the ath_pci fauly driver.

```
 sudo rmmod ndiswrapper 
```

and..

```
  sudo modprobe ndiswrapper 
```

it should work after that.  I added this to my blacklist ( sudo nano /etc/modprobe.d/blacklist )

```

# ath_pci does not properly support Atheros 5005G card.  ndiswrapper installed,
# and using a Windows driver in its place.  net5211 is Windows driver
# that works correctly.

blacklist ath_pci


```

Hope this helps someone; if you run into additional problems, this is where I found all my information to fix this problem.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

