---
title: "Multiple SSIDs"
date: 2022-08-18
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2022-08-18
Folks, appreciate where possible it is best to avoid congested channels when choosing which waveband to select but just wondering;  if an AP is able to use multiple SSIDs they will obviously (I think) be on same channel.

Do they interfere with each other.

Geoff

---

### Post by TheFu on 2022-08-19
RF is the physical layer here.  The laws for RF have been the same forever. No way around them.

SSIDs can be on the same or different channels.

On the 2.4Ghz wifi spectrum, there are 3 channels that don't overlap with others (for most of the world).  Those are channels 1, 6, 11.  Choosing any others, causes interference and compromise.  Period. Ain't no way around that.

The 5.8Ghz wifi spectrum has more "channels", but I don't know which overlap since they aren't very useful in my location.  5.8Ghz doesn't like to go through walls, so line of sight is needed in many locations, especially for concrete or brick inner-walled buildings.

SSIDs are just a logical separation, like like a port on an IP connection.  The underlying ethernet can only convey so much traffic at the same time. Wifi is similar, but simultaneous broadcasts (think network speed, not human speed) can only accept 1 signal on 1 channel at a time without negotiated time splicing.  This wasn't part of the older standards, but has been added to newer standards. The trade-off is slower performance for all connections, unless some can be moved to different channels. That's what MIMO is about. There are all sorts of tricks to make more devices appear to have faster connections by dynamically moving data to different channels based on the clients.  Not all clients implement all the standards. Some implement the standards in non-standard ways or in proprietary ways, but as long as transfers are fast enough, few people will notice.

Use as many channels as you can for each device.
Use different, non-overlapping channels, when possible.
Think of SSDs on the same channel like ports in an IP connection OR like a VLAN "tag".

There are lots of settings in wifi-APs that can impact client bandwidth, total bandwidth, and there are lots of other devices in both unregulated spectrums used by other devices like cordless phones, bluetooth, and all those little RF toys our kids have.  I have some tiny race cars that use 2.4 Ghz for their remote control. Many drones/quadcopters do as well.  All of these things cause interference on some level.  Power output, S/N, antenna sensitivity and the ability for each wifi device to filter out junk interference all matter for total connection through put.

BTW, the connection speed displayed in any GUI is a lie.  Never expect to get that when transferring files. It just never happens. Until you have actually tested moving files, don't believe any bandwidth numbers/speeds.

---

### Post by Geoff_Lane on 2022-08-21
> **TheFu said:**
> 
BTW, the connection speed displayed in any GUI is a lie.  Never expect to get that when transferring files. It just never happens. Until you have actually tested moving files, don't believe any bandwidth numbers/speeds.

Oh that is so true, sometimes out of fascination rather than for any productive reason I will use iperf3 between two devices then I'll use dd as follows;

```
dd if=/dev/zero bs=25K count=1024 status=progress | ssh pi@10.19.44.25 'cat > /dev/null'
```

Seldom similar.

I don't get too many issues with network speed, used to use couple of home plugs with an extra AP (different channel) to reach dead spots but the homeplaugs were getting quite hot so I changed extra AP to repeater, I know I lose some speed but the homeplugs were slowing my speed anyway, repeater seems to be working fine even for video streaming.

Geoff

---

### Post by TheFu on 2022-08-21
> **Geoff_Lane said:**
>  ```
dd if=/dev/zero bs=25K count=1024 status=progress | ssh pi@10.19.44.25 'cat > /dev/null'
```
 

 That command is inefficient in a few ways (starting extra processes unnecessarily) and if compression is enabled on ssh, it will go much faster because compression of just zeros is nearly infinite.

Why not just use scp with random data?

---

### Post by Geoff_Lane on 2022-08-22
> **TheFu said:**
> That command is inefficient in a few ways (starting extra processes unnecessarily) and if compression is enabled on ssh, it will go much faster because compression of just zeros is nearly infinite.

Why not just use scp with random data?

The bottom line is, whatever the connection, if it is sufficient for what I am doing then that is fine whatever and commands tell me.

I often wonder at all these increases in speed, a movie takes same time to watch, guess if household has many occupants all doing their own thing then it becomes an issue.

Sometimes ignorance is bliss, the more one knows the more one frets about it 8-)

Geoff

---

### Post by TheFu on 2022-08-22
100% correct.  I have some storage with terrible performance, but since it is used for backups and the backups take 2-4 minutes a day, the speed issue doesn't really matter to me.

---

### Post by Geoff_Lane on 2022-08-23
> **TheFu said:**
> 100% correct.  I have some storage with terrible performance, but since it is used for backups and the backups take 2-4 minutes a day, the speed issue doesn't really matter to me.

Horses for courses as the old saying goes.

Geoff

---

