---
title: "wireless network not re-connecting"
date: 2013-10-17
forum: Networking &amp; Wireless
---

### Post by jgw on 2013-10-17
I have a wireless network in my home.  I have no problem connecting to that network.  Every once in a while, however, that network will disconnect (I have no idea why).  When it does disconnect it does not re-connect even though it is set to automatically do that.  When I see it has disconnected I have absolutely no problem just re-selecting the same network and it hooks right back up.  I can't figure out, obviously, how to fix it so that it reconnects if it gets unconnected.

All of the above was true.  However, then my wireless network flat out failed and would not reconnnect.  I then re-booted and then connected and am now connected (have been for about 20 minutes), was able to hook up the vpn, etc.  Everything will be fine until it disconnects itself again.  I swear it used to automatically connect on reboot but that too is no longer happening.  

I suspect a problem with how the the network is setup rather than a hardware problem as it will probably remain up for a day or so before it fails again which tells me its unlikely to be a hardware problem.  I have, incidentally, searched for any documentation on simply connecting to a wireless network to no avail.  If there is such, I would appreciate somebody just pointing the way.

Thank you........

---

### Post by varunendra on 2013-10-18
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Keep the script ready and run it again as soon as it disconnects again. Post back that report as well.

---

### Post by jgw on 2013-10-18
Put results in pastbin:
[http://pastebin.ubuntu.com/6260038/](http://pastebin.ubuntu.com/6260038/)

---

### Post by varunendra on 2013-10-18
It is difficult to suggest many things with this chip -
```
Bus 001 Device 005: ID **0bda:8172** Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
```
..except maybe try changing the channel to 1 or 11 (11 seems less crowded) or disabling N channel in the router. But maybe we should wait till the next report when it disconnects.

What is the average speed that you get with this adapter? Like a guess about local file transfer speeds, or for internet you can use speedtest.net. Your current "shake hand" speed with the router is 150 Mb/s. Disabling N-channel will cause it to drop it to 54 Mb/s or less. But in practical usage, it may *sometimes* improve both the speed and connection stability when the N channel is causing troubles. It can only be tested, not guessed.

And please post back the output of -
```
sudo cat "/etc/NetworkManager/system-connections/NETGEAR 1"
```
Be sure to remove or obscure any sensitive data (like your security password) in the output before posting here.

---

### Post by jgw on 2013-10-20
thanks for the reply.......

The speed issue is complicated by the fact that I am also running with hma/vpn and that makes a real difference (although its fast under ubuntu than it is with xp <g>)  There is also no rhyme or reason when I lose my connection.  Its now been up for 2 days but will, eventually (probably sooner than later) stop.  then I have to either just click on the network and it will start right up or, when that doesn't work, I reboot and that seems to get everything working again.  As far as I can tell, when it does go down there is no effort, on the part of ubuntu, to even try and restart.  I will continue to mess with this.

My speed, under the current configuration varies wildly.  It will run between something like 48kb to 1.?mb     I suspect the average is around 600kb.

---

