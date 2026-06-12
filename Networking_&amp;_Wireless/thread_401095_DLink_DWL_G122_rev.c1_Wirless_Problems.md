---
title: "DLink DWL G122 rev.c1 Wirless Problems"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by DeathStar on 2007-04-04
Hi Everyone,

I am pretty new to Linux and even newer to this forum, so please be patient if I write something stupid. :)
 
I recently set up my system as a dual-boot, running Windows XP Pro and Ubuntu Edgy Eft (6.10) on two hard drives. The system is set up fine and I can boot into either OS with ease. The problem is that I cannot get the Wireless to work. I have read several other forum posts and so have tried several other things.

I am using a D-Link DWL G122 (revision C1) USB wireless dongle. It work perfectly in Windows, but in Ubuntu I cannot get it to work. I checked on some websites and have discovered that this dongle uses the Ralink RT73 chipset (I think).

When I check my network interfaces (Administration > Networking) I can see two entires for the Wireless adapter... **wmaster0** and **wlan0**. I tried configuring them both, but didn't get any response. My network broadcasts the SSID and has DHCP enabled, but iff possible, I want to specify the IP address of the device (due to the way my network is set up).

I then tried editing my **/etc/network/interfaces** file directly but still couldn't get it to work. As a temporary measure, I used an ethernet cable to get online. When connected, I downloaded the **Kubuntu-Desktop** for my girlfriend as see likes it better than the standard Gnome one. In the Kubuntu-Desktop, I found a **Wrieless assistant** tool, which strangely was able to make my USB wireless dongle work, and it picked up the ESSID of my network. I thought that I had solved the issue, but then when I tried it again later. it didn't work again. This makes me think that it's not a driver issue, but I really don't know enough to confirm that.

I have seen that a lot of people have had the same issue that I am having, so I am anxious to get it working. Any help would be greatly appreciated. I can't leave the ethernet cable in forever as it is running across the hallway and is a bit of a hazard.

Thanks,
DS.

---

### Post by Floppyjoe on 2007-04-04
> **DeathStar said:**
> Hi Everyone,

I am pretty new to Linux and even newer to this forum, so please be patient if I write something stupid. :)
 
I recently set up my system as a dual-boot, running Windows XP Pro and Ubuntu Edgy Eft (6.10) on two hard drives. The system is set up fine and I can boot into either OS with ease. The problem is that I cannot get the Wireless to work. I have read several other forum posts and so have tried several other things.

I am using a D-Link DWL G122 (revision C1) USB wireless dongle. It work perfectly in Windows, but in Ubuntu I cannot get it to work. I checked on some websites and have discovered that this dongle uses the Ralink RT73 chipset (I think).

When I check my network interfaces (Administration > Networking) I can see two entires for the Wireless adapter... **wmaster0** and **wlan0**. I tried configuring them both, but didn't get any response. My network broadcasts the SSID and has DHCP enabled, but iff possible, I want to specify the IP address of the device (due to the way my network is set up).

I then tried editing my **/etc/network/interfaces** file directly but still couldn't get it to work. As a temporary measure, I used an ethernet cable to get online. When connected, I downloaded the **Kubuntu-Desktop** for my girlfriend as see likes it better than the standard Gnome one. In the Kubuntu-Desktop, I found a **Wrieless assistant** tool, which strangely was able to make my USB wireless dongle work, and it picked up the ESSID of my network. I thought that I had solved the issue, but then when I tried it again later. it didn't work again. This makes me think that it's not a driver issue, but I really don't know enough to confirm that.

I have seen that a lot of people have had the same issue that I am having, so I am anxious to get it working. Any help would be greatly appreciated. I can't leave the ethernet cable in forever as it is running across the hallway and is a bit of a hazard.

Thanks,
DS.
I have this device and it works on my computer. I did try to install the rt73 driver for the card but I could not get it to work. Somehow it used the native driver rt73usb on my computer. I have a few drivers blacklisted on my computer. These are:
```
blacklist islsm_usb
blacklist islsm_device
blacklist islsm
```
Issue the command:
```
sudo gedit /etc/modprobe.d/blacklist
```
to edit this file.

---

### Post by DeathStar on 2007-04-05
Thanks Floppyjoe. I will try that tonight.

So I need to blacklist those drivers. Once I've done that, do I need to reinstall the new RT73 driver? If so, do you have a link to the driver as it took me ages to find last time.

Cheers,
DS.

---

### Post by Floppyjoe on 2007-04-05
> **DeathStar said:**
> Thanks Floppyjoe. I will try that tonight.

So I need to blacklist those drivers. Once I've done that, do I need to reinstall the new RT73 driver? If so, do you have a link to the driver as it took me ages to find last time.

Cheers,
DS.

I have the rt73 driver installed too but it did not work for me so I also blacklisted it.
the native rt73usb driver binds to the device.

---

### Post by DeathStar on 2007-04-05
Hi Floppyjoe,

I'm sorry. I don't really understand what you're trying to say. Could you explin in a little more detail?

I have blacklisted the drivers you mentioned, but I don't know what to do from there. The device still doesn't seem to be working.

You said that you also blacklisted the RT73USB driver. I don't know how to do this.

Cheers,
DS

---

### Post by Floppyjoe on 2007-04-05
I did not blacklist the rt73usb driver but I did also blacklist the rt73 driver that I installed that did not work for me.

---

### Post by DeathStar on 2007-04-16
Hi FloppyJoe,

That did not work.

I have given up on this for now and am using an ethernet / wireless bridge. I will probably create a new post when I am ready to try again with this.

Thanks,
DS

---

### Post by rama on 2007-04-26
@Floppyjoe I am using the same usb dongle (rev C) and I m having the same problem as deathstar. As far as I can tell you made it work using the driver that is included in the ubuntu cd. I have been trying to get it to work but I allways get the same error when restarting the daemon or calling sudo dhclient wlan0: 
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I can scan for wireless networks, but I can never get an ip. In my tests I have stripped my wifi - router from any security settings.
Could you post your /etc/network/interfaces file so that I could see if I 've written something wrong?
Thx in advance

---

### Post by Floppyjoe on 2007-04-26
> **rama said:**
> @Floppyjoe I am using the same usb dongle (rev C) and I m having the same problem as deathstar. As far as I can tell you made it work using the driver that is included in the ubuntu cd. I have been trying to get it to work but I allways get the same error when restarting the daemon or calling sudo dhclient wlan0: 
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I can scan for wireless networks, but I can never get an ip. In my tests I have stripped my wifi - router from any security settings.
Could you post your /etc/network/interfaces file so that I could see if I 've written something wrong?
Thx in advance


UPDATE: I can't get this dongle to work yet with Feisty. When I try a popup says unable to connect because my hardware does not support the networks security settings. This is pure bunk because I know it worked in edgy.

---

